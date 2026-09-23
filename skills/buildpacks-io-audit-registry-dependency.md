---
name: audit-a-registry-buildpack-dependency
description: Check whether a buildpack a build depends on is still current, still published, and not yanked, using the public Cloud Native Buildpacks registry.
api: buildpacks-io:buildpacks-io-buildpacks-api
operations:
  - listBuildpackVersions
  - getBuildpackVersion
auth: none
base_url: https://registry.buildpacks.io/api/v1
---

# Audit a buildpack dependency

Use this to answer "is the buildpack we pin still good?" for each `<namespace>/<name>@<version>`
in a `builder.toml`, `project.toml`, or a CI `pack build` invocation.

Run it per dependency. Every call is an anonymous GET; there is no key and no account.

## 1. Confirm the pinned version still exists — `getBuildpackVersion`

```
GET https://registry.buildpacks.io/api/v1/buildpacks/{namespace}/{name}/{version}
```

- `200` → the version is published. Read `yanked`.
  - `yanked: true` is the finding that matters most: the publisher has retracted this version.
    Anything pinning it should move.
  - Compare the returned `addr` with the digest you actually pin. A different digest means your
    pin and the registry disagree about what that version is.
- `404 {"error":"Unknown buildpack"}` → either the version was never published, the buildpack is
  gone, or the version string is not `MAJOR.MINOR.PATCH`. The API does not tell you which. Go to
  step 2 to separate the cases.

## 2. Compare against what is published — `listBuildpackVersions`

```
GET https://registry.buildpacks.io/api/v1/buildpacks/{namespace}/{name}
```

- `404` here means the buildpack itself is unknown — the dependency is gone from the registry, not
  merely out of date.
- `200` returns `{latest, versions[]}`. Compare `latest.version` with your pin using semver
  (`version_major` / `version_minor` / `version_patch` are also returned on full records).
- `versions[]` is complete, newest first, with a `_link` per version. Walk it backwards from
  `latest` to find the newest non-yanked version if your pin is retracted.

## 3. Record the evidence

For each dependency, capture: pinned version, `latest.version`, `yanked`, `addr` (the digest), and
`updated_at`. `description` frequently carries the publisher's own deprecation notice — Heroku's
`nodejs-npm`, for example, says "[DEPRECATED] ... Replaced by the 'heroku/nodejs-npm-engine' and
'heroku/nodejs-npm-install' buildpacks." That prose is the only migration hint the registry gives.

## Notes

- The registry is a read view over the `buildpacks/registry-index` GitHub repository; it is not the
  OCI registry. `addr` is the pointer that leaves this system — resolve it against Docker Hub, ECR
  Public or GHCR to confirm the image is still pullable.
- A buildpack being absent from this registry does not mean it is unpublished — many widely used
  buildpacks (Paketo's full set, Google Cloud's) are distributed as OCI images without a registry
  entry. Absence here is a distribution fact, not an abandonment finding.
- No rate limits are published; no `Retry-After` is sent on any status.

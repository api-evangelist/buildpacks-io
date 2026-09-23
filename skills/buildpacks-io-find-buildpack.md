---
name: find-a-buildpack
description: Find a Cloud Native Buildpack in the public community registry by keyword and resolve it to a pinned OCI image reference.
api: buildpacks-io:buildpacks-io-search-api
operations:
  - searchBuildpacks
  - listBuildpackVersions
  - getBuildpackVersion
auth: none
base_url: https://registry.buildpacks.io/api/v1
---

# Find a buildpack and pin it

Use this when you need a buildpack for a language or framework and you want the exact image
reference to put in a `builder.toml`, `project.toml` or a `pack build --buildpack` flag.

No credentials are required. Every call is an anonymous GET.

## 1. Search by keyword — `searchBuildpacks`

```
GET https://registry.buildpacks.io/api/v1/search?matches=nodejs
```

- `matches` is REQUIRED. Omitting it returns `400 {"error":"Missing search string 'matches'"}`.
- Multiple space-separated keywords narrow the result and can easily return `[]` — start with one
  keyword.
- The response is a JSON **array** (not an object). Each element is
  `{ "latest": {...}, "versions": [{"version","_link"}] }`.
- There is no pagination and no limit parameter. A broad keyword can return tens of kilobytes;
  narrow the keyword rather than trying to page.
- An empty result is `200 []`, never a 404.

Pick a candidate by `latest.namespace` / `latest.name`. Read `latest.description` — yanked or
superseded buildpacks often say so there (e.g. "[DEPRECATED] ... Replaced by ...").

## 2. List published versions — `listBuildpackVersions`

```
GET https://registry.buildpacks.io/api/v1/buildpacks/{namespace}/{name}
```

Returns `{ "latest": {...}, "versions": [ {"version": "10.11.0", "_link": "..."} ] }`.
The `_link` values are absolute URLs to the full record (they currently contain a doubled slash
before `/api`, which still resolves).

`404 {"error":"Unknown buildpack"}` means that namespace/name pair is not published. Namespaces are
case-sensitive — go back to step 1 rather than guessing.

## 3. Resolve one version — `getBuildpackVersion`

```
GET https://registry.buildpacks.io/api/v1/buildpacks/{namespace}/{name}/{version}
```

The version must be `MAJOR.MINOR.PATCH[-prerelease]`; anything else does not match the route and
comes back as the same `404 Unknown buildpack`.

From the record, use:

- `addr` — the OCI image reference **with digest**. This is the value to pin. Never rebuild the
  reference from `namespace`/`name`; different publishers use different registries
  (`docker.io/...`, `index.docker.io/...`, `public.ecr.aws/...`).
- `yanked` — if `true`, the version has been retracted with `pack buildpack yank`. Do not pin it;
  fall back to the next version in the list.
- `stacks` / `targets` — compatibility. `stacks` is deprecated as of Buildpack API 0.10; newer
  records carry `targets` (os/arch/distros).

## Conventions and failure handling

- Errors are `{"error": "<message>"}` in `application/json` — not RFC 9457. Branch on the HTTP
  status; the message text is the only other signal.
- 404 does not distinguish "unknown buildpack" from "unknown version".
- No rate-limit headers are published and no `Retry-After` is sent. Back off on your own schedule.
- Responses carry a weak `ETag`; conditional requests work if you are polling.
- The API is read-only. Publishing (`pack buildpack register`) and retraction (`pack buildpack
  yank`) go through GitHub issues on `buildpacks/registry-index`, authenticated with the author's
  GitHub token — there is nothing to call here and nothing to undo through this API.

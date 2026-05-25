# Cloud Native Buildpacks (buildpacks-io)

Cloud Native Buildpacks (CNB) is a CNCF Incubating project that transforms application source code into OCI images that can run on any cloud. The v3 specification — **Buildpack API 0.12**, **Platform API 0.15**, and **Distribution API 0.3** — defines a modular, vendor-neutral contract between buildpacks, builders, lifecycles, and platforms. CNB consolidates a decade of production experience from Heroku and Pivotal/Cloud Foundry and provides the reference lifecycle (`buildpacksio/lifecycle`), the `pack` CLI, language bindings (`libcnb` in Go/Rust/.NET), the Kubernetes-native `kpack` platform, the public community registry at registry.buildpacks.io, and an open RFC-driven governance model.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/buildpacks-io/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=opensource-api-evangelist&utm_content=repo)

## Tags

- Cloud Native Buildpacks, Buildpack API, Platform API, Distribution API, OCI, Container, CNCF, Specification, Standards

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## API Versions

| Surface | Version | Source |
|---|---|---|
| Buildpack API | 0.12 | [buildpack.md](https://github.com/buildpacks/spec/blob/main/buildpack.md) |
| Platform API | 0.15 | [platform.md](https://github.com/buildpacks/spec/blob/main/platform.md) |
| Distribution API | 0.3 | [distribution.md](https://github.com/buildpacks/spec/blob/main/distribution.md) |
| `pack` CLI | 0.40.6 (2026-05-16) | [buildpacks/pack](https://github.com/buildpacks/pack) |
| lifecycle | 0.21.9 (2026-05-12) | [buildpacks/lifecycle](https://github.com/buildpacks/lifecycle) |

## Specifications

### Buildpack Specification

The Buildpack API defines the contract between an individual buildpack and the lifecycle: the on-disk layout (`buildpack.toml`, `bin/detect`, `bin/build`), the provides/requires build plan, layer types (launch/build/cache), `launch.toml` and `build.toml` outputs, target declarations (os/arch/distros), SBOM emission, and the `CNB_*` env var contract.

**Human URL:** [https://github.com/buildpacks/spec/blob/main/buildpack.md](https://github.com/buildpacks/spec/blob/main/buildpack.md)

- [Documentation](https://github.com/buildpacks/spec/blob/main/buildpack.md)
- [Repository](https://github.com/buildpacks/spec)
- [JSON Schema — buildpack.toml](json-schema/buildpacks-buildpack-toml-schema.json)
- [JSON Schema — Build Plan](json-schema/buildpacks-build-plan-schema.json)
- [JSON Schema — launch.toml](json-schema/buildpacks-launch-toml-schema.json)
- [JSON Structure](json-structure/buildpacks-io-structure.json)
- [JSON-LD](json-ld/buildpacks-io-context.jsonld)

### Platform Specification

The Platform API defines how platforms (`pack`, `kpack`, Tekton, GitLab Auto DevOps, CircleCI Orb, Project Piper) orchestrate the lifecycle binaries — analyzer, detector, restorer, extender, builder, exporter, creator, rebaser, launcher — and the standard `io.buildpacks.*` OCI image labels.

**Human URL:** [https://github.com/buildpacks/spec/blob/main/platform.md](https://github.com/buildpacks/spec/blob/main/platform.md)

- [Documentation](https://github.com/buildpacks/spec/blob/main/platform.md)
- [Repository](https://github.com/buildpacks/spec)
- [JSON Structure](json-structure/buildpacks-io-structure.json)

### Distribution Specification

How buildpacks, extensions, and builders are packaged as OCI artifacts and published to OCI registries.

**Human URL:** [https://github.com/buildpacks/spec/blob/main/distribution.md](https://github.com/buildpacks/spec/blob/main/distribution.md)

### Image Extension Specification

Image extensions emit Dockerfile snippets applied by the `extender` lifecycle binary to the build and/or run image — enabling base-image customization (apt packages, native libs) inside a buildpacks workflow.

**Human URL:** [https://github.com/buildpacks/spec/blob/main/image_extension.md](https://github.com/buildpacks/spec/blob/main/image_extension.md)

### Project Descriptor (project.toml)

Optional app-root file letting developers declare their builder image, include/exclude globs, buildpack overrides (pre/group/post), and build-time env vars.

**Human URL:** [https://github.com/buildpacks/spec/blob/main/extensions/project-descriptor.md](https://github.com/buildpacks/spec/blob/main/extensions/project-descriptor.md)

- [Documentation](https://github.com/buildpacks/spec/blob/main/extensions/project-descriptor.md)
- [JSON Schema — project.toml](json-schema/buildpacks-project-toml-schema.json)

### Buildpack Registry Extension

The community discovery surface — namespaced buildpack identifiers, the `registry-index` GitHub repository as the source of truth, and the HTTP API exposed at `registry.buildpacks.io/api/v1`.

**Human URL:** [https://github.com/buildpacks/spec/blob/main/extensions/buildpack-registry.md](https://github.com/buildpacks/spec/blob/main/extensions/buildpack-registry.md)

- [Portal](https://registry.buildpacks.io)
- [Registry Index Repository](https://github.com/buildpacks/registry-index)
- [Registry API Repository](https://github.com/buildpacks/registry-api)
- [OpenAPI — Registry API](openapi/buildpacks-registry-api-openapi.yml)
- [Example — Search](examples/buildpacks-registry-search-example.json)
- [Example — Version](examples/buildpacks-registry-version-example.json)
- [Naftiko Capability — Registry Buildpacks](capabilities/registry-buildpacks.yaml)

### Service Bindings Extension

How external service credentials and configuration are surfaced to detect and build under `$CNB_PLATFORM_DIR/bindings/`. Aligns with the Service Binding Specification for Kubernetes.

**Human URL:** [https://github.com/buildpacks/spec/blob/main/extensions/bindings.md](https://github.com/buildpacks/spec/blob/main/extensions/bindings.md)

## Tooling

- [`pack` CLI](https://github.com/buildpacks/pack) — reference CLI implementing the Platform Interface Specification
- [`lifecycle`](https://github.com/buildpacks/lifecycle) — reference lifecycle binaries
- [`buildpacksio/lifecycle` Docker image](https://hub.docker.com/r/buildpacksio/lifecycle)
- [libcnb (Go)](https://github.com/buildpacks/libcnb)
- [libcnb-rs (Rust)](https://github.com/buildpacks/libcnb-rs)
- [libcnb.net (.NET)](https://github.com/buildpacks-community/libcnb.net)
- [kpack (Kubernetes)](https://github.com/buildpacks-community/kpack)
- [GitHub Actions for Buildpacks](https://github.com/buildpacks/github-actions)
- [CircleCI Orb](https://github.com/buildpacks/pack-orb)
- [Samples](https://github.com/buildpacks/samples)

## Governance & Community

- **CNCF Status:** Incubating (since October 2018)
- [CNCF Project Page](https://www.cncf.io/projects/buildpacks/)
- [Governance](https://github.com/buildpacks/community/blob/main/GOVERNANCE.md)
- [Roadmap](https://github.com/buildpacks/community/blob/main/ROADMAP.md)
- [Teams](https://github.com/buildpacks/community/blob/main/TEAMS.md)
- [Adopters](https://github.com/buildpacks/community/blob/main/ADOPTERS.md)
- [RFCs](https://github.com/buildpacks/rfcs)
- [CNCF Mailing List](https://lists.cncf.io/g/cncf-buildpacks)
- [CNCF Slack — #buildpacks](https://slack.cncf.io)
- [GitHub Discussions](https://github.com/buildpacks/community/discussions)
- [YouTube](https://www.youtube.com/@buildpacks)
- [Twitter / X](https://twitter.com/buildpacks_io)
- [Blog (Medium)](https://medium.com/buildpacks)
- [DevStats](https://buildpacks.devstats.cncf.io/)

## Working Group Meetings

- 1st & 3rd Thursday — 10:00 AM Pacific
- 2nd & 4th Thursday — 7:00 AM Pacific

## Position

**Producing** — Cloud Native Buildpacks publishes specifications, governance, and reference tooling. API Evangelist consumes the spec to profile downstream platforms (kpack, Heroku, Paketo, Tanzu Buildpacks) and to capture the v3 contract for AI-driven build pipelines.

## Artifact Inventory

| Artifact | Path |
|---|---|
| OpenAPI — Registry API | [`openapi/buildpacks-registry-api-openapi.yml`](openapi/buildpacks-registry-api-openapi.yml) |
| JSON Schema — buildpack.toml | [`json-schema/buildpacks-buildpack-toml-schema.json`](json-schema/buildpacks-buildpack-toml-schema.json) |
| JSON Schema — project.toml | [`json-schema/buildpacks-project-toml-schema.json`](json-schema/buildpacks-project-toml-schema.json) |
| JSON Schema — launch.toml | [`json-schema/buildpacks-launch-toml-schema.json`](json-schema/buildpacks-launch-toml-schema.json) |
| JSON Schema — Build Plan | [`json-schema/buildpacks-build-plan-schema.json`](json-schema/buildpacks-build-plan-schema.json) |
| JSON Structure | [`json-structure/buildpacks-io-structure.json`](json-structure/buildpacks-io-structure.json) |
| JSON-LD context | [`json-ld/buildpacks-io-context.jsonld`](json-ld/buildpacks-io-context.jsonld) |
| Naftiko Capability — Registry | [`capabilities/registry-buildpacks.yaml`](capabilities/registry-buildpacks.yaml) |
| Spectral Ruleset | [`rules/buildpacks-io-rules.yml`](rules/buildpacks-io-rules.yml) |
| Vocabulary | [`vocabulary/buildpacks-io-vocabulary.yml`](vocabulary/buildpacks-io-vocabulary.yml) |
| Examples | [`examples/`](examples/) |

## Maintainer

- Kin Lane — [apievangelist.com](https://apievangelist.com) — info@apievangelist.com

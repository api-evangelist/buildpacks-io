# buildpacks-io (buildpacks-io)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Cloud Native Buildpacks (CNB) is a CNCF Incubating project that transforms application source code into OCI images that can run on any cloud. The v3 specification — Buildpack API 0.12, Platform API 0.15, and Distribution API 0.3 — defines a modular, vendor-neutral contract between buildpacks, builders, lifecycles, and platforms. CNB consolidates a decade of production experience from Heroku and Pivotal/Cloud Foundry and provides the reference lifecycle (buildpacksio/lifecycle), the `pack` CLI, language bindings (libcnb in Go/Rust/.NET), the Kubernetes-native `kpack` platform, the public community registry at registry.buildpacks.io, and an open RFC-driven governance model.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/buildpacks-io/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/buildpacks-io/refs/heads/main/apis.yml)

## Scope

- **Position:** Producing

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## APIs

### Buildpack Specification

The Buildpack API (currently 0.12) defines the contract between an individual buildpack and the lifecycle. It specifies the on-disk layout of a buildpack (buildpack.toml, bin/detect, bin/build), the build plan provides/requires graph, layer types (launch/build/cache), launch.toml and build.toml outputs, target declarations (os/arch/distros), SBOM emission, and the CNB_* environment variable contract.

- **Human URL:** [https://github.com/buildpacks/spec/blob/main/buildpack.md](https://github.com/buildpacks/spec/blob/main/buildpack.md)

#### Tags

- Cloud Native Buildpacks
- Buildpack API
- Specification
- CNCF

#### Properties

- [Documentation](https://github.com/buildpacks/spec/blob/main/buildpack.md)
- [Repository](https://github.com/buildpacks/spec)
- [JSON Schema](json-schema/buildpacks-buildpack-toml-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/buildpacks-build-plan-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/buildpacks-launch-toml-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Structure](json-structure/buildpacks-io-structure.json)
- [JSON-LD](json-ld/buildpacks-io-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [Postman Collection](collections/buildpacks-registry-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/buildpacks-registry-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Platform Specification

The Platform API (currently 0.15) defines how platforms (pack, kpack, Tekton Pipelines, GitLab Auto DevOps, CircleCI Orb, Project Piper) orchestrate the lifecycle. Specifies the lifecycle binary surface (analyzer, detector, restorer, extender, builder, exporter, creator, rebaser, launcher), the TOML files exchanged on disk (group.toml, plan.toml, order.toml, run.toml, metadata.toml, report.toml, analyzed.toml, project-metadata.toml), the standard io.buildpacks.* OCI image labels, and runtime process selection.

- **Human URL:** [https://github.com/buildpacks/spec/blob/main/platform.md](https://github.com/buildpacks/spec/blob/main/platform.md)

#### Tags

- Cloud Native Buildpacks
- Platform API
- Specification
- CNCF

#### Properties

- [Documentation](https://github.com/buildpacks/spec/blob/main/platform.md)
- [Repository](https://github.com/buildpacks/spec)
- [JSON Structure](json-structure/buildpacks-io-structure.json)
- [Postman Collection](collections/buildpacks-registry-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/buildpacks-registry-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Distribution Specification

The Distribution API (currently 0.3) defines how buildpacks, extensions, and builders are packaged as OCI artifacts and published to OCI registries. Covers labels (io.buildpacks.buildpack.api, io.buildpacks.buildpack.layers), multi-buildpack OCI artifacts, and image extension distribution.

- **Human URL:** [https://github.com/buildpacks/spec/blob/main/distribution.md](https://github.com/buildpacks/spec/blob/main/distribution.md)

#### Tags

- Cloud Native Buildpacks
- Distribution
- OCI
- CNCF

#### Properties

- [Documentation](https://github.com/buildpacks/spec/blob/main/distribution.md)
- [Repository](https://github.com/buildpacks/spec)
- [Postman Collection](collections/buildpacks-registry-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/buildpacks-registry-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Image Extension Specification

Image extensions emit Dockerfile snippets applied by the `extender` lifecycle binary to the build and/or run image. Share the buildpack surface (extension.toml, bin/detect, bin/generate) but produce Dockerfile output instead of layers — enabling base-image customization (apt packages, native libs) inside a buildpacks workflow.

- **Human URL:** [https://github.com/buildpacks/spec/blob/main/image_extension.md](https://github.com/buildpacks/spec/blob/main/image_extension.md)

#### Tags

- Cloud Native Buildpacks
- Image Extension
- Dockerfile
- Specification

#### Properties

- [Documentation](https://github.com/buildpacks/spec/blob/main/image_extension.md)
- [Repository](https://github.com/buildpacks/spec)
- [Postman Collection](collections/buildpacks-registry-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/buildpacks-registry-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Project Descriptor (project.toml)

The Project Descriptor extension defines project.toml — the optional app-root file letting developers declare their builder image, include/exclude globs, buildpack overrides (pre/group/post), and build-time env vars. Read by `pack build` and other platforms before invoking the lifecycle.

- **Human URL:** [https://github.com/buildpacks/spec/blob/main/extensions/project-descriptor.md](https://github.com/buildpacks/spec/blob/main/extensions/project-descriptor.md)

#### Tags

- Cloud Native Buildpacks
- Project Descriptor
- App Surface

#### Properties

- [Documentation](https://github.com/buildpacks/spec/blob/main/extensions/project-descriptor.md)
- [JSON Schema](json-schema/buildpacks-project-toml-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [Postman Collection](collections/buildpacks-registry-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/buildpacks-registry-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Buildpack Registry Extension

The Buildpack Registry extension specifies the community discovery surface — namespaced buildpack identifiers (e.g. paketo-buildpacks/nodejs), the registry-index GitHub repository as the source of truth, and the HTTP API exposed at registry.buildpacks.io/api/v1 (search and per-buildpack version lookup). Backed by the `pack buildpack register/yank/pull` commands.

- **Human URL:** [https://github.com/buildpacks/spec/blob/main/extensions/buildpack-registry.md](https://github.com/buildpacks/spec/blob/main/extensions/buildpack-registry.md)

#### Tags

- Cloud Native Buildpacks
- Registry
- Discovery

#### Properties

- [Documentation](https://github.com/buildpacks/spec/blob/main/extensions/buildpack-registry.md)
- [Portal](https://registry.buildpacks.io)
- [Repository](https://github.com/buildpacks/registry-index)
- [Repository](https://github.com/buildpacks/registry-api)
- [OpenAPI](openapi/buildpacks-registry-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/buildpacks-registry-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/buildpacks-registry-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Example](examples/buildpacks-registry-search-example.json)
- [Example](examples/buildpacks-registry-version-example.json)

### Service Bindings Extension

The Service Bindings extension specifies how external service credentials and configuration are surfaced to detect and build under $CNB_PLATFORM_DIR/bindings/. Aligns with the Service Binding Specification for Kubernetes and lets buildpacks discover databases, message brokers, and CA bundles without provider coupling.

- **Human URL:** [https://github.com/buildpacks/spec/blob/main/extensions/bindings.md](https://github.com/buildpacks/spec/blob/main/extensions/bindings.md)

#### Tags

- Cloud Native Buildpacks
- Service Bindings
- Kubernetes

#### Properties

- [Documentation](https://github.com/buildpacks/spec/blob/main/extensions/bindings.md)
- [Postman Collection](collections/buildpacks-registry-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/buildpacks-registry-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Portal](https://buildpacks.io)
- [Documentation](https://buildpacks.io/docs/)
- [Documentation](https://buildpacks.io/docs/concepts/)
- [Documentation](https://buildpacks.io/docs/for-app-developers/)
- [Documentation](https://buildpacks.io/docs/for-buildpack-authors/)
- [Documentation](https://buildpacks.io/docs/for-platform-operators/)
- [Documentation](https://buildpacks.io/docs/reference/)
- [Getting Started](https://buildpacks.io/docs/app-journey)
- [Community](https://buildpacks.io/community/)
- [Release Notes](https://buildpacks.io/releases/)
- [Blog](https://medium.com/buildpacks)
- [Video Channel](https://www.youtube.com/@buildpacks)
- [Social Media](https://twitter.com/buildpacks_io)
- [GitHub Organization](https://github.com/buildpacks)
- [GitHub Organization](https://github.com/buildpacks-community)
- [Repository](https://github.com/buildpacks/spec)
- [Repository](https://github.com/buildpacks/rfcs)
- [Repository](https://github.com/buildpacks/community)
- [Governance](https://github.com/buildpacks/community/blob/main/GOVERNANCE.md)
- [Roadmap](https://github.com/buildpacks/community/blob/main/ROADMAP.md)
- [Documentation](https://github.com/buildpacks/community/blob/main/TEAMS.md)
- [Case Studies](https://github.com/buildpacks/community/blob/main/ADOPTERS.md)
- [Tool](https://github.com/buildpacks/pack)
- [Tool](https://github.com/buildpacks/lifecycle)
- [Container Image](https://hub.docker.com/r/buildpacksio/lifecycle)
- [SDK](https://github.com/buildpacks/libcnb)
- [SDK](https://github.com/buildpacks/libcnb-rs)
- [SDK](https://github.com/buildpacks-community/libcnb.net)
- [Code Examples](https://github.com/buildpacks/samples)
- [Tool](https://github.com/buildpacks/github-actions)
- [Tool](https://github.com/buildpacks/pack-orb)
- [Tool](https://github.com/buildpacks-community/kpack)
- [Repository](https://github.com/buildpacks/registry-index)
- [Repository](https://github.com/buildpacks/registry-api)
- [Portal](https://registry.buildpacks.io)
- [Analytics](https://buildpacks.devstats.cncf.io/)
- [Documentation](https://www.cncf.io/projects/buildpacks/)
- [Mailing List](https://lists.cncf.io/g/cncf-buildpacks)
- [Forum](https://slack.cncf.io)
- [Forum](https://github.com/buildpacks/community/discussions)
- [Forum](https://stackoverflow.com/questions/tagged/buildpack)
- [Features](undefined)
- [Vocabulary](vocabulary/buildpacks-io-vocabulary.yml)
- [Spectral Rules](rules/buildpacks-io-rules.yml)
- [JSON-LD](json-ld/buildpacks-io-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

## Maintainers

**FN:** Kin Lane
**Email:** info@apievangelist.com
**URL:** https://apievangelist.com

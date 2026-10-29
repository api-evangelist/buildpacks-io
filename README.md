# Buildpacks Io

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Cloud Native Buildpacks (CNB) is a CNCF Graduated project (graduated 2026-07-17) that transforms application source code into OCI images that can run on any cloud. The v3 specification — Buildpack API 0.12, Platform API 0.15, and Distribution API 0.3 — defines a modular, vendor-neutral contract between buildpacks, builders, lifecycles, and platforms. CNB consolidates a decade of production experience from Heroku and Pivotal/Cloud Foundry and provides the reference lifecycle (buildpacksio/lifecycle), the `pack` CLI, language bindings (libcnb in Go/Rust/.NET), the Kubernetes-native `kpack` platform, the public community registry at registry.buildpacks.io, and an open RFC-driven governance model.

**Areas:** Cloud Native Buildpacks · Container Images · Build Automation · CNCF · Open Source · Developer Tools · OCI · Specification · Supply Chain · Registry

## Buildpacks Io on APIs.io

Everything profiled for Buildpacks Io is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/buildpacks-io/](https://apis.io/providers/buildpacks-io/)** — or go straight to one of the APIs or properties below.

### APIs (8)

- [Buildpack Specification](https://apis.io/apis/buildpacks-io/buildpack-spec/) — The Buildpack API (currently 0.12) defines the contract between an individual buildpack and the lifecycle. It specifies the on-disk layout of a buildpack…
- [Platform Specification](https://apis.io/apis/buildpacks-io/platform-spec/) — The Platform API (currently 0.15) defines how platforms (pack, kpack, Tekton Pipelines, GitLab Auto DevOps, CircleCI Orb, Project Piper) orchestrate the…
- [Distribution Specification](https://apis.io/apis/buildpacks-io/distribution-spec/) — The Distribution API (currently 0.3) defines how buildpacks, extensions, and builders are packaged as OCI artifacts and published to OCI registries. Covers…
- [Image Extension Specification](https://apis.io/apis/buildpacks-io/image-extension-spec/) — Image extensions emit Dockerfile snippets applied by the `extender` lifecycle binary to the build and/or run image. Share the buildpack surface…
- [Project Descriptor (project.toml)](https://apis.io/apis/buildpacks-io/project-descriptor-spec/) — The Project Descriptor extension defines project.toml — the optional app-root file letting developers declare their builder image, include/exclude globs,…
- [Service Bindings Extension](https://apis.io/apis/buildpacks-io/service-bindings-spec/) — The Service Bindings extension specifies how external service credentials and configuration are surfaced to detect and build under…
- [buildpacks-io Buildpacks API](https://apis.io/apis/buildpacks-io/buildpacks-io-buildpacks-api/) — Retrieve buildpack version metadata
- [buildpacks-io Search API](https://apis.io/apis/buildpacks-io/buildpacks-io-search-api/) — Search the buildpack registry by keyword

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [buildpacks-registry](https://apis.io/servers/buildpacks-io/buildpacks-registry/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Buildpacks Io Agentic Access](https://apis.io/agentic-access/buildpacks-io/buildpacks-io-agentic-access/)

#### JSON Schema (4)

The data models the API reads and writes.

- [Buildpack Build Plan](https://apis.io/schemas/buildpacks-io/buildpacks-build-plan/)
- [buildpack.toml](https://apis.io/schemas/buildpacks-io/buildpacks-buildpack-toml/)
- [launch.toml](https://apis.io/schemas/buildpacks-io/buildpacks-launch-toml/)
- [project.toml (Project Descriptor)](https://apis.io/schemas/buildpacks-io/buildpacks-project-toml/)

#### JSON Structure (1)

Data models expressed in JSON Structure.

- [Buildpacks Io Structure](https://apis.io/json-structure/buildpacks-io/buildpacks-io-structure/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Buildpacks Io Context](https://apis.io/jsonld/buildpacks-io/buildpacks-io-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Cloud Native Buildpacks Vocabulary](https://apis.io/vocabularies/buildpacks-io/buildpacks-io-vocabulary/)

#### Examples (3)

Example requests and responses.

- [Moved to /providers/buildpacks-io/](https://apis.io/examples/buildpacks-io/buildpacks-registry-search-example/)
- [Buildpacks Registry Version Example](https://apis.io/examples/buildpacks-io/buildpacks-registry-version-example/)
- [Buildpacks Registry Versions List Example](https://apis.io/examples/buildpacks-io/buildpacks-registry-versions-list-example/)

#### Collections (3)

Postman and Open Collection request collections.

- [Cloud Native Registry Buildpacks API](https://apis.io/collections/buildpacks-io/open-buildpacks-io-buildpacks-api/)
- [Cloud Native Registry Buildpacks Search API](https://apis.io/collections/buildpacks-io/open-buildpacks-io-search-api/)
- [Cloud Native Buildpacks Registry API](https://apis.io/collections/buildpacks-io/open-buildpacks-registry-api/)

#### Overlays (2)

OpenAPI overlays, including conversational phrasing for each operation.

- [Buildpacks Io Buildpacks Api Overlay](https://apis.io/overlays/buildpacks-io/buildpacks-io-buildpacks-api-overlay/)
- [Buildpacks Io Search Api Overlay](https://apis.io/overlays/buildpacks-io/buildpacks-io-search-api-overlay/)

#### Governance rules (2)

Spectral rulesets for the provider's contracts.

- [Buildpacks Io — jsonschema rules](https://apis.io/rules/buildpacks-io/buildpacks-io-jsonschema-spectral-rules/)
- [Buildpacks Io API Rules](https://apis.io/rules/buildpacks-io/buildpacks-io-rules/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Buildpacks Io Authentication](https://apis.io/security/buildpacks-io/buildpacks-io-authentication/)
- [Buildpacks Io Domain Security](https://apis.io/security/buildpacks-io/buildpacks-io-domain-security/)
- [Buildpacks Io Vulnerability Disclosure](https://apis.io/security/buildpacks-io/buildpacks-io-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Buildpacks Io Plans Pricing](https://apis.io/plans/buildpacks-io/buildpacks-io-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Buildpacks Io Rate Limits](https://apis.io/rate-limits/buildpacks-io/buildpacks-io-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.buildpacks.io/)
- [Documentation](https://buildpacks.io/docs/)
- [Getting started](https://buildpacks.io/docs/app-journey)
- [API reference](https://github.com/buildpacks/registry-api)
- [Blog](https://medium.com/buildpacks)
- [Security](https://github.com/buildpacks/.github/blob/main/SECURITY.md)
- [Privacy policy](https://www.linuxfoundation.org/privacy/)
- [GitHub](https://github.com/buildpacks)

## API Evangelist rating

**Kin Score 53.5** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 57.1 |
| Contract quality | 62.9 |
| Contract governance | 45.5 |
| Operational transparency | 44.7 |
| Developer ergonomics | 73.2 |
| Access clarity | 18.4 |

**Agent readiness 30.5** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | na |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | na |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | documented (partial credit) |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | na |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 31.4** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/buildpacks-io/](https://apis.io/providers/buildpacks-io/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Buildpacks Io: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/buildpacks-io/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).

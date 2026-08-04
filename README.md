# iconik (iconik)

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

iconik is a hybrid cloud media asset management (MAM) platform for video and media teams. It lets organizations ingest, organize, search, collaborate on, and distribute media across cloud and on-premise storage - working with your existing AWS, Azure, Google Cloud, or on-premise storage rather than forcing a migration into proprietary storage. iconik is API-first: nearly everything in the product is exposed through a set of versioned REST microservice APIs, so integrators can automate ingest, enrich metadata, drive search and discovery, manage files and formats across connected storages, and orchestrate asynchronous jobs.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/iconik/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/iconik/refs/heads/main/apis.yml)

## Access Model

iconik's API is public and documented at [https://app.iconik.io/docs/](https://app.iconik.io/docs/), but it is not an open, anonymous API - it operates against your own iconik tenant. To call it you need an iconik account, and an administrator must generate an **Application ID** and an **Auth Token** in the web UI (Settings / Application Tokens). Those two values are then sent on every request as headers:

- `App-ID` - the application identifier
- `Auth-Token` - the auth token

The base URL is your iconik region host, e.g. `https://app.iconik.io/API` (a European region host such as `https://eu.iconik.io/API` also exists). Requests and responses are JSON (`Content-Type: application/json`). Responses are paginated, returning page metadata (page number, total pages, and total object count).

Event notifications are delivered as **HTTP webhooks**: you register a callback URL and iconik POSTs a JSON payload when a subscribed event (for example an asset change) occurs. There is no public WebSocket API - see `review.yml`.

## Tags

- Media Asset Management
- MAM
- Video
- Media
- Cloud Storage
- Metadata
- Search
- Assets

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## APIs

iconik organizes its API as versioned microservices under `/API/{service}/v1/`. The logical APIs below map onto those microservices.

### iconik Assets API

Create, list, retrieve, update, and delete asset containers - the core media records in iconik that hold files, proxies, formats, and metadata. Includes the delete queue for staged asset removal.

- **Human URL:** [https://app.iconik.io/docs/reference.html](https://app.iconik.io/docs/reference.html)
- **Base URL:** `https://app.iconik.io/API/assets/v1`

#### Tags

- Assets
- Media
- Ingest

#### Properties

- [Documentation](https://app.iconik.io/docs/api.html)
- [API Reference](https://app.iconik.io/docs/reference.html)
- [OpenAPI](openapi/iconik-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/iconik.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/iconik.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### iconik Collections API

Organize assets into collections (iconik's folder-like grouping). Create, list, retrieve, update, and delete collections, and manage the assets and sub-collections contained within a collection. Part of the assets microservice.

- **Human URL:** [https://app.iconik.io/docs/reference.html](https://app.iconik.io/docs/reference.html)
- **Base URL:** `https://app.iconik.io/API/assets/v1`

#### Tags

- Collections
- Organization
- Folders

#### Properties

- [Documentation](https://app.iconik.io/docs/api.html)
- [API Reference](https://app.iconik.io/docs/reference.html)
- [OpenAPI](openapi/iconik-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/iconik.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/iconik.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### iconik Metadata API

Define custom metadata fields and views, and read or write metadata values on assets and collections through a chosen view. Powers the structured, searchable metadata that drives iconik's search and automation.

- **Human URL:** [https://app.iconik.io/docs/reference.html](https://app.iconik.io/docs/reference.html)
- **Base URL:** `https://app.iconik.io/API/metadata/v1`

#### Tags

- Metadata
- Views
- Fields

#### Properties

- [Documentation](https://app.iconik.io/docs/api.html)
- [API Reference](https://app.iconik.io/docs/reference.html)
- [OpenAPI](openapi/iconik-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/iconik.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/iconik.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### iconik Search API

Query assets and collections with full-text, metadata, and facet filtering, sorting, and pagination via a POST search body. Supports discovery across the catalog and management of saved searches.

- **Human URL:** [https://app.iconik.io/docs/reference.html](https://app.iconik.io/docs/reference.html)
- **Base URL:** `https://app.iconik.io/API/search/v1`

#### Tags

- Search
- Discovery
- Saved Searches

#### Properties

- [Documentation](https://app.iconik.io/docs/api.html)
- [API Reference](https://app.iconik.io/docs/reference.html)
- [OpenAPI](openapi/iconik-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/iconik.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/iconik.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### iconik Files API

Manage the files, filesets, formats, proxies, and keyframes attached to an asset, and the storages they live on. Handles the association of media on connected cloud and on-premise storage without forced migration.

- **Human URL:** [https://app.iconik.io/docs/reference.html](https://app.iconik.io/docs/reference.html)
- **Base URL:** `https://app.iconik.io/API/files/v1`

#### Tags

- Files
- Formats
- Storage

#### Properties

- [Documentation](https://app.iconik.io/docs/api.html)
- [API Reference](https://app.iconik.io/docs/reference.html)
- [OpenAPI](openapi/iconik-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/iconik.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/iconik.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### iconik Jobs API

Track and drive asynchronous operations such as transfers, transcodes, and ingest. Create, list, retrieve, update, and delete jobs, including parent and child job relationships that report progress and status.

- **Human URL:** [https://app.iconik.io/docs/reference.html](https://app.iconik.io/docs/reference.html)
- **Base URL:** `https://app.iconik.io/API/jobs/v1`

#### Tags

- Jobs
- Async
- Orchestration

#### Properties

- [Documentation](https://app.iconik.io/docs/api.html)
- [API Reference](https://app.iconik.io/docs/reference.html)
- [OpenAPI](openapi/iconik-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/iconik.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/iconik.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/iconik-io)
- [Website](https://www.iconik.io)
- [Documentation](https://app.iconik.io/docs/)
- [Plans](plans/iconik-plans-pricing.yml)
- [Rate Limits](rate-limits/iconik-rate-limits.yml)
- [Fin Ops](finops/iconik-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com

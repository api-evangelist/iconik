# iconik (iconik)

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

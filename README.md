# BigChange (bigchange)

BigChange is an all-in-one field service and job management platform - marketed as
**JobWatch** - that combines CRM, job scheduling, live vehicle/resource tracking, a
mobile workforce app, job finance (quotes, invoices, purchase orders), and business
intelligence into one system for trades and field-service organisations.

## Access model (read this first)

BigChange exposes a **real, documented, modern REST API** (the "BigChange DX" API).
The catalog entry is grounded in BigChange's own **published OpenAPI/Swagger
documents**, which are publicly reachable without a login:

- BigChange DX (core): `https://api.bigchange.com/swagger/v1/swagger.json` (108 paths)
- Asset Management: `https://api.bigchange.com/swagger/asset-management/v1/swagger.json` (34 paths)
- Webhooks: `https://api.bigchange.com/swagger/webhooks/v1/swagger.json` (4 paths)

What is **confirmed** from those specs:

- **Base URL:** `https://api.bigchange.com`
- **Authentication:** HTTP **Bearer JWT** access token (global `bearer` security
  scheme), plus a **required `Customer-Id` header** (int64) on every operation.
- **Real paths and methods** for jobs, contacts, persons, finance (invoices,
  quotes, purchase orders, sales opportunities), stock, resources, users, vehicles,
  notes, worksheets, reference data, assets, and webhooks.

What is **login-walled / modeled**:

- The human-readable reference site (`developers.bigchange.com`) is a JavaScript
  single-page app and the endpoint prose pages did not render for scraping; the
  exact **token-exchange endpoint and grant flow** ("authentication proxy" -
  `developers.bigchange.com/docs/rest/auth-proxy/get-an-access-token`) is described
  from the portal navigation and is **modeled**, not copied verbatim. API keys are
  issued in the developer portal under **Account > Manage API Keys / Integrations**.
- Request/response **body schemas** in the bundled OpenAPI are summarized as generic
  objects; the upstream `swagger.json` documents carry the full field-level models.
- **Pricing** is modeled from BigChange marketing pages (a free "Essentials" API
  tier plus per-user / per-vehicle SaaS subscription); exact figures are not
  reconciled.

A separate **legacy JobWatch web-services API** also exists (host
`webservice.bigchange.com`, authenticated with an API key plus account
username/password). This entry focuses on the modern REST API; the legacy web
service is noted for completeness only.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/bigchange/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/bigchange/refs/heads/main/apis.yml)

## Tags

- Field Service Management
- Job Management
- Scheduling
- Workforce Management
- Fleet
- CRM
- SaaS

## Timestamps

- **Created:** 2026-07-12
- **Modified:** 2026-07-12

## APIs

### BigChange Jobs API

Create, retrieve, update, schedule, start, cancel, and report on jobs and job
groups, including line items, job stock, worksheets, constraints, flags, and status
history.

- **Base URL:** `https://api.bigchange.com`
- **API Reference:** [Jobs](https://developers.bigchange.com/docs/category/rest/api-reference/v-2-0-0/jobs)

### BigChange Contacts and Persons API

Manage customer contacts and contact groups (put on/off stop, set site access
hours) and persons with data-consent history - the CRM core of JobWatch.

- **Base URL:** `https://api.bigchange.com`
- **API Reference:** [Contacts](https://developers.bigchange.com/docs/category/rest/api-reference/v-2-0-0/contacts)

### BigChange Finance API

Manage invoices, quotes, purchase orders, and sales opportunities and their line
items under `/v1/finance`.

- **Base URL:** `https://api.bigchange.com`
- **API Reference:** [Invoices](https://developers.bigchange.com/docs/category/rest/api-reference/v-2-0-0/invoices)

### BigChange Stock and Inventory API

Manage stock items, stock details and suppliers, and read stock movement records.

- **Base URL:** `https://api.bigchange.com`
- **API Reference:** [Stock](https://developers.bigchange.com/docs/category/rest/api-reference/v-2-0-0/stock)

### BigChange Resources, Users and Vehicles API

Manage resources and resource groups, back-office users, and fleet vehicles that
jobs are scheduled against.

- **Base URL:** `https://api.bigchange.com`
- **API Reference:** [Resources](https://developers.bigchange.com/docs/category/rest/api-reference/v-2-0-0/resources)

### BigChange Notes and Worksheets API

Create and manage notes and note types with progress history, and read worksheets,
worksheet groups, and worksheet questions.

- **Base URL:** `https://api.bigchange.com`
- **API Reference:** [Notes](https://developers.bigchange.com/docs/category/rest/api-reference/v-2-0-0/notes)

### BigChange Reference Data API

Read-only lookups: VAT codes, nominal codes, department codes, product categories,
job types, note types, and sales-opportunity stages and probabilities.

- **Base URL:** `https://api.bigchange.com`
- **API Reference:** [Reference Data](https://developers.bigchange.com/docs/category/rest/api-reference/v-2-0-0/reference-data)

### BigChange Asset Management API

Manage customer assets, categories, attributes, images, and service schedules, plus
service agreements and activities, under `/asset-management/v1`.

- **Base URL:** `https://api.bigchange.com`
- **OpenAPI:** [asset-management swagger.json](https://api.bigchange.com/swagger/asset-management/v1/swagger.json)

### BigChange Webhooks API

List webhook subscriptions and inspect, retry, or clear failed deliveries under
`/webhooks/v1`. Webhooks are outbound HTTP callbacks (not a WebSocket transport).

- **Base URL:** `https://api.bigchange.com`
- **OpenAPI:** [webhooks swagger.json](https://api.bigchange.com/swagger/webhooks/v1/swagger.json)

## Common Properties

- [Domain Security](security/bigchange-domain-security.yml)
- [Authentication](authentication/bigchange-authentication.yml)
- [LinkedIn](https://www.linkedin.com/company/bigchange)
- [Website](https://www.bigchange.com)
- [Documentation](https://developers.bigchange.com/docs/rest/api-reference)
- [Plans](plans/bigchange-plans-pricing.yml)
- [Rate Limits](rate-limits/bigchange-rate-limits.yml)
- [Fin Ops](finops/bigchange-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com

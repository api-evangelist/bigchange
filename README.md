# BigChange (bigchange)

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

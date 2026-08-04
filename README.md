# Shipwell (shipwell)

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

Shipwell is an AI-powered transportation management system (TMS) and freight execution platform for shippers, brokers, and carriers. The Shipwell v2 Core API lets developers plan, rate, tender, book, track, and settle multimodal freight - parcel, LTL, truckload, intermodal, rail, and ocean - programmatically, covering shipments, quoting and rating, carrier management, purchase orders and orders, documents, tenders, freight pay and audit, and a real-time events and webhooks surface.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/shipwell/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/shipwell/refs/heads/main/apis.yml)

## Access Model (be honest)

Shipwell is a proprietary, enterprise SaaS platform. The developer documentation is public at [docs.shipwell.com](https://docs.shipwell.com/), but the full platform and API are **contract- and access-gated**:

- **Sales-led onboarding.** There is no public self-serve signup or public pricing; you request a demo and are quoted based on freight volume, modules, and integrations.
- **Company-scoped API keys.** Requests are authenticated with an API key passed in the `Authorization` header (the docs call this the AuthToken scheme). Keys can be permission-restricted.
- **Separate environments.** Production (`https://api.shipwell.com/v2`) and sandbox (`https://sandbox-api.shipwell.com/v2`) are fully separate; objects in one cannot be manipulated from the other. In sandbox, third-party integrations return mocked responses.
- **Mixed base paths.** Most of the Core API is under `/v2`, but the newer **Orders API is served under the host root without the `/v2` prefix** (for example `https://api.shipwell.com/orders`).

Because the full API reference and schemas assume an authenticated account, this catalog entry mixes **confirmed** endpoints (documented publicly) with **honestly-modeled** endpoints (inferred from the documented resource groups). Modeled endpoints are flagged in the OpenAPI (`(modeled)`) and in `review.yml` under `endpointsModeled` - verify them against the live reference before use.

## APIs

Five logical APIs are cataloged:

- **Shipwell Shipments API** — create, list, retrieve, and update multimodal shipments with stops, line items, equipment, service levels, notes, and carrier assignments. (endpoints confirmed)
- **Shipwell Quoting and Rating API** — request rates/quotes (RFQs), run spot negotiations and carrier bids. (endpoints modeled)
- **Shipwell Carriers API** — list and manage carriers, carrier relationships, tags, and assignments. (partly confirmed)
- **Shipwell Orders API** — create and manage orders and purchase orders and consolidate them onto shipments; served under the host root without `/v2`. (endpoints modeled)
- **Shipwell Events and Webhooks API** — retrieve real-time events (shipment tracking timeline updates) and register webhook subscriptions delivered by HTTP POST. (partly confirmed)

## Real-Time / WebSocket

Shipwell does **not** expose a documented public WebSocket API. Real-time supply-chain updates (shipment tracking events such as `in_transit` and `delivered`) are delivered through the **Events and Webhooks API** as server-initiated HTTP POST callbacks to a subscriber endpoint - not a WebSocket or SSE stream. See `review.yml` for the full assessment.

## Tags

- Transportation Management
- TMS
- Freight
- Logistics
- Shipping
- Supply Chain

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## Common Properties

- [Website](https://www.shipwell.com/)
- [LinkedIn](https://www.linkedin.com/company/shipwell)
- [Documentation](https://docs.shipwell.com/)
- [Request a Demo](https://www.shipwell.com/request-a-demo)
- [Plans](plans/shipwell-plans-pricing.yml)
- [Rate Limits](rate-limits/shipwell-rate-limits.yml)
- [Fin Ops](finops/shipwell-finops.yml)
- [Blog](https://www.shipwell.com/blog)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com

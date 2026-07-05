# Shipwell (shipwell)

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

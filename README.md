# OnTheMarket (onthemarket)

OnTheMarket is the third-largest residential property portal in the United Kingdom, operating onthemarket.com. It was founded in 2013 by Agents' Mutual Limited as an agent-owned challenger to Rightmove and Zoopla, listed on AIM as OnTheMarket plc, and was acquired outright by CoStar Group in December 2023 for approximately GBP 99 million. In a market with no MLS and no cooperative listing standard, OnTheMarket sits at the demand end of the value chain: consumers search the portal, and listings arrive from member estate agents' CRM systems rather than from a shared data pool. Its API posture is honest and narrow. There is no public developer portal — developer., developers., api. and docs.onthemarket.com do not resolve, and /developers, /api, /docs, /openapi.json, /swagger.json and /api-docs all return 404 on the main site. What does exist is a member-only integration surface: the OnTheMarket Real Time Datafeed (RTDF), a Rightmove-RTDF-compatible feed API served from the live, OnTheMarket-operated host realtime-api.onthemarket.com, used by agency CRM vendors to push listings and pull branch enquiries on behalf of member agents. No machine-readable contract for it is published anywhere; OnTheMarket's developer guide is distributed under agreement, and every path on the host returns 404 to an anonymous caller. There is no RESO Web API or Data Dictionary certification, no OData $metadata document and no Universal Property Identifier anywhere in the stack — RESO is a North American construct and the UK has never adopted it, so "certified but unreachable" does not apply here; there is no certification layer in this market at all. OnTheMarket publishes no open data. The genuinely open UK property layer belongs to the public sector — HM Land Registry Price Paid Data and Ordnance Survey — and none of it comes from the portals. OnTheMarket's own Terms of Use go further than most and expressly forbid automated access to any page other than the home page.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/onthemarket/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/onthemarket/refs/heads/main/apis.yml)

## Tags

- Real Estate
- United Kingdom
- Property Listings
- Property Portal
- PropTech
- Rentals
- Estate Agents
- Data Feed
- New Homes
- Commercial Real Estate

## Timestamps

- **Created:** 2026-07-26
- **Modified:** 2026-07-26

## APIs

### OnTheMarket Real Time Datafeed (RTDF) API

OnTheMarket's member-only feed API for estate-agency CRM software. It is modelled on the Rightmove Real Time Datafeed (RTDF/ADF) specification, with OnTheMarket-specific differences in request and response fields and an "Only With Us" capability for exclusive listings; overseas properties are not supported. The service host realtime-api.onthemarket.com is live and presents an OnTheMarket TLS certificate (subject O=Agents' Mutual Limited, CN=*.onthemarket.com), and the enquiry endpoint /v1/property/getbranchemails is published in third-party CRM vendor setup instructions. OnTheMarket publishes no documentation, no OpenAPI, no Swagger and no OData $metadata for it: every path on the host returns HTTP 404 with an empty body to an anonymous client, and there is no self-service signup. Access requires an existing OnTheMarket agent membership with a data feed in place, arranged through OnTheMarket support — a Rightmove-style RTDF connection using a client certificate over TLS. Listed here as a real but undocumented and member-gated surface, with no machine-readable contract available to harvest.

- **Human URL:** [https://expert.onthemarket.com/contact-us/](https://expert.onthemarket.com/contact-us/)
- **Base URL:** `https://realtime-api.onthemarket.com/v1`

#### Tags

- Data Feed
- Property Listings
- Leads
- Estate Agents

#### Properties

- [Website](https://expert.onthemarket.com/)
- [Support](https://expert.onthemarket.com/contact-us/)

## Common Properties

- [Website](https://www.onthemarket.com/)
- [About](https://www.onthemarket.com/about/)
- [Terms of Service](https://www.onthemarket.com/terms/)
- [Blog](https://www.onthemarket.com/content/)
- [Partners](https://expert.onthemarket.com/our-partners/)
- [Support](https://expert.onthemarket.com/contact-us/)
- [Sign Up](https://expert.onthemarket.com/join-us/)
- [Login](https://expert.onthemarket.com/apps/login)
- [GitHub Organization](https://github.com/OnTheMarket)
- [LinkedIn](https://www.linkedin.com/company/onthemarket/)
- [Parent Company](https://www.costargroup.com/)

## RESO Posture

**Certified:** No. **Posture:** No RESO reference found anywhere on OnTheMarket's properties.

RESO is a North American (NAR/MLS) construct and the United Kingdom has no MLS to certify against. `https://www.reso.org/certificates/` was fetched anonymously (HTTP 200) and contains no reference to OnTheMarket or to any United Kingdom organization; `https://certification.reso.org/` returned HTTP 400 to an anonymous client. No OData service document or `$metadata` exists — probes of `https://www.onthemarket.com/$metadata` and `https://realtime-api.onthemarket.com/$metadata` both returned HTTP 404. There is no Universal Property Identifier; OnTheMarket uses its own opaque property identifiers. The only interoperable convention in this market is a de facto one — the Rightmove BLM/RTDF format that OnTheMarket and Openbrix also accept — with no governing body, no certification and no version registry behind it.

## Access Gate

**Gate:** `membership-required` — you must be an OnTheMarket member estate agent, homebuilder or developer with a listing agreement, or the CRM software vendor integrating on that member's behalf. There is no developer programme, no API terms page, no application form and no key self-issuance on any OnTheMarket property. Membership is arranged commercially via [expert.onthemarket.com/join-us](https://expert.onthemarket.com/join-us/); data feeds are set up by OnTheMarket support (support@onthemarket.com, 0808 1202 877). The Terms of Use are themselves part of the gate — clause 3.3 prohibits automated access to any page other than the home page.

## Open Data

**None.** OnTheMarket publishes no open, unlicensed, publicly callable dataset. Sold prices and the free instant-valuation AVM (built with Property Price Advice) are consumer web pages, not data products. The genuinely open UK property layer belongs to the public sector — HM Land Registry Price Paid Data under the Open Government Licence and Ordnance Survey's open addressing and mapping products — and none of it comes from the portals.

## Auth Model

Not published. Consistent with its Rightmove RTDF lineage, the connection is mutual TLS with a client certificate rather than a bearer token; integrators are told to support TLS 1.1/1.2 and SHA-1 PEM certificates. No API keys, no OAuth 2.0, no SAML and no OIDC discovery document are served on any OnTheMarket host (`/.well-known/openid-configuration` returned HTTP 404).

## Maintainers

- **Kin Lane** — kin@apievangelist.com

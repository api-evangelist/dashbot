# Dashbot

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

Dashbot is a conversational-data analytics platform (now operating as Dimension Labs) that ingests chatbot, voice-assistant, live-chat, call, survey and other unstructured customer conversations and enriches them into structured "dimensions" for causal intelligence and reporting. Data is sent in through a Universal REST tracker and dozens of one-click integrations (Twilio, Slack, Intercom, Zendesk, Salesforce, Amazon Lex/Connect, Google Dialogflow, Genesys, Cognigy, Kore.ai, Rasa, and more), then explored through dashboards, data explorer, flows and an analytics Agent. A REST Export API (api.dimensionlabs.io) and first-party JavaScript, Python and Ruby SDKs let teams pull enriched data back out programmatically. Dashbot was surfaced as a portfolio company of bessemer-venture-partners; the company rebranded to Dimension Labs while the API and SDKs retain the Dashbot name (api.dashbot.io still responds).

**Areas:** Company · Artificial Intelligence · Conversational Analytics · Chatbots · Voice Assistant · Customer Experience · Data Enrichment · Analytics · Contact Center

## Dashbot on APIs.io

Everything profiled for Dashbot is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/dashbot/](https://apis.io/providers/dashbot/)** — or go straight to one of the APIs or properties below.

### APIs (4)

- [Dashbot Export API](https://apis.io/apis/dashbot/dashbot-export-api/) — Read API for enriched conversational data. GET /export returns a zipFile handle for all dimension data across a set of bot IDs over a date range, optionally…
- [Dashbot Universal Tracker API](https://apis.io/apis/dashbot/dashbot-universal-tracker-api/) — Write/ingest API for unstructured customer conversations. POST one message object per call to /track (realtime, timestamp within 24 hours) or…
- [Dimension Labs Documentation MCP](https://apis.io/apis/dashbot/dashbot-mcp/) — Model Context Protocol endpoint served from the Dimension Labs documentation host. Answers JSON-RPC 2.0; tools/list is authorization-gated for anonymous…
- [Dashbot Index API](https://apis.io/apis/dashbot/dashbot-index-api/) — The Index API from Dashbot — 1 operation(s) for index.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [dimension-labs-docs](https://apis.io/servers/dashbot/dimension-labs-docs/)

#### Collections (1)

Postman and Open Collection request collections.

- [Export API](https://apis.io/collections/dashbot/open-dashbot-export-api/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Dashbot Export Api Overlay](https://apis.io/overlays/dashbot/dashbot-export-api-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Dashbot Authentication](https://apis.io/security/dashbot/dashbot-authentication/)
- [Dashbot Domain Security](https://apis.io/security/dashbot/dashbot-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Dashbot Plans Pricing](https://apis.io/plans/dashbot/dashbot-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Dashbot Rate Limits](https://apis.io/rate-limits/dashbot/dashbot-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.dimensionlabs.io/)
- [Documentation](https://docs.dimensionlabs.io/docs/dimension-product-guide)
- [Getting started](https://docs.dimensionlabs.io/reference/generating-dashbot-api-key)
- [API reference](https://docs.dimensionlabs.io/reference/using-the-integration-guides)
- [Pricing](https://www.dimensionlabs.io/pricing)
- [Sign up](https://tally.so/r/pb5Zjb)
- [Support](https://docs.dimensionlabs.io/docs/troubleshoting)
- [Blog](https://www.dimensionlabs.io/blog)
- [Compliance](https://www.dimensionlabs.io/pricing)
- [Terms of service](https://www.dimensionlabs.io/terms-of-service-policy)
- [Privacy policy](https://www.dimensionlabs.io/privacy-policy-policy)
- [GitHub](https://github.com/actionably)

## API Evangelist rating

**Kin Score 49.8** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 41.6 |
| Contract governance | 18.2 |
| Operational transparency | 2.6 |
| Developer ergonomics | 55.4 |
| Access clarity | 84.2 |

**Agent readiness 35.2** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | na |
| MCP Server | verified |
| Auth Clarity | bearer (partial credit) |
| Idempotency | na |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | — |
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
| Operation Distinctiveness | na |

**Regulatory alignment 27.3** — AI & Biometrics

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/dashbot/](https://apis.io/providers/dashbot/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Dashbot: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/dashbot/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).

# Sendoso

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

Sendoso is a corporate gifting and direct mail platform that lets sales, marketing, customer success and people teams send physical gifts, branded swag, eGifts, direct mail and charitable donations at scale. The Sendoso Core API (v3) automates sending against pre-configured campaigns — physical gifts to a known address, physical gifts with recipient address collection, and eGifts delivered by email or as embeddable links — while the Marketplace and SmartSend APIs send from an open catalog and let Sendoso pick the gift from the recipient's interests. A SCIM 2.0 surface handles user provisioning, an embeddable iFrame puts the whole send flow inside a partner application, and Svix-signed webhooks report twenty-eight send lifecycle events. Sendoso also ships an OAuth-protected MCP server, an agent skill and an A2A agent card, and integrates with Salesforce, HubSpot, Outreach, SalesLoft, Marketo and other CRM and sales engagement tools.

**Areas:** Corporate Gifting · Direct Mail · Sales Engagement · Marketing Automation · CRM Integration · eGifts · Swag and Merchandise · Fulfillment · Employee Recognition · Account Based Marketing · SCIM Provisioning · Webhook

## Sendoso on APIs.io

Everything profiled for Sendoso is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/sendoso/](https://apis.io/providers/sendoso/)** — or go straight to one of the APIs or properties below.

### APIs (8)

- [Sendoso Marketplace and SmartSend API](https://apis.io/apis/sendoso/sendoso-marketplace-api/) — Browse the Sendoso marketplace catalog, get AI-selected gift recommendations for a recipient, and send either. Four operations on /api/v3, scoped to…
- [Sendoso Webhooks](https://apis.io/apis/sendoso/sendoso-webhooks/) — Twenty-eight Svix-signed send lifecycle events delivered to an endpoint you control. Subscriptions are configured in a hosted portal; there is no webhook…
- [Sendoso MCP Server](https://apis.io/apis/sendoso/sendoso-mcp/) — OAuth-protected remote MCP server over the Sendoso platform, at https://app.sendoso.com/mcp. Publishes RFC 9728 protected-resource and RFC 8414…
- [Sendoso Campaigns API](https://apis.io/apis/sendoso/sendoso-campaigns-api/) — Campaigns, called "touches" in the API.
- [Sendoso Sends API](https://apis.io/apis/sendoso/sendoso-sends-api/) — Create and retrieve gift, direct mail and eGift sends.
- [Sendoso Smart Send API](https://apis.io/apis/sendoso/sendoso-smartsend-api/) — AI-selected gift recommendations and sending them.
- [Sendoso Teams API](https://apis.io/apis/sendoso/sendoso-teams-api/) — Team groups and their members.
- [Sendoso Users API](https://apis.io/apis/sendoso/sendoso-users-api/) — Read the authorized user, list organization users, invite new users.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Sendoso Webhooks](https://apis.io/asyncapis/sendoso/sendoso-webhooks-asyncapi/)

#### Event channels (1)

Individual events and webhooks the provider emits.

- [/](https://apis.io/channels/sendoso/sendevents/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [sendoso-mcp.yml](https://apis.io/servers/sendoso/sendoso-mcp-yml/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Sendoso Vocabulary](https://apis.io/vocabularies/sendoso/sendoso-vocabulary/)

#### Overlays (3)

OpenAPI overlays, including conversational phrasing for each operation.

- [Sendoso Core Overlay](https://apis.io/overlays/sendoso/sendoso-core-overlay/)
- [Sendoso Marketplace Overlay](https://apis.io/overlays/sendoso/sendoso-marketplace-overlay/)
- [Sendoso Scim Overlay](https://apis.io/overlays/sendoso/sendoso-scim-overlay/)

#### Governance rules (2)

Spectral rulesets for the provider's contracts.

- [Sendoso — jsonschema rules](https://apis.io/rules/sendoso/sendoso-jsonschema-spectral-rules/)
- [Sendoso API Rules](https://apis.io/rules/sendoso/sendoso-rules/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Sendoso Authentication](https://apis.io/security/sendoso/sendoso-authentication/)
- [Sendoso Domain Security](https://apis.io/security/sendoso/sendoso-domain-security/)
- [Sendoso Trust Center](https://apis.io/security/sendoso/sendoso-trust-center/)
- [Sendoso Vulnerability Disclosure](https://apis.io/security/sendoso/sendoso-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Sendoso Scopes](https://apis.io/scopes/sendoso/sendoso-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Sendoso Plans Pricing](https://apis.io/plans/sendoso/sendoso-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Sendoso Rate Limits](https://apis.io/rate-limits/sendoso/sendoso-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Sendoso Finops](https://apis.io/finops/sendoso/sendoso-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.sendoso.com/)
- [Documentation](https://developer.sendoso.com/rest-api/overview/introduction)
- [Getting started](https://developer.sendoso.com/rest-api/overview/introduction)
- [API reference](https://developer.sendoso.com/rest-api/reference/sends/get-sends)
- [Pricing](https://www.sendoso.com/compare-plans)
- [Blog](https://www.sendoso.com/blog)
- [Terms of service](https://www.sendoso.com/terms)
- [Privacy policy](https://www.sendoso.com/privacy)
- [GitHub](https://github.com/sendoso)

## API Evangelist rating

**Kin Score 58.1** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 80.0 |
| Contract quality | 28.8 |
| Contract governance | 31.8 |
| Operational transparency | 42.1 |
| Developer ergonomics | 71.4 |
| Access clarity | 77.6 |

**Agent readiness 45.8** — agent-native

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | documented (partial credit) |
| Auth Clarity | negotiable (partial credit) |
| Idempotency | documented (partial credit) |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | derived (partial credit) |
| Agent Skills | yes |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | conformant |
| Dry Run Mode | — |
| Delegated Identity | documented (partial credit) |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | — |

**Regulatory alignment 45.1** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/sendoso/](https://apis.io/providers/sendoso/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Sendoso: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/sendoso/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).

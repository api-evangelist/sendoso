# Sendoso (sendoso)

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

Sendoso is a corporate gifting and direct mail platform that lets sales, marketing, customer success
and people teams send physical gifts, branded swag, eGifts, direct mail and charitable donations at
scale. The Core API (v3) automates sending against pre-configured campaigns, the Marketplace and
SmartSend APIs send from an open catalog, SCIM 2.0 handles user provisioning, an embeddable iFrame
puts the send flow inside a partner application, and Svix-signed webhooks report twenty-eight send
lifecycle events.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/sendoso/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/sendoso/refs/heads/main/apis.yml)

## Timestamps

- **Created:** 2026-05-02
- **Modified:** 2026-08-13

## APIs

### Sendoso Core API — `https://app.sendoso.com/api/v3`

Ten operations: create a send (physical, physical-with-address-collection, or eGift), generate eGift
links, list sends, list and read campaigns ("touches"), read the current user, list and invite users,
list team groups and their members.

- [Documentation](https://developer.sendoso.com/rest-api/overview/introduction)
- [OpenAPI](openapi/sendoso-core-api-openapi.yml) · [Overlay](overlays/sendoso-core-overlay.yaml)

### Sendoso Marketplace and SmartSend API — `https://app.sendoso.com/api/v3`

Four operations: browse the catalog, send a product variant, get AI gift recommendations for a
recipient email, send a recommendation. Scoped to `marketplace` and `smartsend`.

- [Documentation](https://developer.sendoso.com/marketplace/overview/introduction)
- [OpenAPI](openapi/sendoso-marketplace-api-openapi.yml) · [Overlay](overlays/sendoso-marketplace-overlay.yaml)

### Sendoso SCIM API — `https://app.sendoso.com/api/scim/v2`

SCIM 2.0 user provisioning. Needs its own OAuth client credentials, separate from the Core API, and
is an Enterprise-tier entitlement.

- [Documentation](https://developer.sendoso.com/scim/overview/introduction)
- [OpenAPI](openapi/sendoso-scim-api-openapi.yml) · [Overlay](overlays/sendoso-scim-overlay.yaml)

### Sendoso Webhooks

Twenty-eight send lifecycle events, signed with Svix HMAC-SHA256 over the raw body with a five-minute
replay window. Subscriptions live in a hosted portal; there is no webhook management API.

- [Documentation](https://developer.sendoso.com/webhooks/introduction)
- [AsyncAPI](asyncapi/sendoso-webhooks-asyncapi.yml)

### Sendoso MCP Server — `https://app.sendoso.com/mcp`

An OAuth-protected remote MCP server over the Sendoso platform, publishing RFC 9728 protected-resource
metadata and RFC 8414 authorization-server metadata with dynamic client registration and PKCE S256.
Sold from the Core plan tier upward.

- [MCP profile](mcp/sendoso-mcp.yml) · [Tool crosswalk](mcp/sendoso-tool-crosswalk.yml)

## Agent surfaces Sendoso publishes itself

| Surface | URL | Status |
|---|---|---|
| MCP server (platform) | `https://app.sendoso.com/mcp` | Live, OAuth-gated |
| MCP server (docs search) | `https://developer.sendoso.com/mcp` | Live, anonymous, 3 tools |
| A2A agent card | `/.well-known/agent-card.json` on the docs host | 200, graded **conformant** with deviations |
| Agent Skill | `/.well-known/agent-skills/sendoso/skill.md` | 200, provider-authored, saved verbatim |
| llms.txt | `https://developer.sendoso.com/llms.txt` | 200, 44 pages, every page also served as `.md` |

Sendoso's `robots.txt` sets `Content-Signal: ai-train=yes, search=yes, ai-input=yes` — an explicit
opt-in.

## Not published by Sendoso

Recorded absences, so that a gap here reads as deliberate rather than unexamined:

- **No OpenAPI.** Probed 404 on `/openapi.json`, `/openapi.yaml`, `/docs.json`, `/mint.json`,
  `/rest-api/openapi.json`, `/scim/openapi.json`, `/marketplace/openapi.json` and
  `/api-reference/openapi.json`. The reference pages are hand-authored MDX, not spec-backed. The
  three descriptions in `openapi/` are generated by API Evangelist from those pages and say so.
- **No SDKs.** Nothing first-party on npm, PyPI, RubyGems, Packagist, Maven Central, NuGet, crates.io
  or pkg.go.dev. Fifteen of the sixteen repositories in `github.com/sendoso` are archived forks of
  other people's projects.
- **No status page.** `status.sendoso.com` resolves but does not answer; the underlying Atlassian
  Statuspage reports INACTIVE.
- **No changelog, no versioning policy, no deprecation policy, no SLA.**
- **No security.txt and no published vulnerability disclosure policy** on any host.
- **No idempotency.** Sendoso states plainly that duplicate payloads are not handled — `POST
  /api/v3/send` is not safe to retry.
- **No AsyncAPI.** The event catalog is real and complete; the AsyncAPI document in `asyncapi/` is
  ours, generated from it.
- **No named certifications readable.** The Vanta trust center at `security.sendoso.com` returns 200
  but renders entirely client-side, delivering no certification name to any automated reader.

## Provenance correction, 2026-08-13

This repository previously carried five API entries (Inventory, Recipients, Reports, Sends, Teams)
and an OpenAPI describing `https://app.sendoso.com/api/v2` with `X-Api-Key` authentication. **None of
it was real** — Sendoso's API is `/api/v3` with OAuth 2.0, and not one of those paths exists. Those
files and the eighteen artifacts derived from them (Postman and Open Collections, examples, JSON
Schema, JSON Structure, JSON-LD, agentic-access) are quarantined in
[`_scaffold/`](_scaffold/README.md) rather than deleted, so the mistake stays auditable.

## Maintainers

**FN:** API Evangelist
**Email:** info@apievangelist.com
**URL:** https://apievangelist.com

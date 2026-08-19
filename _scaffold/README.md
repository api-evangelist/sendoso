# Quarantined scaffold artifacts — DO NOT USE

These OpenAPI documents were **not published by Sendoso** and they **do not describe the
Sendoso API**. They were written by an early API Evangelist scaffold pass (see
`git log` — the originals are dated 2026-05-03) and were wrong on every load-bearing detail.

Quarantined 2026-08-13 during the enrichment pass, following the MEDITECH remediation
pattern (quarantine, do not delete, so the mistake stays auditable).

## What they claimed vs. what Sendoso actually publishes

| | Scaffold (wrong) | Sendoso's own docs (real) |
|---|---|---|
| Base path | `https://app.sendoso.com/api/v2` | `https://app.sendoso.com/api/v3` |
| Auth | `apiKey` header `X-Api-Key` | OAuth 2.0 Authorization Code, `Authorization: Bearer` |
| Resources | `/sends`, `/recipients`, `/inventory`, `/reports`, `/teams` | `/send`, `/touches`, `/users`, `/groups`, `/me`, `/marketplace/products`, `/smartsend/recommendations`, `/api/scim/v2/Users` |
| Operations | `listSends`, `createSend`, `listRecipients`, `listInventory`, `getReport`, … | `getCurrentUser`, `getUsers`, `inviteUser`, `getTeamGroups`, `getTeamGroupUsers`, `getCampaigns`, `getCampaign`, `getSends`, `createSend`, `generateEgiftLinks`, … |

Not one path in these files exists on the Sendoso API. `https://app.sendoso.com/api/v2`
returns **HTTP 404** (probed 2026-08-13).

## Replacement

`../openapi/sendoso-core-api-openapi.yml`, `../openapi/sendoso-marketplace-api-openapi.yml` and
`../openapi/sendoso-scim-api-openapi.yml` are generated **from Sendoso's own published reference
pages** at https://developer.sendoso.com — every path, method, parameter, request field and
response field in them is traceable to a documented page recorded in each operation's
`externalDocs`. They carry `info.x-generated-from: documentation`; Sendoso does not publish
an OpenAPI document of its own (probed: `/openapi.json`, `/openapi.yaml`, `/docs.json`,
`/mint.json`, `/rest-api/openapi.json`, `/api-reference/openapi.json` all 404 on
`developer.sendoso.com`, and the Mintlify page payload reports `openApiReferenceData: undefined`,
i.e. the reference pages are hand-authored MDX, not spec-backed).

Files in this directory are excluded from every apis.yml pointer.

## Blast radius — everything derived from the wrong spec came here with it

The fabricated OpenAPI did not stay in `openapi/`. Every downstream artifact was built from
it, so every one of them described an API Sendoso does not sell:

| Quarantined | What it wrongly asserted |
|---|---|
| `openapi/` (6 files) | `/api/v2/sends`, `/recipients`, `/inventory`, `/reports`; `X-Api-Key` auth |
| `collections/` (12 files) | Postman + OpenCollection runs against `{{baseUrl}}/sends/:send_id` on `/api/v2` |
| `postman/` (5 files) | Same, one collection per invented "API" |
| `examples/` (2 files) | `POST https://app.sendoso.com/api/v2/sends` with an `X-Api-Key` header and `recipient_id`/`item_id` fields that do not exist |
| `json-schema/` | A `Send` with `status: pending\|processing\|shipped\|delivered\|failed\|cancelled` and `recipient`/`item` refs. The real Send object is `{id, send_gid, type, subtype, currency, current_total_cost}` |
| `json-structure/` | Same invented Send, plus a "Cancellation only possible in pending state" rule the API has no endpoint for |
| `json-ld/` | A JSON-LD context mapping the invented fields to schema.org |
| `agentic-access/` | Agentic execution contracts classified over the 10 invented operations |
| `finops/` | A "Usage-Based, Monthly, USD" billing model and FOCUS column mapping for a provider that publishes no prices at all |

`rules/` and `vocabulary/` were left in place: the Spectral ruleset is generic style linting
with no endpoint claims, and the vocabulary is domain-level (Send, Recipient, Budget) rather
than contract-level.

## Still outstanding

The public Postman workspace at https://www.postman.com/kinlaneapi/sendoso/overview was
published from these same collections and still serves the invented `/api/v2` requests. It
lives outside this repo and needs to be rebuilt or unpublished by hand.

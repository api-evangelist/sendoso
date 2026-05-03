# Sendoso

**URL:** [https://raw.githubusercontent.com/api-evangelist/sendoso/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/sendoso/refs/heads/main/apis.yml)

Sendoso is a corporate gifting and direct mail platform that enables sales, marketing, and customer success teams to send physical and digital gifts at scale. The Sendoso Sending Platform provides personalized gift sending, branded swag, e-gift cards, direct mail, and charitable donations, integrating with Salesforce, HubSpot, Outreach, and other CRM tools.

## Timestamps

- **Created:** 2026-05-02
- **Modified:** 2026-05-02

## APIs

### Sendoso Sending Platform API

The Sendoso API enables programmatic sending of gifts, swag, e-gifts, direct mail, and branded merchandise. Integrate gift-sending into CRM workflows, marketing automation, and customer engagement pipelines. Supports recipient management, inventory browsing, budget tracking, and send analytics.

**Human URL:** [https://developer.sendoso.com/](https://developer.sendoso.com/)
**Base URL:** `https://app.sendoso.com/api/v2`

#### Tags

Corporate Gifting, Direct Mail, Sales Engagement, Marketing Automation

#### Properties

- [Documentation](https://developer.sendoso.com/)
- [Reference](https://developer.sendoso.com/reference)
- [Getting Started](https://developer.sendoso.com/getting-started)
- [Authentication](https://developer.sendoso.com/authentication)
- [Webhooks](https://developer.sendoso.com/webhooks)
- [OpenAPI](openapi/sendoso-api-openapi.yml)

---

## Common Properties

- [Website](https://sendoso.com/)
- [Developer Portal](https://developer.sendoso.com/)
- [Integrations](https://sendoso.com/integrations/)
- [Pricing](https://sendoso.com/pricing/)
- [Blog](https://sendoso.com/blog/)
- [Status](https://status.sendoso.com/)
- [Terms of Service](https://sendoso.com/terms-of-service/)
- [Privacy Policy](https://sendoso.com/privacy-policy/)

## Artifacts

### OpenAPI Specifications

| File | Description |
|------|-------------|
| [sendoso-api-openapi.yml](openapi/sendoso-api-openapi.yml) | Sendoso REST API v2 — sends, recipients, inventory, teams, reports |

### JSON Schemas

| File | Description |
|------|-------------|
| [sendoso-send-schema.json](json-schema/sendoso-send-schema.json) | JSON Schema for the Sendoso Send resource |

### JSON Structures

| File | Description |
|------|-------------|
| [sendoso-send-structure.json](json-structure/sendoso-send-structure.json) | Field-by-field structural documentation for the Send resource |

### JSON-LD Context

| File | Description |
|------|-------------|
| [sendoso-context.jsonld](json-ld/sendoso-context.jsonld) | JSON-LD context mapping Sendoso vocabulary to schema.org |

### Examples

| File | Description |
|------|-------------|
| [sendoso-create-send-example.json](examples/sendoso-create-send-example.json) | Create a gift send |
| [sendoso-list-sends-example.json](examples/sendoso-list-sends-example.json) | List sends with filtering |

### Rules

| File | Description |
|------|-------------|
| [sendoso-rules.yml](rules/sendoso-rules.yml) | Spectral ruleset enforcing Sendoso API conventions |

### Capabilities

| File | Description |
|------|-------------|
| [capabilities/gift-sending.yaml](capabilities/gift-sending.yaml) | Unified gift sending workflow — sends, recipients, inventory, budgets |
| [capabilities/shared/sendoso-api.yaml](capabilities/shared/sendoso-api.yaml) | Per-API Naftiko consumed definition for the Sendoso REST API |

### Vocabulary

| File | Description |
|------|-------------|
| [sendoso-vocabulary.yml](vocabulary/sendoso-vocabulary.yml) | Domain vocabulary for Sendoso corporate gifting concepts |

## Maintainers

**Email:** kin@apievangelist.com

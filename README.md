# Sendoso

Sendoso is a corporate gifting and direct mail platform that enables sales, marketing, and customer success teams to send physical and digital gifts at scale. The Sendoso Sending Platform provides personalized gift sending, branded swag, e-gift cards, direct mail, and charitable donations, integrating with Salesforce, HubSpot, Outreach, Marketo, and other CRM and sales engagement tools.

**Website:** [https://sendoso.com/](https://sendoso.com/)
**Developer Portal:** [https://developer.sendoso.com/](https://developer.sendoso.com/)

## APIs

| API | Description |
|---|---|
| [Sendoso Sending Platform API](https://developer.sendoso.com/) | REST API v2 for programmatic gift sending, recipient management, inventory browsing, and analytics |

## Properties

| Property | URL |
|---|---|
| Website | https://sendoso.com/ |
| Developer Portal | https://developer.sendoso.com/ |
| API Reference | https://developer.sendoso.com/reference |
| Getting Started | https://developer.sendoso.com/getting-started |
| Authentication | https://developer.sendoso.com/authentication |
| Webhooks | https://sendoso.com/webhooks/ |
| Integrations | https://sendoso.com/integrations/ |
| Pricing | https://sendoso.com/pricing/ |
| Status | https://status.sendoso.com/ |

## Artifacts

### OpenAPI

- [Sendoso Sending Platform API](openapi/sendoso-api-openapi.yml) — OpenAPI 3.1 specification for the Sendoso REST API v2 (sends, recipients, inventory, teams, reports)

### Rules

- [Sendoso Rules](rules/sendoso-rules.yml) — Spectral ruleset enforcing Sendoso API conventions

### Capabilities

**Shared Definitions**
- [sendoso-api](capabilities/shared/sendoso-api.yaml) — Per-API consumed definition for the Sendoso REST API

**Workflow Capabilities**
- [Gift Sending](capabilities/gift-sending.yaml) — Unified workflow for corporate gift sending (sends, recipients, inventory, budgets)

### JSON Schema

- [Send Schema](json-schema/sendoso-send-schema.json) — Schema for the Sendoso Send resource

### JSON Structure

- [Send Structure](json-structure/sendoso-send-structure.json) — Field-by-field structural documentation for the Send resource

### JSON-LD

- [Sendoso Context](json-ld/sendoso-context.jsonld) — JSON-LD context mapping Sendoso vocabulary to schema.org

### Examples

- [Create Send](examples/sendoso-create-send-example.json) — Example corporate gift send request and response
- [List Sends](examples/sendoso-list-sends-example.json) — Example sends listing with filtering

### Vocabulary

- [Sendoso Vocabulary](vocabulary/sendoso-vocabulary.yml) — Domain vocabulary for Sendoso corporate gifting concepts

## Tags

Corporate Gifting, Direct Mail, Sales Engagement, Marketing Automation, CRM Integration

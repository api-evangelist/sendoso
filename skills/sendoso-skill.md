---
name: Sendoso
description: Use when integrating gift and direct mail sending capabilities into applications, automating physical gift and eGift sends to customers/leads/employees, managing campaigns and sends, tracking send status, or provisioning users via SCIM.
metadata:
    mintlify-proj: sendoso
    version: "1.0"
---

# Sendoso API Skill

## Product summary

Sendoso is a REST API platform for automating physical gift and eGift sends. Use it to programmatically trigger sends, embed sending into custom forms, and manage campaigns, users, and send tracking. The API uses OAuth 2.0 for authentication and returns JSON responses. Key endpoints: `POST /api/v3/send` (create sends), `GET /api/v3/touches` (list campaigns), `GET /api/v3/send` (retrieve sends), `GET /api/v3/me` (current user). Access the full documentation at https://developer.sendoso.com and comprehensive page navigation at https://developer.sendoso.com/llms.txt.

## When to use

Reach for this skill when:
- Building integrations to send physical gifts or eGifts programmatically
- Automating gift sends based on CRM triggers or business events (e.g., lead reactivation, customer milestones)
- Retrieving campaign (touch) IDs and send history for reporting or analytics
- Managing user provisioning/deprovisioning via SCIM
- Setting up webhooks to receive real-time send status updates
- Integrating with marketplace products or SmartSend recommendations
- Debugging send failures, address collection issues, or authentication problems

## Quick reference

### Authentication
- **Method**: OAuth 2.0 Authorization Code grant
- **Token endpoint**: `https://app.sendoso.com/oauth/token`
- **Token lifetime**: 7200 seconds (2 hours); use refresh token to extend
- **Header format**: `Authorization: Bearer YOUR_ACCESS_TOKEN`
- **Required scopes**: `public` (read), `write` (send gifts), `update` (account changes), `marketplace`, `smartsend`
- **Register app**: Contact developers@sendoso.com with redirect URI

### Core API Endpoints

| Endpoint | Method | Purpose |
|----------|--------|---------|
| `/api/v3/send` | POST | Create a send (physical or eGift) |
| `/api/v3/send` | GET | Retrieve all sends (paginated) |
| `/api/v3/touches` | GET | List all active campaigns |
| `/api/v3/touches/{id}` | GET | Get single campaign details |
| `/api/v3/me` | GET | Get current user info & balance |
| `/api/v3/users` | GET | List organization users |
| `/api/v3/teams` | GET | List teams |

### Send Types

| Type | Endpoint | When to use | Required fields |
|------|----------|------------|-----------------|
| **Physical (known address)** | POST /api/v3/send | Recipient address is known | touch_id, name, email, address, city, state, zip, country, confirm_address=false, via="single_person_or_company" |
| **Physical (address collection)** | POST /api/v3/send | Recipient address unknown; collect via email/link | touch_id, name, email, no_address=true, confirm_address=true, address_confirmation_via, expire_after_days (2-7), via="single_person_or_company" |
| **eGift** | POST /api/v3/send | Send digital gift card | touch_id, email, via="single_email_address" |
| **Marketplace product** | POST /api/v3/marketplace/products/send | Send from marketplace catalog | variant_ids, recipient_email, recipient_first_name, recipient_last_name |

### Pagination
- Use `page` (starts at 1) and `per_page` (max 100) query parameters
- Response includes `current_page`, `per_page`, `total_count` or `total_posts`
- Example: `GET /api/v3/send?page=2&per_page=50`

### Webhook Events
Subscribe to events like: `send.initiated`, `send.sent`, `send.delivered`, `send.opened`, `send.clicked`, `send.redeemed`, `send.failed`, `send.canceled`, `send.expired`, `send.refunded`. All webhooks include `send_gid` and `status_changed_at` in payload.

## Decision guidance

### When to use physical send vs eGift

| Scenario | Physical Send | eGift |
|----------|---------------|-------|
| Recipient address known | ✓ Use direct send | — |
| Recipient address unknown | ✓ Use address collection | — |
| Need instant delivery | — | ✓ Use eGift |
| Want tangible item | ✓ Use physical | — |
| International recipient | Check campaign's `ship_to_countries` | Check campaign availability |
| Recipient needs choice | — | ✓ Use marketplace/SmartSend |

### When to use address collection methods

| Method | When to use |
|--------|------------|
| **Email** | Recipient can respond to email; you want custom message on collection form |
| **Link** | Recipient prefers link; sender gets collection link in response |

### When to use Marketplace vs Core API

| Use case | Approach |
|----------|----------|
| Send from pre-configured campaigns | Core API: POST /api/v3/send with touch_id |
| Send from large product catalog | Marketplace API: POST /api/v3/marketplace/products/send |
| AI-powered gift selection | SmartSend API: POST /api/v3/marketplace/recommendations/send |

## Workflow

### 1. Authenticate and get access token
- Register app with Sendoso (contact developers@sendoso.com)
- Receive client_id and client_secret
- Direct user to `https://app.sendoso.com/oauth/authorize?client_id=...&redirect_uri=...&response_type=code&scope=write`
- Exchange authorization code for access token at `https://app.sendoso.com/oauth/token`
- Store access token and refresh token; refresh every 2 hours

### 2. Retrieve available campaigns
- Call `GET /api/v3/touches` to list all active campaigns
- Filter by `delivery_type` (mail or email) if needed
- Note the campaign `id` (touch_id) for sending
- Check `ship_to_countries`, `currency`, and price range for campaign

### 3. Prepare send payload
- Determine send type: physical (known address), physical (address collection), or eGift
- Gather required fields: touch_id, recipient name/email, address (if known)
- Add optional fields: custom_message, via_from (application name)
- For physical sends, include mobile_no for non-US addresses

### 4. Create the send
- POST to `/api/v3/send` with complete payload
- Capture `tracking_code` from response for tracking
- For address collection, capture collection link if using link method
- Handle error responses: 400 (bad request), 401 (auth), 404 (campaign not found)

### 5. Track send status
- Poll `GET /api/v3/send` with tracking_code or send_gid
- Or subscribe to webhooks for real-time status updates
- Monitor status progression: initiated → sent/fulfilling → delivered/redeemed/failed

### 6. Handle failures
- Check error message for specific issue (email blank, touch not found, insufficient funds, out of stock)
- Retry with corrected payload if validation error
- Contact support if persistent failures

## Common gotchas

- **Duplicate sends**: Sendoso does not deduplicate payloads. Sending identical requests twice will create two sends. Implement idempotency on your side.
- **Token expiration**: Access tokens expire after 2 hours. Implement refresh token logic before making requests, not after failure.
- **Missing mobile_no for non-US**: Physical sends to non-US addresses require mobile_no field or will fail silently.
- **Campaign date windows**: Campaigns have start_date and end_date. Sends outside these windows will fail with "Touch not found" even if campaign exists.
- **Address confirmation expiry**: Address collection forms expire after the specified days (2-7). Recipient must confirm before expiry or send is canceled.
- **Rate limiting**: API throttles at 10 requests/second. Batch operations or contact support for higher limits.
- **Webhook signature validation**: Always verify webhook signatures using HMAC-SHA256 and timestamp (must be within 5 minutes). Implement replay attack protection.
- **Sandbox vs Production**: Sandbox mirrors production workflow but touch IDs differ and package status doesn't progress beyond processing. Test thoroughly before production.
- **No history API**: Sendoso doesn't expose historical data via API. All API sends are recorded in the platform but not queryable by date range.
- **Notification emails**: Notifications always go to the sender initiating the send, not a configurable address.
- **Dynamic notes**: Custom messages support dynamic text/templates, but test with your template syntax.

## Verification checklist

Before submitting work with Sendoso API:

- [ ] OAuth token is valid and includes required scopes (write for sends, marketplace for marketplace sends)
- [ ] Campaign touch_id exists and is active (call GET /api/v3/touches to verify)
- [ ] Campaign dates are within send window (check start_date and end_date)
- [ ] Recipient email is valid format (API validates but catches at send time)
- [ ] For physical sends: address fields are complete (address, city, state, zip, country)
- [ ] For non-US physical sends: mobile_no is included
- [ ] For address collection: expire_after_days is 2-7 inclusive
- [ ] via_from field is consistent across all sends from same application
- [ ] Webhook endpoint is reachable and signature verification is implemented
- [ ] Error handling covers 400 (validation), 401 (auth), 404 (campaign), 429 (rate limit)
- [ ] Refresh token logic is in place for long-running integrations
- [ ] Test in sandbox environment before production deployment

## Resources

- **Full documentation navigation**: https://developer.sendoso.com/llms.txt
- **REST API Overview**: https://developer.sendoso.com/rest-api/overview/introduction
- **Authentication & OAuth**: https://developer.sendoso.com/rest-api/overview/authentication
- **Webhooks & Events**: https://developer.sendoso.com/webhooks/introduction

---

> For additional documentation and navigation, see: https://developer.sendoso.com/llms.txt
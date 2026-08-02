---
name: Register and test marketplace webhooks
description: Register and test marketplace webhooks using the Tackle Cloud GTM API.
api: openapi/tackle-api-openapi.json
operations: [v1-get-token, v1-create-or-update-webhook, v1-test-webhook, v1-get-all-webhooks]
generated: '2026-07-21'
method: generated
---

# Register and test marketplace webhooks
## Authentication
1. POST `https://api.tackle.io/v1/authenticate` with your M2M `client_id` and `client_secret` (create these in the Tackle Platform) to obtain a JWT access token.
2. Send `Authorization: Bearer <JWT>` on every request. See https://developers.tackle.io/docs/getting-an-access-token.

## Steps
1. Authenticate with `v1-get-token` (POST /v1/authenticate) to get a Bearer JWT.
2. Register or update your endpoint with `v1-create-or-update-webhook` (POST /v1/webhooks). Choose a delivery auth scheme for Tackle to use when calling you back: HTTP Basic, a `subscription-key` header API key, or OAuth2 client credentials.
3. Verify delivery with `v1-test-webhook` (POST /v1/webhooks/test).
4. Confirm registration with `v1-get-all-webhooks` (GET /v1/webhooks).

## Rules
- Webhooks are the event surface — Tackle publishes no AsyncAPI. See asyncapi/tackle-webhooks.yml.
- No idempotency-key contract; make handlers idempotent on your side.
- Errors are proprietary JSON (see errors/tackle-error-codes.yml); a 401 means the JWT expired — re-authenticate.

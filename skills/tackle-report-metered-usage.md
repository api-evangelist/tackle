---
name: Report metered marketplace usage
description: Report metered marketplace usage using the Tackle Cloud GTM API.
api: openapi/tackle-api-openapi.json
operations: [v1-get-token, v1-create-metering-usage-records, v1-list-metering-usage-records, v1-get-metering-usage-record]
generated: '2026-07-21'
method: generated
---

# Report metered marketplace usage
## Authentication
1. POST `https://api.tackle.io/v1/authenticate` with your M2M `client_id` and `client_secret` (create these in the Tackle Platform) to obtain a JWT access token.
2. Send `Authorization: Bearer <JWT>` on every request. See https://developers.tackle.io/docs/getting-an-access-token.

## Steps
1. Authenticate with `v1-get-token`.
2. Submit usage with `v1-create-metering-usage-records` (POST /v1/metering/usage-records) — or upsert with the PUT variant.
3. Reconcile with `v1-list-metering-usage-records` (GET) and `v1-get-metering-usage-record` (GET /v1/metering/usage-records/{usage_record_id}).

## Rules
- Server: https://api.tackle.io/v1.
- No rate-limit headers are advertised; retry 5xx with backoff.
- Metering feeds disbursements/invoices (data-model/tackle-data-model.yml).

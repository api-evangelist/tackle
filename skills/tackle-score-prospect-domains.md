---
name: Score domains for cloud-marketplace propensity to buy
description: Score domains for cloud-marketplace propensity to buy using the Tackle Cloud GTM API.
api: openapi/tackle-prospect-openapi.json
operations: [scoreDomains, searchScoredDomains]
generated: '2026-07-21'
method: generated
---

# Score domains for cloud-marketplace propensity to buy
## Authentication
1. POST `https://api.tackle.io/v1/authenticate` with your M2M `client_id` and `client_secret` (create these in the Tackle Platform) to obtain a JWT access token.
2. Send `Authorization: Bearer <JWT>` on every request. See https://developers.tackle.io/docs/getting-an-access-token.

## Steps
1. Submit a batch of domains with `scoreDomains` (POST) to get propensity-to-buy signals per cloud marketplace.
2. Retrieve previously scored accounts with `searchScoredDomains` (POST) using the paginated response.

## Rules
- Server: https://prospect.tackle.io.
- Responses paginate via a `PaginationMetadata` object.
- Errors return `MessageError`/`SearchError` objects, not RFC 9457.

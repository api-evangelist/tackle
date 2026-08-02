---
name: Create an AWS Marketplace private offer
description: Create an AWS Marketplace private offer using the Tackle Cloud GTM API.
api: openapi/tackle-marketplace-openapi.json
operations: [listProducts, createPrivateOffer, getPrivateOffer]
generated: '2026-07-21'
method: generated
---

# Create an AWS Marketplace private offer
## Authentication
1. POST `https://api.tackle.io/v1/authenticate` with your M2M `client_id` and `client_secret` (create these in the Tackle Platform) to obtain a JWT access token.
2. Send `Authorization: Bearer <JWT>` on every request. See https://developers.tackle.io/docs/getting-an-access-token.

## Steps
1. List your AWS Marketplace products with `listProducts` (GET) to get the target `productId`.
2. Create the offer with `createPrivateOffer` (POST /private-offers) — supply buyer, pricing dimensions and EULA.
3. Poll `getPrivateOffer` (GET) to watch the offer move through its lifecycle.

## Rules
- Server: https://aws.offers.tackle.io/api (Offers AWS API v3.2.0).
- Pagination on list endpoints uses `limit`/`offset`/`next_token`.
- A 409 means the offer already exists or is in a conflicting state (errors/tackle-error-codes.yml).

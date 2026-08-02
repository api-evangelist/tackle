---
name: Provision users via SCIM 2.0
description: Provision users via SCIM 2.0 using the Tackle Cloud GTM API.
api: openapi/tackle-scim-openapi.json
operations: [getServiceProviderConfig, createUser, getUsers, patchUser, deleteUser]
generated: '2026-07-21'
method: generated
---

# Provision users via SCIM 2.0
## Authentication
The SCIM service uses an apiKey header (not the JWT Bearer flow). See authentication/tackle-authentication.yml.

## Steps
1. Read `getServiceProviderConfig` (GET /ServiceProviderConfig) to confirm supported SCIM capabilities.
2. Create a user with `createUser` (POST /Users).
3. List/filter users with `getUsers` (GET /Users) using `cursor`/`maxResults` pagination.
4. Update attributes with `patchUser` (PATCH /Users/{id}) using a SCIM PatchOp body.
5. Deactivate with `deleteUser` (DELETE /Users/{id}).

## Rules
- Server: https://scim.tackle.io (implements SCIM protocol 2.0 — see conformance/tackle-conformance.yml).
- Use `application/scim+json` content type.

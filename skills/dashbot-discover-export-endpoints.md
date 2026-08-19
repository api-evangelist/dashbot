---
name: Discover the Dimension Labs Export API surface
description: >-
  Call the Export API entry point to enumerate the endpoints the API exposes to
  your key before running an export, and verify the API key is accepted.
api: openapi/dashbot-export-api-openapi.yml
operations: [get_new-endpoint]
---

# Discover the Dimension Labs Export API surface

Use this before the first export from a new key or a new environment. It is the
cheapest way to confirm the credential works, because the Export API's only
documented failure — `403 Forbidden` — is identical on both operations, and a
403 on `/index` tells you the key is wrong without pulling any data.

## Prerequisites
- A Dimension Labs API key, generated in the app at
  **Integrations > Add Source > Show Integration Instructions**
  ([docs](https://docs.dimensionlabs.io/reference/generating-dashbot-api-key)).

## Steps

1. **Call `get_new-endpoint`.**

   ```
   GET https://api.dimensionlabs.io/index
   Authorization: <your-api-key>
   ```

   The key is the raw `Authorization` header value — no `Bearer` prefix is
   documented.

2. **Read the response.** `200` returns a JSON object with `_links`, described
   in the spec as "a collection of links to other endpoints this API supports".
   Treat `_links` as the authoritative endpoint list for your key rather than
   assuming the two operations in the published spec are all of them.

3. **Handle `403`.** The body is `{ "message": "<what went wrong>" }`.
   Regenerate the key or confirm you are using the key for the right
   integration source, then retry. There is no `401`, no `429` and no
   documented 5xx — every auth problem arrives as 403.

4. **Proceed to the export.** Once `/index` returns 200, run `get_export` (see
   `dashbot-export-enrichment-data.md`).

## Notes
- The provider's published description for this operation is still the ReadMe
  scaffold text ("This is your first endpoint! Edit this page to start
  documenting your API"), so the response shape above is taken from the spec's
  own `_links` schema rather than from prose.
- No rate limits or throttling headers are published; nothing needs to be
  backed off against on this call.

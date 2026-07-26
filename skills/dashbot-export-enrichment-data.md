---
name: Export Dimension Labs enrichment data
description: >-
  Pull enriched conversational-analytics data (dimensions) for one or more bots
  over a date range from the Dashbot / Dimension Labs Export API, handling the
  API-key header and the 403 auth failure.
api: openapi/dashbot-export-openapi.json
operations: [get_export]
---

# Export Dimension Labs enrichment data

Use this skill to retrieve enriched dimension data for your bots from the
Dashbot / Dimension Labs platform over a chosen date range.

## Prerequisites
- A Dimension Labs API key. Generate one in the app: **Integrations > Add
  Source > (create integration) > Show Integration Instructions**
  (https://docs.dimensionlabs.io/reference/generating-dashbot-api-key).
- The bot ID(s) you want to export.

## Steps
1. **Authenticate.** Send the API key in the `Authorization` header. All Export
   API calls hit `https://api.dimensionlabs.io`.
2. **Call `get_export`.** `GET /export` with query parameters:
   - `startDate` (required) — UNIX ms, `YYYY-MM-DD`, or `YYYY-DD-MM`; inclusive.
   - `endDate` (required) — same formats; inclusive.
   - `botIds` — the bot IDs to export.
   - `promptNames` — optional filter to only the named prompts/dimensions.
3. **Read the response.** On `200` the body is a JSON object with a `zipFile`
   string (the export archive). Download and unpack it.
4. **Handle errors.** A `403 Forbidden` (`{ "message": ... }`) means the
   `Authorization` header is missing or the key is not valid for the requested
   bots/range — regenerate or check the key, then retry.

## Example
```
GET https://api.dimensionlabs.io/export?startDate=2026-06-01&endDate=2026-06-30&botIds=<botId>
Authorization: <your-api-key>
```

## Notes
- This is a batch export for historical/enriched data. To *send* conversational
  data in, use the Universal tracker endpoint
  (`https://tracker.dimensionlabs.io/track?platform=universal`), documented at
  https://docs.dimensionlabs.io/reference/rest-api.

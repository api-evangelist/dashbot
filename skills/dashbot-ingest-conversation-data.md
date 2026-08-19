---
name: Ingest conversation data into Dimension Labs
description: >-
  Format and POST unstructured customer conversations — chat turns, call
  transcripts, reviews, survey responses, emails — to the Dimension Labs
  Universal tracker so they are enriched into Dimensions, choosing correctly
  between the realtime and historical endpoints and avoiding the silent
  failure modes that accept a request and mis-file the data.
api: https://docs.dimensionlabs.io/reference/rest-api
operations: [POST /track, POST /trackhistorical]
---

# Ingest conversation data into Dimension Labs

The write path has **no OpenAPI** — it is documented in prose at
[REST API](https://docs.dimensionlabs.io/reference/rest-api) and
[Sending your data to Dimension](https://docs.dimensionlabs.io/reference/sending-data-to-dimension).
Every rule below comes from those pages; nothing here is inferred.

## Prerequisites
- An integration source created in the app, and its API key
  (**Integrations > Add Source > Show Integration Instructions**).
- Data already fetched from the source platform.

## Steps

1. **Format each record as a message object.** Six fields are required:

   | Field | Type | Rule |
   |---|---|---|
   | `text` | string | The message text. |
   | `userId` | string | The **end user's** id — not the bot's — on both directions. Each human participant uses their own id. |
   | `incoming` | boolean | `true` for anything originating outside the enterprise. |
   | `conversationId` | string | Groups the whole conversation across participants. No colons. |
   | `sessionId` | string | Session boundary. No colons. |
   | `dimensionlabs_timestamp` | number | UNIX time in **milliseconds**. |

   Field *names* are case-sensitive (`userId`, not `USERID`); values are not.

2. **Decide the direction.** `incoming: true` is the customer/end user side and
   `incoming: false` is your bot, system or agent. This holds for
   non-conversational sources too: reviews and news articles are *incoming*;
   survey questions are *outgoing* and survey answers are *incoming*. Direction
   also selects the `type` query parameter.

3. **Pick the endpoint by data age.**
   - Timestamp within the last 24 hours → realtime:
     `POST https://tracker.dimensionlabs.io/track?platform=universal&v=11.1.0-rest&type=incoming|outgoing&apiKey=<KEY>`
   - Timestamp older than 24 hours → historical:
     `POST https://tracker.dimensionlabs.io/trackhistorical?platform=universal&v=11.1.0-rest&type=incoming|outgoing&apiKey=<KEY>`

   Historical data is **excluded from the nightly enrichment run** and must be
   manually backfilled in the platform afterwards. Do not use the historical
   endpoint for convenience.

4. **Send.** `Content-Type: application/json`, one message object per POST.
   There is no batch endpoint and no bulk array form on the tracker; for large
   historical loads use the file upload path instead
   ([Uploading data from a file](https://docs.dimensionlabs.io/reference/uploading-data)).

5. **Attach optional metadata to improve enrichment.** `intent`
   (`name`, optional `confidence` 0.0–1.0, optional `inputs[]`), `images[]`,
   `buttons[]`, `postback`, `platformJson` (the general-purpose container — put
   CSAT/NPS, channel, and any other context here), and `platformUserJson`
   (firstName, lastName, locale, timezone, customerTier, abTestGroup).

6. **Redact PII before sending.** Dimension Labs expects the caller to do this.
   With the `dimensionlabs` npm SDK, pass a `redact` object with
   `redactAsync(text)` and/or `redactObjectAsync(obj)`; `redactAsync` runs first
   and its output feeds `redactObjectAsync`. See
   [PII Redaction](https://docs.dimensionlabs.io/reference/pii-redaction).

7. **Check the response.** The tracker documents no error catalogue — the
   provider's own example simply tests `res.status === 200`. There is no
   request-id header to quote to support.

## Failure modes that return no error

These are the ones that will cost you a day. All are documented behaviour, none
produces an HTTP error:

- **Seconds instead of milliseconds** in `dimensionlabs_timestamp` → the record
  is filed in 1970.
- **Mis-cased field names** (`userid`, `SESSIONID`) → the field is ignored.
- **A colon in `conversationId` / `sessionId`** → not permitted; use `-` or `_`.
- **Omitting `conversationId`** → sessions fragment every time `userId` changes,
  e.g. when a human agent joins a live chat.
- **A stale timestamp on `/track`** → belongs on `/trackhistorical`.

## Operational notes
- No rate limits are published. Dimension Labs recommends sending in real time
  or rolled up every 15 minutes, and documents an AWS Lambda + EventBridge
  pattern for the scheduled case
  ([Creating a Live Integration](https://docs.dimensionlabs.io/reference/automating-api-interactions)).
- The API key travels in the **query string**. Treat tracker URLs as secrets:
  they will appear in proxy and CDN logs.
- There is no idempotency key. Re-sending a message is not documented as safe.

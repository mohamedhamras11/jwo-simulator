# JWO Store Simulator

A browser-based simulator for the Just Walk Out (JWO) store flow, for QA and UAT.
It plays the store gates: scan a shopper code at entry, add items, walk out, and send the purchase.

Hosted page: https://mohamedhamras11.github.io/jwo-simulator/

Or serve `index.html` over HTTP yourself.

## Calls it makes

| Step | Request |
|---|---|
| Entry scan | `POST /external/orders/customers/identify` |
| Walk out | `POST /external/orders/sync` |

Each request is logged with its request, response, status and timing, with copy-as-cURL.

## Usage

1. Enter the Platform URL (HTTPS), merchant domain, a bearer token and the JWO store ID.
2. Scan a shopper code, add items, then walk out.

Notes:
- The platform must allow this page's origin (CORS).
- Use a short-lived token. It stays in the browser tab unless "remember" is ticked, and is only sent to the Platform URL you enter.
- Item IDs and UPCs are sent exactly as typed, with no lookup.

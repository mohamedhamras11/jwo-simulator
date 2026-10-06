# JWO Store Simulator

A browser-based simulator for the Just Walk Out (JWO) store flow, for QA and UAT.
It plays the store gates: scan a shopper code at entry, add items, walk out, and send the purchase.

Hosted page: https://mohamedhamras11.github.io/jwo-simulator/

Or serve `index.html` over HTTP yourself.

## Calls it makes

| Step | Request |
|---|---|
| QR scan (optional, at entry, in store or exit) | `POST /external/orders/customers/identify` |
| Walk out | `POST /external/orders/sync` |
| Live cart display (optional) | `/console/transactions/carts` (create, add/update/delete items, read, abandon) |

Shopper identity is optional: a shopper can walk in without scanning, or scan a QR at any point. Up to eight gates run at once, each with its own shopper, cart and trip, and "Scan all" / "Walk out all" fire every gate at the same moment.
Each request is logged with its request, response, status and timing, with copy-as-cURL, and the log can be filtered by gate.

## Usage

1. Enter the Platform URL (HTTPS), merchant domain, a bearer token and the JWO store ID.
2. Walk in (with or without a QR scan), add items, then walk out. Add more gates to run shoppers in parallel.
3. Optional: set a Cart API host to show each gate's basket as RC prices it, refreshed every few seconds. Turn the mirror off to skip it.

Notes:
- The platform must allow this page's origin (CORS).
- Use a short-lived token. It stays in the browser tab unless "remember" is ticked, and is only sent to the Platform URL you enter.
- Item IDs and UPCs are sent exactly as typed, with no lookup.

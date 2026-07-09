# Param transform — decrypt API fields inside the proxy loop

**Problem:** HTTPS MITM gives you HTTP plaintext, but important JSON/query fields are still Base64, AES, or custom-encoded. The manual loop — copy to a REPL, edit, paste into Postman, repeat — does not scale.

This page explains the **two layers** and when DevPeek’s param transform helps. Configuration UI walkthroughs with screenshots: [website param-transform docs](https://devpeek.ypgao.com/en/docs/param-transform/) ([中文](https://devpeek.ypgao.com/docs/param-transform/)).

---

## Layer 1 vs layer 2

| Layer | What you get | Fix when broken |
|-------|--------------|-----------------|
| **Transport (HTTPS MITM)** | Readable HTTP headers & body | CA on device + host in SSL decrypt scope |
| **Application (param transform)** | Readable business fields inside JSON/query | Transform rules on specific keys |

If your list is full of `CONNECT` tunnels and empty bodies, fix **layer 1** first.

Once you see something like:

```json
{
  "username": "alice",
  "token": "YWxpY2U6c2VjcmV0"
}
```

…param transform can decode `token` (and re-encode on send).

---

## What changes in your workflow

**Without param transform**

```text
Capture → copy ciphertext → external script → edit → paste back → hope headers still match
```

**With param transform**

```text
Capture → view/edit plaintext in DevPeek → Mock or resend → auto re-encrypt outbound
```

Rules apply in **request details**, **Mock matching**, and **debug/resend APIs** — they share the same plaintext view.

---

## Rule types (conceptual)

DevPeek supports layered rules; exact dialogs are on the website:

1. **Built-in transforms** — common Base64 / encoding helpers
2. **Script transforms** — JavaScript for AES, custom signing prep, multi-field logic
3. **Rule wizard** — pick features from a captured request instead of guessing JSON paths

Start from one field on one endpoint, then expand.

---

## Example mental model

Request body (on the wire):

```json
{ "data": "AES_BASE64_BLOB" }
```

After transform rule on `data`:

```json
{ "data": { "phone": "13800138000", "code": "123456" } }
```

You edit `phone` in the UI. DevPeek serializes and encrypts before the request leaves the proxy.

---

## When param transform is the wrong tool

- **Signing covers the entire payload** — editing one field may invalidate HMAC/RSA unless your script re-signs (advanced).
- **Binary or protobuf bodies** — you may need script rules or pre-processing; start with JSON APIs.
- **Certificate pinning in the app** — layer 1 never succeeds; transform cannot run without capture.

---

## Getting started

1. Complete [quick start](./quick-start.md) until HTTPS bodies are visible.
2. Open a request with encrypted fields → create a transform rule from that request.
3. Verify plaintext in detail view, then try **Mock** on the same endpoint.

Full manual: [devpeek.ypgao.com/docs/param-transform](https://devpeek.ypgao.com/en/docs/param-transform/)

Example configs (coming soon): [examples/](../examples/)

---

## Related

- [Charles alternative — why teams add DevPeek](./charles-alternative.md)
- [Mobile H5 debugging](./mobile-h5-debugging.md)

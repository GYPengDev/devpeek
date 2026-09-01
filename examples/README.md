# Examples

Sample configs and patterns for DevPeek. These are **illustrative snippets** — adjust hosts, keys, and scripts for your environment.

> Full UI walkthroughs: [devpeek.ypgao.com/docs](https://devpeek.ypgao.com/en/docs/)

---

## Status

| Category | In this repo | Notes |
|----------|--------------|-------|
| Param transform (Base64 field) | Below | Import via app UI or config export |
| Mock auto-response | Below | Use visual Mock wizard when possible |
| Forward / Map Route | Below | Plain-text forward rules |

Contributions welcome via [Discussions](https://github.com/GYPengDev/devpeek/discussions) — share sanitized configs (no real secrets).

---

## Base64 query field (concept)

**Goal:** Decode a Base64 `token` query param for inspection; re-encode on send.

```json
{
  "comment": "Configure equivalent rule in DevPeek param transform UI",
  "match": {
    "host": "api.example.com",
    "pathPrefix": "/v1/login"
  },
  "fields": [
    {
      "location": "query",
      "key": "token",
      "transform": "base64-decode"
    }
  ]
}
```

Website: [param transform docs](https://devpeek.ypgao.com/en/docs/param-transform/)

---

## Mock: return fixed JSON for an endpoint

**Goal:** When `GET /v1/user/profile` is called, respond with a static JSON body without hitting the backend.

Use the **visual Mock wizard** from a captured request when you can — it picks URL and param traits automatically.

Manual rule shape (conceptual):

```json
{
  "comment": "Created via Mock wizard preferred",
  "match": {
    "method": "GET",
    "host": "api.example.com",
    "path": "/v1/user/profile"
  },
  "response": {
    "status": 200,
    "headers": {
      "Content-Type": "application/json"
    },
    "body": "{\"id\":1,\"name\":\"demo-user\"}"
  }
}
```

Website: [Mock docs](https://devpeek.ypgao.com/en/docs/mock/)

---

## Forward rule (Map Route)

**Goal:** Map `h5.example.com` to a local dev server, or only a path prefix.

Plain-text forward rules (one mapping per line):

```text
h5.example.com	http://localhost:3300
api.example.com	http://127.0.0.1:8080
api.example.com/v2/	http://127.0.0.1:9000
```

`host + path` prefix (1.2.1+): longest path wins; the browser URL stays the original host.

Website: [Map Route docs](https://devpeek.ypgao.com/en/docs/map-route/)

---

## Export / import full config

DevPeek can export settings (including rules) from **Preferences → Export config**. Use that to backup before trying examples.

Website: [Install & preferences](https://devpeek.ypgao.com/en/docs/install/)

---

## Related GitHub docs

- [Param transform explainer](../docs/param-transform.md)
- [Quick start](../docs/quick-start.md)

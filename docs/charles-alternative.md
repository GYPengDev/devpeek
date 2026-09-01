# Charles Proxy alternative — when DevPeek fits better

This is a **decision guide**, not a feature matrix copied from marketing pages. For DevPeek capture UI details, see the [website docs](https://devpeek.ypgao.com/en/docs/capture/).

---

## What Charles (and Fiddler) still do best

- Mature, battle-tested **HTTPS MITM** on many platforms
- Deep ecosystem familiarity in enterprise QA teams
- macOS-first workflows with long-standing muscle memory

If your job is **pure transport inspection** and you already have Charles licenses and scripts, switching may not pay off immediately. DevPeek now ships on **Windows and macOS**; pick it when param transform, visual Mock, or mobile page mirror matter more than a Charles-shaped workflow.

---

## Where teams hit the wall

These are recurring patterns from mobile H5 / Hybrid App debugging — the scenarios DevPeek is optimized for:

### 1. Transport is plain, business fields are not

You see JSON in Charles, but `token`, `sign`, and `data` are Base64/AES blobs. The real loop becomes:

```text
Charles → Node REPL → edit → Postman → Charles again
```

DevPeek adds **param transform**: rules decrypt fields for display and editing; outbound requests re-encrypt. Mock and debug APIs match on **plaintext**.

→ [Param transform guide](./param-transform.md)

### 2. The bug is in the page, not just the API

Charles shows XHR/fetch. It does not give you a **mirrored mobile page** with Elements/Console tuned for WebView quirks.

DevPeek **Debug** tab: pick the phone client, refresh, inspect DOM and console in panels built for proxied mobile HTML.

→ [Mobile H5 debugging](./mobile-h5-debugging.md)

### 3. Mock rules are write-only torture

Hand-authoring rewrite rules for every endpoint does not scale. DevPeek’s **visual Mock** starts from a captured request — pick URL/param traits, configure intercept in a guided flow.

→ [Mock docs on website](https://devpeek.ypgao.com/en/docs/mock/)

### 4. Joint debugging on LAN

Exporting `.chls` or HAR and syncing with a teammate is slow. DevPeek discovers peers on the LAN and shares sessions (scrub secrets before sharing).

→ [Collaboration docs](https://devpeek.ypgao.com/en/docs/collaboration/)

---

## Side-by-side (high level)

| Dimension | Charles / Fiddler | DevPeek |
|-----------|-------------------|---------|
| Primary platform today | macOS / Windows (Charles), Windows (Fiddler) | **Windows and macOS** |
| HTTPS MITM | ✅ Core strength | ✅ With CA + host decrypt rules |
| App-layer field decrypt/edit | Manual scripts / external tools | ✅ Built-in param transform |
| Mobile page runtime debug | Limited / external WebView tools | ✅ Built-in debug panels over proxy |
| Visual Mock from capture | Manual map rules | ✅ Wizard from live request |
| LAN session share | Export files | ✅ Peer discovery + share |
| Pricing | Commercial licenses | Core desktop **free forever**; [Pro tiers](https://devpeek.ypgao.com/en/pricing/) |

---

## Practical migration path

You do not have to rip out Charles on day one.

1. Keep Charles where the team already has licenses and muscle memory.
2. Run DevPeek on Windows or macOS for **mobile H5 joint debugging** sessions.
3. Port the painful part first: **param transform rules** and **visual Mock** for your top 5 endpoints.
4. Align CA trust on test phones once — same MITM concept, different root.

---

## Try it

- [5-minute quick start](./quick-start.md)
- [Download](https://devpeek.ypgao.com/)
- [Full documentation](https://devpeek.ypgao.com/en/docs/)

Questions? [GitHub Discussions](https://github.com/GYPengDev/devpeek/discussions)

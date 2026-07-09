# Mobile H5 & WebView debugging over the proxy

Phone-only bugs — layout glitches, WebView JS errors, race conditions on slow networks — are hard to diagnose when your only tool is a **request list**.

DevPeek’s **Debug** tab mirrors **HTML pages that flow through the proxy** and exposes **built-in** Elements, Console, and Network panels on your desktop. This is not “remote Chrome DevTools”; it is tuned for proxied mobile web sessions.

Full tutorial with video: [website debug-replay guide](https://devpeek.ypgao.com/en/docs/debug-replay/) ([中文](https://devpeek.ypgao.com/docs/debug-replay/)).

---

## Prerequisites (all required)

| Check | Why |
|-------|-----|
| Phone uses DevPeek as HTTP(S) proxy | Traffic must route through the app |
| DevPeek root CA installed **and trusted** on the phone | HTTPS must decrypt (iOS: enable trust in Certificate Trust Settings) |
| Target host in **SSL decrypt scope** | Otherwise you only see tunnels |
| Page is **HTML** loaded through the proxy | Native screens outside WebView are out of scope |

Quick setup: [quick-start.md](./quick-start.md) · [Proxy & SSL on website](https://devpeek.ypgao.com/en/docs/proxy-ssl/)

---

## Workflow

```text
Capture (verify traffic) → Debug tab → select phone client tab → refresh page on phone → mirror + panels
```

1. **Capture** — confirm the phone’s requests appear under its client tab.
2. **Debug** — switch tab, select the same client IP tab at the top.
3. On the phone, **refresh** the target H5 URL.
4. When injectable HTML is available, DevPeek **auto-connects** and shows:
   - Page mirror
   - Elements / Console / Network (built-in panels)

If it stays on **“Waiting for device connection”**, fix proxy/SSL first — do not assume a Debug bug.

---

## Good fits

- **Hybrid Apps** (React Native WebView, Flutter WebView, uni-app shells)
- **Embedded H5** inside native containers
- **Mobile browser** pages that fail only on real devices
- Joint sessions: Capture APIs in one tab, Debug the page in another — same phone, same app

---

## Not a replacement for

- **Native UI** outside WebView (Swift/Kotlin views)
- **Certificate-pinned** apps without MITM success
- **Desktop-only** sites — use Capture + extension import instead

---

## Tips from the field

**Use throttling presets** in Debug to reproduce slow-network races without leaving the app.

**Session recording** (when enabled) helps attach a repro to a bug report — scrub PII before sharing.

**Chrome extension** on PC browsers: record a session, import into DevPeek for replay when the repro is desktop-side.

---

## vs Charles + Safari Web Inspector

Charles excels at traffic. Safari Web Inspector needs USB/cable workflows and does not unify **Mock + param transform + page mirror** in one Windows-centric loop.

DevPeek targets teams that already proxy mobile traffic but still lose hours on **page-level** issues.

---

## Next steps

- [Param transform](./param-transform.md) for encrypted API fields during the same session
- [Charles alternative](./charles-alternative.md) for tool-choice context
- [FAQ](https://devpeek.ypgao.com/en/docs/faq/)

Questions: [GitHub Discussions](https://github.com/GYPengDev/devpeek/discussions)

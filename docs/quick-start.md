# Quick start checklist

A **5-minute checklist** for your first DevPeek session. For screenshots, videos, and certificate walkthroughs, use the [full quick-start guide on the website](https://devpeek.ypgao.com/en/docs/quick-start/) ([中文](https://devpeek.ypgao.com/docs/quick-start/)).

---

## Before you begin

- Windows PC with DevPeek installed ([download](https://devpeek.ypgao.com/))
- Phone and PC on the **same Wi‑Fi** (or routable LAN)
- A target H5 page or API you are **authorized** to debug

---

## Step 1 — Start the proxy

1. Launch DevPeek.
2. Confirm the proxy is listening (default port **8888**; shown in the title bar).
3. Click the **LAN IP** in the title bar to copy `IP:port` for the phone.

**Sanity check:** With system proxy enabled on the PC, browse locally — you should see requests in the Capture list.

---

## Step 2 — Point the phone at your PC

On the phone Wi‑Fi settings, set HTTP proxy to manual:

```text
Host: <your PC LAN IP>
Port: 8888
```

Each device appears as its own **client tab** in DevPeek (by IP).

---

## Step 3 — Trust the CA & enable decrypt

1. Export or download the DevPeek root CA from the app.
2. Install on the phone and **fully trust** it (iOS: Settings → General → About → Certificate Trust Settings).
3. Add target hostnames to **SSL decrypt scope** in DevPeek.

**Sanity check:** Browse HTTPS on the phone. You should see decrypted method/URL/body — not endless `CONNECT` tunnels with empty bodies.

Stuck here? [Proxy & SSL docs](https://devpeek.ypgao.com/en/docs/proxy-ssl/) · [Install guide](https://devpeek.ypgao.com/en/docs/install/)

---

## Step 4 — Capture traffic

Open the **Capture** tab:

- Select the phone’s client tab.
- Tap a request → inspect Headers / Body / Response.
- Use search to filter by URL, Host, or response body keywords.

Next: [Param transform](./param-transform.md) if fields are still encrypted at the app layer.

---

## Step 5 — Debug a mobile page (optional)

When the page is HTML served through the proxy:

1. Open the **Debug** tab.
2. Select the phone client tab.
3. Refresh the page on the phone.

DevPeek mirrors the page and opens **built-in** Elements / Console / Network panels — not desktop Chrome DevTools.

Guide: [Mobile H5 debugging](./mobile-h5-debugging.md) · [Website](https://devpeek.ypgao.com/en/docs/debug-replay/)

---

## Common blockers

| Symptom | Likely cause |
|---------|----------------|
| No requests at all | Wrong LAN IP, firewall, phone not on same network |
| Only `CONNECT`, no body | CA not trusted or host missing from decrypt scope |
| Debug stuck on “waiting for device” | Page not injectable HTML, or SSL/proxy prerequisites not met |
| HTTPS works on PC but not phone | Phone CA install incomplete (especially iOS trust step) |

More: [FAQ on website](https://devpeek.ypgao.com/en/docs/faq/)

---

## What’s next?

- Encrypted JSON fields → [Param transform](./param-transform.md)
- Compare with Charles/Fiddler → [Charles alternative](./charles-alternative.md)
- Example configs → [examples/](../examples/)

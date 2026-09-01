<h1 align="center">DevPeek</h1>

<p align="center">
  <strong>Local HTTP(S) packet capture — MITM proxy, param transform, visual Mock, WebSocket</strong>
</p>

<p align="center">
  <a href="https://devpeek.ypgao.com/">Website</a> ·
  <a href="https://devpeek.ypgao.com/en/docs/">Documentation</a> ·
  <a href="https://devpeek.ypgao.com/en/changelog/">Changelog</a> ·
  <a href="https://devpeek.ypgao.com/en/pricing/">Pricing</a> ·
  <a href="https://github.com/GYPengDev/devpeek/releases">Releases</a>
</p>

<p align="center">
  <a href="https://devpeek.ypgao.com/"><img src="https://img.shields.io/badge/Download-Windows-blue?style=for-the-badge" alt="Download DevPeek for Windows"></a>
  <a href="https://devpeek.ypgao.com/"><img src="https://img.shields.io/badge/Download-macOS-black?style=for-the-badge" alt="Download DevPeek for macOS"></a>
  <a href="https://devpeek.ypgao.com/en/docs/quick-start/"><img src="https://img.shields.io/badge/Docs-Quick%20Start-green?style=for-the-badge" alt="DevPeek quick start"></a>
</p>

<p align="center">
  <a href="./README.zh-CN.md">中文说明</a>
</p>

<p align="center">
  <img src="https://devpeek.ypgao.com/devpeek.png" alt="DevPeek logo" width="96" height="96">
</p>

---

DevPeek is a **Windows / macOS** local **HTTP(S) 抓包** app: MITM proxy, decrypted capture list, param transform, visual Mock, and WebSocket. Current stable: **1.3.0**.

It is built around:

> **Capture + param transform + visual Mock**

> **About this repository:** Official **distribution, docs index, and feedback hub**. Application source code is **proprietary** and not published here.

---

## Why not stop at Charles or Fiddler?

Classic proxy tools excel at TLS interception and API inspection. DevPeek targets the gap after that:

| Scenario | Typical pain | DevPeek angle |
|----------|--------------|---------------|
| Body is HTTPS-plain but fields are AES/Base64 | Copy ciphertext between proxy, scripts, and Postman | [**Param transform**](./docs/param-transform.md) — edit plaintext in-app, re-encrypt on send |
| Mock rules are tedious to hand-write | Regex and JSON editing for every endpoint | Visual Mock from a captured request; **groups** to switch scenes |
| Teammate needs the same request | Export files, sync timestamps manually | LAN collaboration — send a plaintext HTTP request to a peer |
| Long-lived WS / WSS | HTTP tools hide handshake and frames | WebSocket sessions + [WS Flow](https://devpeek.ypgao.com/en/docs/wsmock-dsl/) (preview) |

See also: [Charles Proxy alternative — when to pick DevPeek](./docs/charles-alternative.md)

---

## Screenshots

<p align="center">
  <img src="https://devpeek.ypgao.com/docs/figures/proxy_requestlist.png" alt="DevPeek HTTPS capture list with per-client tabs" width="720">
  <br><em>Capture — per-device tabs, decrypted HTTPS bodies</em>
</p>

<p align="center">
  <img src="https://devpeek.ypgao.com/docs/figures/param_transform_rule_wizard.png" alt="DevPeek param transform rule wizard for encrypted API fields" width="720">
  <br><em>Param transform — rule wizard for encrypted request fields</em>
</p>

<p align="center">
  <img src="https://devpeek.ypgao.com/docs/figures/mock_wizard_features.png" alt="DevPeek visual Mock rule builder" width="720">
  <br><em>Visual Mock — pick traits from a live request</em>
</p>

---

## Core capabilities

**Capture & inspection**

- Local HTTP(S) MITM proxy (generated CA, host-based decrypt rules)
- Client tabs by IP — phone, browser, test app stay separated
- Response-body search (regex, case options)
- Breakpoints, throttling, lifecycle scripts
- Pin requests; content-type filter; remembered column widths

**Param transform** *(differentiator)*

- Rules for Base64, AES, custom scripts
- Details, Mock, and debug APIs default to **plaintext**; outbound requests re-encrypt automatically
- [GitHub guide](./docs/param-transform.md) · [Full docs on website](https://devpeek.ypgao.com/en/docs/param-transform/)

**Mock & routing**

- Request-only or response-only intercept; **rule groups** with batch on/off
- Map Route / forward rules (`host` or `host + path` prefix) for local backends

**WebSocket**

- Proxied **WS / WSS** sessions alongside HTTP (handshake, frames)
- WS Flow (preview) for multi-turn mocks — [website guide](https://devpeek.ypgao.com/en/docs/wsmock-dsl/)

**Also included**

- LAN collaboration · Chromium extension import · SQLite history · Windows / macOS auto-update

Core desktop features are **free forever**. Pro & Team tiers: [pricing](https://devpeek.ypgao.com/en/pricing/).

---

## Quick start (5 minutes)

1. [Download](https://devpeek.ypgao.com/) the Windows or macOS installer (or [GitHub Releases](https://github.com/GYPengDev/devpeek/releases)).
2. Set the phone Wi‑Fi proxy to `PC_LAN_IP:8888` (port shown in the title bar; one-click copy).
3. Install & fully trust the DevPeek root CA; add target hosts to SSL decrypt scope.
4. **Capture** tab → inspect traffic. **Debug** tab → select the phone client, refresh the page to mirror.

Checklist & troubleshooting: [docs/quick-start.md](./docs/quick-start.md) · [Website quick start](https://devpeek.ypgao.com/en/docs/quick-start/)

---

## Download

| Channel | URL |
|---------|-----|
| **Official (recommended)** | https://devpeek.ypgao.com/ |
| **GitHub Releases** | https://github.com/GYPengDev/devpeek/releases |
| Install & certificates | https://devpeek.ypgao.com/en/docs/install/ |

**Windows** (NSIS) and **macOS** (DMG, Apple Silicon and Intel) are published on the website. Installers stay on the official site; this repo tracks notes and links.

---

## Docs on GitHub vs website

This repo hosts **short, scenario-focused guides** for discovery and search. Step-by-step manuals with videos and figures live on the website.

| Topic | GitHub (summary) | Website (full manual) |
|-------|------------------|------------------------|
| Quick start | [docs/quick-start.md](./docs/quick-start.md) | [EN](https://devpeek.ypgao.com/en/docs/quick-start/) · [ZH](https://devpeek.ypgao.com/docs/quick-start/) |
| Charles alternative | [docs/charles-alternative.md](./docs/charles-alternative.md) | [Capture docs](https://devpeek.ypgao.com/en/docs/capture/) |
| Param transform | [docs/param-transform.md](./docs/param-transform.md) | [EN](https://devpeek.ypgao.com/en/docs/param-transform/) · [ZH](https://devpeek.ypgao.com/docs/param-transform/) |
| WebSocket Mock | — | [EN](https://devpeek.ypgao.com/en/docs/wsmock-dsl/) · [ZH](https://devpeek.ypgao.com/docs/wsmock-dsl/) |
| Mock, SSL, FAQ | — | [docs index](https://devpeek.ypgao.com/en/docs/) |

---

## Changelog

Recent release highlights: [CHANGELOG.md](./CHANGELOG.md)

Canonical, version-by-version notes: [devpeek.ypgao.com/changelog](https://devpeek.ypgao.com/en/changelog/)

---

## Feedback

- **Bugs:** [Open an issue](https://github.com/GYPengDev/devpeek/issues/new?template=bug_report.yml)
- **Features:** [Feature request](https://github.com/GYPengDev/devpeek/issues/new?template=feature_request.yml)
- **Questions:** [Discussions](https://github.com/GYPengDev/devpeek/discussions) · [Contact form](https://devpeek.ypgao.com/en/contact/)
- **Security:** [SECURITY.md](./SECURITY.md)

---

## Related

| Repository | Role |
|------------|------|
| [devpeek-site](https://github.com/GYPengDev/devpeek-site) | Official website (Nuxt) |
| [examples/](./examples/) | Config samples index (rules & transforms) |

---

## Who is it for?

Mobile frontend · Hybrid / uni-app · React Native & Flutter WebView · H5 inside native shells · QA engineers doing joint debugging on real devices.

---

## License

DevPeek is **proprietary software**. All rights reserved.

This repository contains documentation, release metadata, and community templates — not application source code.

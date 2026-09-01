# Changelog

> **Canonical changelog (full detail, all versions):**  
> [devpeek.ypgao.com/changelog](https://devpeek.ypgao.com/en/changelog/) · [中文](https://devpeek.ypgao.com/changelog/)
>
> This file lists **recent stable highlights** for GitHub Releases and search indexing. It is not a copy of the website.

---

## 1.3.0

**Theme:** capture list polish, Mock groups, WebSocket, LAN collaboration, and Windows / macOS auto-update.

- Capture list: time / size / duration / CONNECT columns, resizable remembered widths, pin, content-type filter, tail pagination.
- Mock **groups** with batch enable/disable and remembered sidebar collapse.
- **WebSocket / WSS** sessions next to HTTP; handshake, frames, and **WS Flow** (preview) for multi-turn mocks.
- Copy URL / cURL / request / response; richer JSON tree preview.
- LAN collaboration: discover peers, send plaintext HTTP to a teammate, set a display name.
- In-app auto-update on **Windows and macOS**; macOS **DMG** install; drag-and-drop `.dpconfig` import.

[Full 1.3.0 notes on website →](https://devpeek.ypgao.com/en/changelog/1.3.0/) · [中文](https://devpeek.ypgao.com/changelog/1.3.0/)

---

## 1.2.2

**Theme:** debug-API editor stability, throttling, Windows installer.

- Param-transform plaintext editor no longer steals focus while typing.
- Request-body tab follows `Content-Type` when filling from capture.
- Weak-network bandwidth limits applied in the proxy stream, closer to real throttling.
- Windows installer: faster process shutdown, optional launch after setup.

[Full 1.2.2 notes on website →](https://devpeek.ypgao.com/en/changelog/1.2.2/)

---

## 1.2.1

**Theme:** Tauri desktop shell, path-level Map Route, debug API.

- Desktop shell moved from Electron to **Tauri** (smaller footprint, tray / window controls).
- Forward rules: `host + path` prefix, longest-prefix wins; save applies immediately.
- Debug API: source request pinned, Query / headers as table or text, CONNECT tunnels can open the drawer.
- First install no longer auto-enables system proxy; Lite mode opens the browser for you.

[Full 1.2.1 notes on website →](https://devpeek.ypgao.com/en/changelog/1.2.1/)

---

## 1.1.7

**Theme:** replay drawer, certificates, tray launcher.

- Replay / debug drawer rewritten: auto-fill from capture, send history, elapsed timing.
- CA expiry / trust checks; QR download for phone certificates.
- Native tray launcher (start/stop Core, restore system proxy on exit).
- Reduced antivirus false positives (no obfuscator; stable installer filenames).

[Full 1.1.7 notes on website →](https://devpeek.ypgao.com/en/changelog/1.1.7/)

---

## 1.1.6

**Theme:** first-run proxy defaults, About / check-for-updates.

- Clearer proxy menu (recording indicator) and About window with version + update check.
- HTTPS decrypt scope covers more common hosts by default (still editable).

[Full 1.1.6 notes on website →](https://devpeek.ypgao.com/en/changelog/1.1.6/)

---

## 1.1.4

**Theme:** polish, persistence, and mobile-debug quality-of-life.

- Rebrand to **DevPeek** with updated logo and title bar identity.
- Capture history persisted to **SQLite** — paginated list survives restarts; script-processed headers/bodies saved.
- Mock can intercept **request-only** or **response-only**; rule matching and editor flow improved.
- Title bar shows LAN IP + proxy port with **one-click copy** for phone setup.
- Debug view styling and element highlight alignment improved; less DB write churn.
- Replay: open local recording files; Chrome extension captures fuller console + network for playback.
- LAN collaboration: delete imported entries; faster peer leave broadcast on app exit.
- Certificate install wizard and optional browser CA import on supported platforms.

[Full 1.1.4 notes on website →](https://devpeek.ypgao.com/en/changelog/1.1.4/)

---

## 1.1.3

**Theme:** settings access, request-detail stability, unified window chrome.

- **Developer Tools** available in packaged builds from the gear menu.
- **Open config directory** for backup/migration of settings and global scripts.
- Global scripts / breakpoints initialization fixes.
- Request detail tabs fixed in order; inner tabs only when content exists.
- Independent dialogs (preferences, SSL, replay, etc.) share custom title bar + window controls.

[Full 1.1.3 notes on website →](https://devpeek.ypgao.com/en/changelog/1.1.3/)

---

## 1.1.2

**Theme:** light/dark consistency across capture, debug, replay, and preferences.

[Full 1.1.2 notes on website →](https://devpeek.ypgao.com/en/changelog/1.1.2/)

---

## 1.1.1

**Theme:** menu restructuring — changelog separated from About.

[Full 1.1.1 notes on website →](https://devpeek.ypgao.com/en/changelog/1.1.1/)

---

## 1.0.x — first public releases

- Local HTTP(S) proxy with MITM CA, per-client tabs, breakpoints, throttling, global scripts.
- Mobile web debug foundation, replay window, LAN collaboration, Chromium extension.
- Built-in updater (Windows/macOS depending on channel).

[1.0.1 notes →](https://devpeek.ypgao.com/en/changelog/1.0.1/) · [1.0.0 notes →](https://devpeek.ypgao.com/en/changelog/1.0.0/)

---

## License

DevPeek is proprietary software. All rights reserved.

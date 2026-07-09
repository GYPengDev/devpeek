# Assets

Optional local media for the GitHub README. **Currently the README uses figures hosted on [devpeek.ypgao.com](https://devpeek.ypgao.com/)** so this folder can stay empty.

If you want fully offline README images (faster load, no dependency on the site):

1. Export 3–4 PNGs from the app or copy from `devpeek.ypgao.com/public/docs/figures/`:
   - `screenshots/capture-list.png` — e.g. `proxy_requestlist.png`
   - `screenshots/param-transform.png` — e.g. `param_transform_rule_wizard.png`
   - `screenshots/mock-wizard.png` — e.g. `mock_wizard_features.png`
2. Update image URLs in `README.md` / `README.zh-CN.md` to `./assets/screenshots/...`
3. Upload `banner.png` (1280×640) in GitHub **Settings → Social preview**

Recommended `alt` text should mention: HTTPS proxy, mobile debug, param transform, Mock.

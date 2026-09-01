<h1 align="center">DevPeek</h1>

<p align="center">
  <strong>本地 HTTP(S) 抓包 — MITM 代理、参数转换、可视化 Mock、WebSocket</strong>
</p>

<p align="center">
  <a href="https://devpeek.ypgao.com/">官网</a> ·
  <a href="https://devpeek.ypgao.com/docs/">使用文档</a> ·
  <a href="https://devpeek.ypgao.com/changelog/">更新日志</a> ·
  <a href="https://devpeek.ypgao.com/pricing/">定价</a> ·
  <a href="https://github.com/GYPengDev/devpeek/releases">Releases</a>
</p>

<p align="center">
  <a href="https://devpeek.ypgao.com/"><img src="https://img.shields.io/badge/下载-Windows-blue?style=for-the-badge" alt="下载 DevPeek Windows 版"></a>
  <a href="https://devpeek.ypgao.com/"><img src="https://img.shields.io/badge/下载-macOS-black?style=for-the-badge" alt="下载 DevPeek macOS 版"></a>
  <a href="https://devpeek.ypgao.com/docs/quick-start/"><img src="https://img.shields.io/badge/教程-快速开始-green?style=for-the-badge" alt="DevPeek 快速开始"></a>
</p>

<p align="center">
  <a href="./README.md">English README</a>
</p>

<p align="center">
  <img src="https://devpeek.ypgao.com/devpeek.png" alt="DevPeek 标志" width="96" height="96">
</p>

---

DevPeek 是面向开发与测试的 **Windows / macOS** 本机 **HTTP(S) 抓包**工具：MITM 代理、解密列表、参数转换、可视化 Mock、WebSocket。当前稳定版：**1.3.0**。

核心理念：

> **抓包 + 参数转换 + 可视化 Mock**

> **关于本仓库：** DevPeek 的 **官方发布、文档索引与反馈入口**。应用**源码闭源**，不在此公开。

---

## 和 Charles / Fiddler 差在哪？

传统抓包工具擅长 TLS 解密和接口分析。DevPeek 补的是「解密之后」的联调链路：

| 场景 | 常见痛点 | DevPeek 做法 |
|------|----------|--------------|
| HTTPS 已解密，字段仍是 AES/Base64 | 在代理、脚本、Postman 之间来回复制密文 | [**参数转换**](./docs/param-transform.md) — 界面里改明文，发出时自动加密 |
| Mock 规则手写成本高 | 每个接口写正则、改 JSON | 从已抓请求上**可视化**配 Mock；**分组**按场景启停 |
| 同事要对同一条请求 | 导文件、对时间戳 | 局域网协作 — 把明文 HTTP 发给伙伴 |
| 长连接 WS / WSS | HTTP 工具只看到握手 | WebSocket 会话 + [WS Flow](https://devpeek.ypgao.com/docs/wsmock-dsl/)（预览） |

延伸阅读：[Charles 替代 — 什么时候选 DevPeek](./docs/charles-alternative.md)

---

## 界面预览

<p align="center">
  <img src="https://devpeek.ypgao.com/docs/figures/proxy_requestlist.png" alt="DevPeek 抓包列表与按客户端分 Tab" width="720">
  <br><em>抓包 — 按设备分 Tab，HTTPS 解密后查看 Body</em>
</p>

<p align="center">
  <img src="https://devpeek.ypgao.com/docs/figures/param_transform_rule_wizard.png" alt="DevPeek 参数转换规则向导" width="720">
  <br><em>参数转换 — 加密字段规则向导</em>
</p>

<p align="center">
  <img src="https://devpeek.ypgao.com/docs/figures/mock_wizard_features.png" alt="DevPeek 可视化 Mock 配置" width="720">
  <br><em>可视化 Mock — 从请求上拾取特征</em>
</p>

---

## 主要能力

**抓包与检查**

- 本机 HTTP(S) MITM 代理（自签 CA、按域名解密）
- 按客户端 IP 分 Tab（手机、浏览器、测试 App 互不干扰）
- 响应体搜索（正则、大小写）
- 断点、弱网、生命周期脚本
- 请求置顶、按内容类型筛选、列宽会记住

**参数转换**（差异化能力）

- Base64、AES、自定义脚本等规则
- 详情、Mock、调试 API 默认与**明文**交互，发送时自动加密
- [GitHub 短文](./docs/param-transform.md) · [官网完整教程](https://devpeek.ypgao.com/docs/param-transform/)

**Mock 与转发**

- 仅拦请求或仅拦响应；规则**分组**，组内批量启停
- Map Route / 转发规则（整域或 `host + path` 前缀）对接本地服务

**WebSocket**

- 经代理的 **WS / WSS** 会话与 HTTP 并列（握手、帧）
- WS Flow（预览）描述多轮对话 — [官网教程](https://devpeek.ypgao.com/docs/wsmock-dsl/)

**其他**

- 局域网协作 · Chromium 扩展导入 · SQLite 历史 · Windows / macOS 自动更新

桌面端**基础功能永久免费**，Pro / 团队版见 [定价](https://devpeek.ypgao.com/pricing/)。

---

## 5 分钟上手

1. 在 [官网](https://devpeek.ypgao.com/) 或 [GitHub Releases](https://github.com/GYPengDev/devpeek/releases) 下载 Windows 或 macOS 安装包。
2. 手机 Wi‑Fi 代理填 `电脑局域网IP:8888`（标题栏显示端口，可一键复制）。
3. 手机安装并**完全信任**根 CA；目标域名加入 SSL 解密范围。
4. **抓包** Tab 看流量；**调试** Tab 选中手机客户端，刷新页面即可镜像。

清单与排错：[docs/quick-start.md](./docs/quick-start.md) · [官网快速开始](https://devpeek.ypgao.com/docs/quick-start/)

---

## 下载

| 渠道 | 链接 |
|------|------|
| **官网（推荐）** | https://devpeek.ypgao.com/ |
| **GitHub Releases** | https://github.com/GYPengDev/devpeek/releases |
| 安装与证书 | https://devpeek.ypgao.com/docs/install/ |

当前发布 **Windows**（NSIS）与 **macOS**（DMG，Apple Silicon / Intel）安装包。安装包在官网；本仓库跟踪说明与链接。

---

## GitHub 文档 vs 官网

本仓库放 **场景向短文**，方便搜索与发现；带视频、分步截图的完整手册在官网。

| 主题 | GitHub（摘要） | 官网（完整） |
|------|----------------|--------------|
| 快速开始 | [docs/quick-start.md](./docs/quick-start.md) | [中文](https://devpeek.ypgao.com/docs/quick-start/) · [EN](https://devpeek.ypgao.com/en/docs/quick-start/) |
| Charles 替代 | [docs/charles-alternative.md](./docs/charles-alternative.md) | [抓包文档](https://devpeek.ypgao.com/docs/capture/) |
| 参数转换 | [docs/param-transform.md](./docs/param-transform.md) | [中文](https://devpeek.ypgao.com/docs/param-transform/) · [EN](https://devpeek.ypgao.com/en/docs/param-transform/) |
| WebSocket Mock | — | [中文](https://devpeek.ypgao.com/docs/wsmock-dsl/) · [EN](https://devpeek.ypgao.com/en/docs/wsmock-dsl/) |

---

## 更新日志

近期版本摘要：[CHANGELOG.md](./CHANGELOG.md)

完整逐版说明：[devpeek.ypgao.com/changelog](https://devpeek.ypgao.com/changelog/)

---

## 反馈

- **缺陷：** [提交 Issue](https://github.com/GYPengDev/devpeek/issues/new?template=bug_report.yml)
- **功能建议：** [Feature request](https://github.com/GYPengDev/devpeek/issues/new?template=feature_request.yml)
- **使用问题：** [Discussions](https://github.com/GYPengDev/devpeek/discussions) · [联系我们](https://devpeek.ypgao.com/contact/)
- **安全：** [SECURITY.md](./SECURITY.md)

---

## 相关仓库

| 仓库 | 说明 |
|------|------|
| [devpeek-site](https://github.com/GYPengDev/devpeek-site) | 官网源码（Nuxt） |
| [examples/](./examples/) | 配置示例索引 |

---

## 适用人群

移动端前端 · Hybrid / uni-app · RN / Flutter WebView · 壳内 H5 · 需要在真机联调的测试工程师。

---

## 许可

DevPeek 为**专有软件**，保留所有权利。

本仓库仅含文档、发布信息与社区模板，不含应用源码。

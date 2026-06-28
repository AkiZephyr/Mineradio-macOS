# Mineradio macOS

![Mineradio 暗场启动页](./docs/assets/readme/cinema-beat-smoke.png)

Mineradio macOS 是基于 [XxHuberrr/Mineradio](https://github.com/XxHuberrr/Mineradio) 的非官方 macOS 适配维护版。这个仓库会围绕 Mac 桌面体验继续维护：补齐 macOS 打包、平台路径、更新资产选择，并在此基础上探索更适合 macOS 的动效、窗口层级和沉浸式播放体验。

> 说明：本项目不是原作者发布的官方 Mac 版。原项目的代码、设计和品牌来源请见上游仓库；本仓库会在 GPL-3.0 授权范围内继续公开维护修改内容。

## 项目定位

- 面向 macOS 的 Mineradio 适配和长期维护版本
- 保留原项目的沉浸式音乐播放器核心体验
- 优先修复 macOS 运行、打包、路径、更新和桌面集成问题
- 后续会加入更贴近 Mac 使用习惯的交互、动效和视觉细节

如果你需要 Windows 官方安装包，请前往原项目仓库：

[XxHuberrr/Mineradio](https://github.com/XxHuberrr/Mineradio)

## 当前状态

当前版本：`1.1.1`

macOS 适配状态：

- 已支持在 macOS 上开发运行
- 当前公开安装包主要面向 Apple Silicon Mac（arm64 / M 系列芯片）
- 已支持生成 macOS `.app`、`.dmg` 和 `.zip`
- 已将节奏分析缓存、登录 Cookie 和更新下载目录迁移到用户数据目录
- 已按平台选择更新资产，macOS 优先使用 `latest-mac.yml` 和 `.dmg` / `.zip`
- 已去除 macOS 上不适用的 Windows Direct3D Chromium 参数

## 支持范围

当前 Release 安装包优先支持并测试 Apple Silicon Mac：

- Apple Silicon：已发布 arm64 安装包，适用于 M1 / M2 / M3 / M4 系列 Mac
- Intel Mac：暂未作为正式支持平台发布，后续会根据测试条件和用户反馈评估 x64 或 Universal 安装包

如果你使用的是 Intel Mac，请暂时不要把当前 arm64 安装包视为可用版本。欢迎在 Issues 中反馈设备型号、macOS 版本和启动日志，方便后续补齐兼容性验证。

## 核心特性

- Open-Meteo 天气电台，根据位置、城市和天气 mood 生成播放队列
- 网易云音乐账号、搜索、歌单、播客和歌词体验接入
- QQ 音乐搜索、登录态与音源补充接入
- 歌词舞台、自定义歌词、歌词位置与视觉控制
- 基于节奏的电影镜头视觉系统
- 面向长播客和 DJ 曲目的专属视觉模式
- Wallpaper 银河首页背景和播放态视觉切换
- 右键唤起 3D 歌单架，支持歌单队列浏览
- GitHub Releases 更新检测与下载入口

## macOS 构建

```bash
npm install
npm start
```

生成当前 Mac 架构的未压缩 `.app`：

```bash
npm run build:mac:dir
```

生成当前 Mac 架构的 `.dmg` 和 `.zip`。当前公开 Release 主要使用 Apple Silicon / arm64 构建：

```bash
npm run build:mac
```

如需同时构建 Intel x64 与 Apple Silicon arm64 产物，可以使用：

```bash
npm run build:mac:all
```

注意：`build:mac:all` 只代表构建配置保留了 x64 能力，不代表 Intel Mac 已经完成正式适配和发布验证。

未配置 Apple Developer ID 时，可以临时跳过签名做本地构建验证：

```bash
CSC_IDENTITY_AUTO_DISCOVERY=false npm run build:mac
```

## Windows 构建

本仓库仍保留原项目的 Windows 构建脚本，便于和上游保持兼容：

```bash
npm run build:win
npm run build:win:dir
```

Windows 用户如需稳定安装包，建议优先使用上游官方发布版本。

## 与上游的关系

本仓库源自：

[https://github.com/XxHuberrr/Mineradio](https://github.com/XxHuberrr/Mineradio)

主要差异方向：

- macOS 打包与发布配置
- macOS 用户数据路径和缓存目录适配
- macOS 更新资产选择
- macOS 窗口、壁纸和视觉体验维护
- 后续面向 Mac 的独立功能和动效探索

本地仓库建议保留两个远程：

```bash
origin   https://github.com/AkiZephyr/Mineradio-macOS.git
upstream https://github.com/XxHuberrr/Mineradio.git
```

这样既可以维护独立 Mac 版本，也可以按需同步原项目更新。

## 更新机制

Mineradio 会请求 GitHub Releases latest 检测新版本。macOS 版本优先读取 `latest-mac.yml`，并下载适合当前平台的 `.dmg` / `.zip` 产物。

本地验证更新链路时，可以通过 `MINERADIO_UPDATE_MANIFEST` 指向一个本地 manifest JSON 或 HTTP 地址来模拟线上 Release。

## 第三方音乐平台说明

Mineradio macOS 不是网易云音乐、QQ 音乐、腾讯音乐娱乐集团或原 Mineradio 项目的官方客户端，也不隶属于任何音乐平台。

项目中的第三方平台接入仅用于个人学习、本地客户端体验和用户自有账号的播放辅助。请遵守对应平台的用户协议、版权规则和会员权益规则。项目不会提供绕过付费、绕过会员、破解音质或重新分发音乐内容的能力。

## 用户数据与隐私

登录 Cookie、搜索历史、自定义封面、自定义歌词、节奏分析缓存等数据只应保存在本机用户数据目录或浏览器本地存储中，不应提交到仓库。

更多说明见 [PRIVACY.md](./PRIVACY.md)。

## 致谢

感谢 [XxHuberrr](https://github.com/XxHuberrr) 创建 Mineradio 原项目，并以 GPL-3.0 授权开放代码。本仓库的 macOS 适配工作建立在原项目基础之上。

原项目 README 中列出的共创者、体验反馈者和发布准备协助者，同样是 Mineradio 能被继续适配和维护的重要基础。

## 版权与授权

Copyright (C) 2026 XxHuberrr.

本仓库的修改内容由 AkiZephyr 维护，并继续采用 GPL-3.0 授权。详见 [LICENSE](./LICENSE)。

MR Logo、Mineradio 名称、界面视觉设计与原创视觉表达归原作者所有；本仓库仅作为非官方 macOS 适配维护版本使用相关素材和名称。第三方依赖和第三方服务分别遵循其各自授权与服务条款。

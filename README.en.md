# Mineradio macOS

> English | [简体中文](./README.md)

Mineradio macOS is an unofficial macOS-focused port and maintained edition of [XxHuberrr/Mineradio](https://github.com/XxHuberrr/Mineradio). This repository continues the project with a Mac-first desktop experience: completing macOS packaging, platform paths and update asset selection, and exploring macOS-native motion, window layering and immersive playback on top of it.

**Disclaimer:** this is *not* an official Mac release from the original author. The code, design and branding of the original project belong to the upstream repository; the modifications published here are maintained publicly under the GPL-3.0 license.

## Project Positioning

- A macOS adaptation and long-term maintenance branch of Mineradio
- Preserves the immersive music-player core experience of the original project
- Prioritizes fixes for macOS runtime, packaging, paths, updates and desktop integration
- Will progressively add interactions, animations and visual details that fit Mac usage habits

If you need the official Windows installer, please go to the upstream repository:

[XxHuberrr/Mineradio](https://github.com/XxHuberrr/Mineradio)

## Current Status

- Current version: **1.1.3**
- macOS adaptation status:
  - Development and local runs on macOS are supported
  - Public installers currently target Apple Silicon Macs (arm64 / Apple M series)
  - Building macOS `.app`, `.dmg` and `.zip` artifacts is supported
  - Rhythm analysis cache, login cookies and the update download directory have been moved to the user data directory
  - Update assets are selected per platform; macOS prefers `latest-mac.yml` and `.dmg` / `.zip`
  - Windows-only Direct3D Chromium flags have been removed on macOS

## Support Scope

Current release installers are built and tested for Apple Silicon Macs first:

- **Apple Silicon:** arm64 installers are published, for M1 / M2 / M3 / M4 series Macs
- **Intel Mac:** not yet published as a formally supported platform. x64 or Universal installers will be evaluated based on available test conditions and user feedback

If you are using an Intel Mac, please do not treat the current arm64 installer as a usable build for now. Feel free to open an Issue with your device model, macOS version and startup logs so compatibility can be verified and added later.

## Core Features

- Open-Meteo weather radio: generates play queues from location, city and weather mood
- NetEase Cloud Music account, search, playlists, podcasts and lyrics
- QQ Music search, login state and supplementary audio sources
- Lyrics stage, custom lyrics, lyric positioning and visual controls
- Tempo-driven cinematic camera visual system
- Dedicated visual modes for long podcasts and DJ tracks
- Wallpaper galaxy home background and playback-state visual transitions
- Right-click to summon the 3D playlist shelf for browsing playlist queues
- GitHub Releases update detection and download entry point

## macOS Build

```bash
npm install
npm start
```

Build an unpacked `.app` for the current Mac architecture:

```bash
npm run build:mac:dir
```

Build `.dmg` and `.zip` for the current Mac architecture. Public releases currently use Apple Silicon / arm64 builds:

```bash
npm run build:mac
```

To build both Intel x64 and Apple Silicon arm64 artifacts:

```bash
npm run build:mac:all
```

> Note: `build:mac:all` only means the x64 build capability is preserved in the configuration — it does **not** mean Intel Macs are formally adapted or release-verified.

Without an Apple Developer ID configured, you can temporarily skip signing for local build verification:

```bash
CSC_IDENTITY_AUTO_DISCOVERY=false npm run build:mac
```

## Windows Build

The original Windows build scripts are kept in this repository for compatibility with upstream:

```bash
npm run build:win
npm run build:win:dir
```

Windows users looking for a stable installer are advised to use the official upstream release.

## Relationship with Upstream

This repository is derived from:

<https://github.com/XxHuberrr/Mineradio>

Main areas of divergence:

- macOS packaging and release configuration
- macOS user data paths and cache directories
- macOS update asset selection
- macOS window, wallpaper and visual experience maintenance
- Future Mac-specific features and motion exploration

It is recommended to keep two remotes in your local clone:

```bash
origin   https://github.com/AkiZephyr/Mineradio-macOS.git
upstream https://github.com/XxHuberrr/Mineradio.git
```

This way you can maintain the independent Mac edition while syncing upstream updates when needed.

## Update Mechanism

Mineradio queries the GitHub Releases `latest` endpoint to detect new versions. The macOS build reads `latest-mac.yml` first and downloads the `.dmg` / `.zip` artifact matching the current platform.

To validate the update flow locally, point `MINERADIO_UPDATE_MANIFEST` at a local manifest JSON or an HTTP URL to simulate an online release.

## Third-Party Music Platforms

Mineradio macOS is not an official client of NetEase Cloud Music, QQ Music, Tencent Music Entertainment Group, or the original Mineradio project, and is not affiliated with any music platform.

The third-party platform integrations in this project are intended solely for personal learning, local client experience and playback assistance with the user's own account. Please comply with each platform's terms of service, copyright rules and membership benefit rules. This project does not provide, and will not provide, any capability to bypass payment, bypass membership, crack audio quality, or redistribute music content.

## User Data & Privacy

Login cookies, search history, custom covers, custom lyrics, rhythm analysis cache and similar data should only be stored in the local user data directory or browser local storage, and must never be committed to the repository.

See [PRIVACY.md](./PRIVACY.md) for details.

## Acknowledgements

Thanks to **XxHuberrr** for creating Mineradio and open-sourcing it under GPL-3.0. The macOS adaptation work in this repository builds on that foundation.

The co-creators, experience feedback contributors and release-preparation helpers listed in the upstream README are equally important to Mineradio being able to keep getting adapted and maintained.

## Copyright & License

Copyright (C) 2026 XxHuberrr.

Modifications in this repository are maintained by AkiZephyr and continue to be licensed under GPL-3.0. See [LICENSE](./LICENSE).

The MR logo, the Mineradio name, UI visual design and original visual expression belong to the original author; this repository uses those assets and the name only as an unofficial macOS adaptation and maintenance edition. Third-party dependencies and third-party services are subject to their respective licenses and terms of service.

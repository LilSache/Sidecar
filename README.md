# Project Sidecar &nbsp; ![Alpha](https://img.shields.io/badge/status-alpha%2Fbeta-orange?style=flat-square) ![PoC](https://img.shields.io/badge/stage-proof--of--concept-red?style=flat-square)

> [!WARNING]
> 🚧 **Alpha / Beta — Proof of Concept.** This project is under heavy active development. More features are currently broken than working. Expect crashes, missing UI elements, and incomplete functionality. **Not intended for general production use.**

Project Sidecar is a Windows game launcher frontend for handheld PCs like the ROG Ally, Steam Deck, and Lenovo Legion Go. It is heavily inspired by Daijishō on Android — built to bring that same console-like experience to Windows, with full controller navigation, platform artwork, emulator management, and game metadata scraping.

Built on **Avalonia UI** (.NET 8).

A huge thank you to the Daijishō team and community. Their work was the entire inspiration for this project. Please go support them: [github.com/magneticchen/Daijishou](https://github.com/magneticchen/Daijishou)

---

## ✨ Features

* **Widescreen Console Hub**: Smooth, gamepad-navigable platform carousel and grid selection layouts.
* **Daijishō Theme Engine**: Full support for importing and displaying native Daijishō theme packages, automatically applying platform wallpapers and system graphics.
* **Context-Aware Accent Tinting**: Real-time extraction of dominant vibrant colors from game cover art using `ColorExtractorService` to dynamically recolor frontend accents.
* **Game Details & Metadata**: High-fidelity game detail pages featuring clean metadata badges (genre, developer, publisher, release year), description cards, and blurred cover art backgrounds.
* **Game-Specific Soundtrack Scraping**: Intelligent online theme music scraper that finds and caches game soundtracks from YouTube (automatically filtering ads and Shorts) for ambient audio while browsing.
* **Simulated Cloud Backups**: Integrated local OAuth2 simulated Google Drive backup server for secure save game synchronization.
* **RetroAchievements Integration**: Display achievement counts and notifications directly on the UI dashboard.
* **Seamless Input**: Built-in touchscreen swiping, full gamepad navigation, and robust 2D D-pad grid movement.
* **Built-in Setup Wizard**: Easy step-by-step initial installation wizard to configure BIOS paths and download emulator runtimes.

---

## 🛠️ Technology Stack

* **Frontend Framework**: [Avalonia UI](https://github.com/AvaloniaUI/Avalonia) (XAML & C#) for high-framerate, multi-platform rendering.
* **Target Runtime**: .NET 8.0
* **Audio Library**: Managed audio playback system via cross-platform bindings.
* **Database**: SQLite database backend for fast caching of metadata, games list, and emulator parameters.

---

## 🚀 Getting Started

### Prerequisites
* **.NET 8.0 SDK** (or later)
* Windows 10/11

### Compiling and Running
To restore dependencies and build the application:
```powershell
dotnet build ProjectSidecar.sln
```

To run the application:
```powershell
dotnet run --project Sidecar.App/Sidecar.App.csproj
```

---

## 📁 Repository Structure

```
├── ProjectSidecar.sln        # Main Visual Studio / Rider Solution
├── README.md                 # Project Overview & Guidelines
├── Sidecar.App/             # Avalonia UI Frontend (Views, ViewModels, Assets)
├── Sidecar.Background/      # Background Services (Scanners, Workers)
├── Sidecar.Browser/         # Chromium Embedded Browser Overlay
├── Sidecar.Core/            # Config, Models, Core Services (Theme, Logger, Security)
├── Sidecar.Desktop/         # Native Desktop Integrations & Helper Hooks
├── Sidecar.Emulation/       # Emulator Installer and Launch Helpers
└── Sidecar.Integrations/    # Third-party Metadata Scrapers & APIs
```

---

## ⚠️ Known Issues & Limitations

* **Controller navigation** is still imperfect in many views — some buttons may not respond correctly
* **Carousel centering** can still shift on first and last cards in certain scenarios
* **Daijishō theme import** — wallpapers load but full theme color/accent pipeline is only partially wired
* **YouTube music scraper** may return no result for obscure or very old game titles
* **YouTube rate limiting** (HTTP 429) can occur during rapid game browsing
* **Aspect ratio on non-16:9 displays** — theme wallpapers may crop or stretch
* **Google Drive Backup** is a simulated flow — no real cloud sync without production API credentials
* **Daijishō backup import** from Android — UI stubbed, not implemented
* **Save file converter** between emulators — not yet implemented
* **Boot animation / custom loading screen** — file upload works, playback not fully wired
* **Custom frontend fonts** — setting exists, not fully applied to all UI elements
* **Resolution / refresh rate selector** — UI present, not fully applied at runtime
* **Wallpaper Engine integration** for live wallpapers — planned, not started
* **BIOS hash verification** may flag custom or region-variant BIOS dumps as unconfigured
* **Emulator download URLs** may break if upstream GitHub release tags change
* **Ryujinx** downloads from a community mirror due to original project shutdown — may become unavailable
* **L1/R1 tab switching** between Library, Apps, and Settings — partially working, context-dependent
* **RetroAchievements** — display wired, live achievement tracking not fully implemented
* **Global `.exe` search** — basic implementation, deep scan may miss certain install locations
* **Microsoft Edge block** — best-effort only, cannot prevent all Edge invocations at OS level
* **Device detection / screen optimization** — runs once on first boot, manual adjustment needed for edge cases
* **Setup wizard emulator downloads** — some emulators may still fail on first attempt due to network timing

---

## 📜 License

This project is licensed under the permissive MIT License. See [LICENSE](LICENSE) for details.


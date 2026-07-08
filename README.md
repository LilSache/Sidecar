# Project Sidecar

> [!WARNING]
> **This project is currently a Proof of Concept (PoC) and is under heavy active development. More features are currently broken than working.** It is not yet intended for general production use. THIS WAS CREATED BY A DUDE AND AI BASICALLY BUILT THIS I WILL NOT LIE OR TRY TO BE DECEPTIVE. PLEASE SUPPORT TAPIOCA FOX AND OTHER REAL DEVS PLEASE. 

Project Sidecar is a premium console-like game launcher and library frontend for Windows, meticulously optimized for handheld PCs WITH WINDOWS 11 (like the ROG Ally, Steam Deck, and Lenovo Legion Go) and controllers. **It is heavily influenced by the aesthetic, layout, and theme structure of the popular Android launcher Daijishō**, adapting its premium visual design language to deliver a high-performance 1080p 120Hz dashboard for all your PC games and emulated classics.

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

* **YouTube Rate Limiting**: Extensive/rapid scraping of theme music tracks may trigger temporary HTTP 429 Rate Limiting from YouTube search endpoints. The app includes a 1.5-second scroll debounce to prevent spamming queries.
* **Aspect Ratio Variations in Themes**: Certain custom community Daijishō themes use background wallpapers that might crop or stretch on ultra-wide screens or non-16:9 displays.
* **Simulated Google Drive Backups**: The cloud backup link utilizes a local web server (loopback on port `50352`) and is running in high-fidelity simulation mode. Real sync requires registering custom production developer API credentials.
* **BIOS Hashing Check**: Emulation BIOS verification checks against specific SHA-256 signatures. Custom system variations (e.g. modified bios dumps) may report as "Not configured" even if functionally compatible.
MANY OTHER ISSUES I REALLY HOPE YOU UNDERSTAND THIS.
I AM WORKING ON THESE ISSUES AS SOON 
---

## 📜 License

This project is licensed under the permissive MIT License. See [LICENSE](LICENSE) for details.

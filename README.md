<!--
  Manor Lords Co-op Mod — Proprietary Software — All Rights Reserved.
  See LICENSE in the repository root.
  Unauthorized copying, modification, redistribution, derivative works,
  reverse engineering, or AI/LLM training/extraction is strictly prohibited.
-->

# Manor Lords Co-op Mod

> **PROPRIETARY SOFTWARE — ALL RIGHTS RESERVED**
> This repository is **source-available for inspection and personal, non-commercial gameplay only**.
> It is **NOT open source**. Copying, modifying, redistributing, issuing unofficial updates/bug fixes, reverse engineering, or using any part of this codebase with AI/LLM tools to build, port, or reimplement competing projects is **strictly prohibited** without prior explicit written permission from the Copyright Holder.
> See [`LICENSE`](LICENSE) for full binding legal and AI-policy terms.

---

## Overview

**Manor Lords Co-op** brings true multi-lord multiplayer (co-op & PvP) to *Manor Lords* (tested on build `0.8.117`). Each player commands their own independent lord, region, economy, armies, and diplomacy inside a shared live world.

### Key Features
- **Independent Lords per Player (up to 6 players):** Every human player rules their own region, settlement, treasury, policies, and armies — alongside optional AI lords and the Baron.
- **Full World & Construction Sync:** Point buildings, burgage plots, fields, pastures, marketplaces, castle/manor walls & gates, roads with native pathfinding, wooden bridges, upgrades, and live construction progress.
- **Host-Authoritative Army, Mercenary & Combat Sync:** Synchronized militia, retinue customization, mercenary hiring/movement, squad formations/stances/skills/camps, Host-authoritative melee/ranged combat, HP, morale, routs, and casualties.
- **Bidirectional Diplomacy & PvP:** War/peace declarations, alliances, territory claims, challenges, caravans, and raiding.
- **Adaptive High-Speed Clock Sync (1x - 6x):** Rate matching, stall barriers, and lobby speed voting to keep peers synchronized even at high speeds.
- **In-Game Overlay & Lobby Browser:** Steam relay / P2P & LAN lobbies, region/scenario selector, saved-game co-op support, ping markers, and map visit sync.
- **Full 7-Language Support:** Switch live between **English, Türkçe, Русский, Deutsch, 简体中文, Français, and Polski** directly from the Multiplayer Menu or Settings — covering the Portal UI, in-game Overlay/HUD, Main Menu button, notifications, and game language sync (with full Cyrillic & CJK font support).
- **Zero-Script Drop-In & Vortex Ready:** No `.bat`, `.ps1`, or `.sh` scripts required — drop the `ManorLords` folder into your game directory (or install via Vortex) and launch directly from Steam.
- **Windows & Linux (Proton / Steam Deck) Support** in one unified release archive.

---

## Download

- **Direct Download (v1.0.7):** [ManorLords_Multiplayer_Mod.zip](https://github.com/p3pabaddon/manor-lords-multiplayer/raw/main/ManorLords_Multiplayer_Mod.zip) (47.55 MB — zero-script drop-in / Vortex ready)
- **Nexus Mods:** https://www.nexusmods.com/manorlords/mods/465 *(exact same archive — supports both **Vortex / Mod Manager** and **Manual Download**)*

---

## Quick Installation (No `.bat` / No Installer Needed!)

> **Important — Upgrading or Existing UE4SS Users:**
> - **If you previously installed `MLUE4SS` (v3.0.1) or other UE4SS/PAK mods via Vortex, remove/disable them first** and delete any old `xinput1_3.dll` or root `UE4SS.dll` inside `ManorLords\Binaries\Win64\` — older `UE4SS v3.0.1` crashes Manor Lords `0.8.117`.
> - This package already includes pre-configured **RE-UE4SS v4.0.0 (UE 5.5)** (`dwmapi.dll` + `ue4ss\UE4SS.dll`).
> - **Requires Steam build `0.8.117`** (Steam beta branch).

### Windows — Manual Drop-In (Recommended)
1. Download [`ManorLords_Multiplayer_Mod.zip`](https://github.com/p3pabaddon/manor-lords-multiplayer/raw/main/ManorLords_Multiplayer_Mod.zip) (or from Nexus Mods).
2. Open your Manor Lords game folder (`Steam -> Right-click Manor Lords -> Manage -> Browse local files`).
3. Extract the **`ManorLords`** folder from the ZIP directly into your `Manor Lords` game folder (merge/overwrite if prompted).
4. Launch Manor Lords normally via **Steam -> Play** and click **Multiplayer** in the Main Menu (or press **`F10`**).

### Windows — Vortex / Mod Manager
1. Download via **Mod Manager Download (Vortex)** on Nexus Mods and enable the mod.
2. Deploy mods (make sure no conflicting legacy `MLUE4SS v3` / `xinput1_3.dll` mod is enabled).
3. Launch Manor Lords normally via **Steam -> Play**!

### Linux / Steam Deck (Proton)
1. Extract the **`ManorLords`** folder from the ZIP directly into your `Manor Lords` game directory.
2. In Steam -> Right-click *Manor Lords* -> Properties -> **Launch Options**, set:
   ```
   WINEDLLOVERRIDES="dwmapi=n,b" %command%
   ```
3. Launch Manor Lords via Steam and open the Multiplayer Portal at `http://127.0.0.1:27065`.
4. See [`README.txt`](README.txt) for full Windows & Linux instructions.

---

## In-Game Controls & Hotkeys

| Key | Action |
|---|---|
| `F3` | Minimize or hide the top-left Realm Roster HUD (Full -> Minimized -> Hidden) |
| `F10` | Open / close the Co-op Lobby & Multiplayer Overlay |
| `F4` | In-game Host & Steward Menu (including live Speed Control switcher) |
| `F7` | Diplomacy Panel |
| `F5` | Manual Host-authoritative world sync (Host only) |
| `F6` | Reload synced save (Client) |
| `F8` | Drop forensic sync trace bookmark |
| `Alt / Ctrl / Shift + MMB` | Tactical map ping marker visible to teammates |

---

## Troubleshooting & Diagnostics

If you encounter a desync or issue during a match:
1. Press **`F8`** in-game to bookmark the exact moment.
2. Open the Multiplayer Portal (**`F10`**) -> click **Settings** -> click **Export Sync Logs to Desktop** (no batch file required).
3. A diagnostic ZIP archive (`ManorLords_SyncLog_*.zip`) and summary report are generated on your Desktop containing `UE4SS.log`, `daemon.log`, latest `CrashContext`, and forensic sync trace summaries.

---

## Legal Notice, Exclusivity & Anti-AI Protection

- **All Rights Reserved:** Copyright (c) 2026 Manor Lords Co-op Author. No open-source license is granted.
- **Official Distribution Only:** Only the Copyright Holder is authorized to distribute, update, patch, or publish bug fixes for this mod. Unofficial forks, re-uploads, repacks, or third-party patches are strictly prohibited without prior explicit written permission from the Copyright Holder.
- **No AI / LLM Extraction or Training:** All Text and Data Mining (TDM) and AI/LLM ingestion, training, extraction, refactoring, or reimplementation rights are expressly reserved under **EU Directive 2019/790 Article 4(3)** and **17 U.S.C. § 106**.
- **Copyright Management Information (CMI):** Removing [`LICENSE`](LICENSE) or per-file copyright headers violates **17 U.S.C. § 1202 (DMCA)**.
- **Third-Party Attribution:** MIT-licensed portions and third-party dependencies are documented in [`docs/THIRD_PARTY_NOTICES.md`](docs/THIRD_PARTY_NOTICES.md).
- **Disclaimer:** Unofficial fan modification. Not affiliated with Slavic Magic or Hooded Horse.

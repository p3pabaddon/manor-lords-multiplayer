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
- **Full 8-Language Support:** Switch live between **English, Türkçe, Русский, Deutsch, 简体中文, Français, Polski, and Čeština** directly from the Multiplayer Menu or Settings — covering the Portal UI, in-game Overlay/HUD, Main Menu button, notifications, and game language sync (with full Cyrillic, Central European & CJK font support).
- **Windows & Linux (Proton / Steam Deck) Support** in one unified release archive.

---

## Download

- **Direct Download (v1.0.20):** [ManorLords_Multiplayer_Mod.zip](https://github.com/p3pabaddon/manor-lords-multiplayer/raw/main/ManorLords_Multiplayer_Mod.zip) (47.7 MB)
- **One-Click Delta Updater:** Existing v1.0.8+ users can double-click `4_CHECK_AND_UPDATE.bat` to apply the ~1 MB delta patch automatically.
- **Nexus Mods:** https://www.nexusmods.com/manorlords/mods/465

### What's Fixed in v1.0.20
- **Multiplayer Button & F10 Portal Reliability Fix:** `1_INSTALL.bat` and `4_CHECK_AND_UPDATE.bat` now deploy a **self-contained runtime** (`daemon/`, `ui/`, `bin/`, `runtime/node.exe`) directly inside `ue4ss\Mods\ManorLordsCoop\`, so launching from Steam uses pure-ASCII relative paths and **never breaks** if you move, rename, or delete your downloaded ZIP folder or extract to Turkish/Russian/non-ASCII folders on `D:\` / `E:\` drives. Also fixed a Node.js v24 `realpathSync` bug that caused `coop_daemon.mjs` to exit silently on symlink/OneDrive/junction paths, cleared stale `shuttingDown` flags before spawning `CoopOverlay.exe`, and added a clear Windows popup alert if the portal ever fails to start.
- **Client Militia Disband Sync & Post-F5 Fix (`coopnative v0.8.9`):** Fixed Client Militia disbands not syncing to Host and getting blocked after a Host F5 resync. `coopnative v0.8.9` now repairs Militia ownership using `FSquad::originRegion (+0x1F8)` (not just `currentRegion`), captures native C++ UI disband calls (`SetSkillActive -> RequestDisbandSquad`) directly into `coop_disband_poll()`, adds a Lua `unitCount -> 0` fallback, and allows Host to accept disbands for Client-owned Militia regions.
- **Host 3×3 Rain Sheet / Sky Cutout Fix (`coopnative v0.8.9`):** Added an AOB-verified native guard (`cameraClearanceGuard` at `0x4B747C0`) blocking silenced secondary human pawns from overwriting Host's global `buildingMPC["camera_clearance"]` every frame, paired with an outside-Paper-Map `playerRef` guard.
- **Client Burgage Homes Disappearing on Server Sync Fix:** Fixed residential plot projection aborting on a single SEH-faulting `slicingAngle` and discarding valid outer Burgage polygons when sub-plot replay returned `0/N`.
- **Client Combat-Tick Stability Fix:** Forward-declared `read_lua_combat` in `npc_mirror.lua`, eliminating silent nil-global errors during active combat ticks.

### Previous (v1.0.19)
- **Post-Resync Client Desktop Crash Fix (`coopnative v0.8.8`):** Added an AOB-verified native null-pointer shield (`removeProblemGuard` at `0x4C691E0`) fixing a crash (`EXCEPTION_ACCESS_VIOLATION` reading `0xD88` at `+0x4C691EA`) that could close the Client's game seconds after a periodic World Resync reload when assigning an ox guide (`newTask_setGuideTask`) to an ox whose `homeRegion` was null. Protects all 65 callers of `ARegion::removeProblem` across the game binary.
- **Diagnostic Trace Version Tag:** Updated the sync log version label to `v62_OxGuideCrashGuard` so exported diagnostic logs clearly show the exact active release.

### Previous (v1.0.18)
- **Turkish & Multi-Language Reset Fix:** Fixed Manor Lords automatically resetting back to English when joining or creating a Multiplayer room. Updated all `SetLanguage` locale mappings to match the exact game codes (`tr_TR`, `ru_RU`, `de_DE`, `zh_CN`, `fr_FR`, `pl_PL`, `cs_CZ`, `en_US`, `es_ES`, `pt_BR`) and prevented the mod's default English setting from overwriting your existing in-game language when entering a lobby.

### Previous (v1.0.17 Hotfix)
- **Save Sync Failure Hotfix (`"Failed to receive save from host"`):** Fixed a regression in `v1.0.16` where `SAVE_SYNC_COMPLETE` traveled via Steam Lobby Chat ahead of the Steam P2P save chunks, causing instant SHA-256 mismatches during match start and join-in-progress. Save transfers now travel strictly in order on the same reliable P2P lane, and the client receiver is now fully resilient to out-of-order completion packets and duplicate `SAVE_SYNC_BEGIN` headers.
- **Premature P2P Reset Fix:** Fixed the stale-connection watchdog resetting fresh Steam P2P sessions right after joining or while a save transfer / live match was active.

### Previous (v1.0.16)
- **Client Militia Rally, Disband & Removal Fix (`coopnative v0.8.7`):** Fixed Client players being unable to rally Militia, freshly rallied Militia immediately disbanding on Client, and deleted/disbanded Client Militia staying alive as ghost squads on Host (which previously returned on F5).
- **Brigands & Raiders Target All Human Lords:** Fixed Brigands/Raiders only targeting the Host; raiders now properly target all settled human lords and display a clear shared alert naming which region and lord is being raided (in all 8 supported languages).
- **Client Rain, Overlapping Double Music & Building Selection Recovery:** Fixed Client rain visuals sticking to Host, permanently stopped the hidden duplicate music track from playing out of sync, and added automatic hover/cursor/UI recovery so Clients don't lose building highlighting or map selection.
- **Lobby Map Crop & Spawn Alignment Fix:** Fixed the lobby map preview cropping top/bottom edges so all spawn shields line up cleanly with the full parchment map.
- **500+ ms Lobby Ping & Stuck Match Start Fix:** Cleaned up stale connections when recreating lobbies, stopped lobby keepalives from inflating ping to 500+ ms, prevented bulk save transfers from flooding Steam lobby chat on SDR resets, deduplicated repeated handshake ACKs, and added automatic match-start retry & save-sync recovery.
- **Storehouse Livestock & Building Sync Fixes:** Stopped Cows, Chickens, other live animals, and special non-stock items (such as Church graves/corpses) from being placed into Storehouses or Granaries, and fixed **Corpse Pit** and **Dyer's Workshop** construction sync for Client players.

### Previous (v1.0.15)
- **Rehost Starting Resource Duplication Fix:** Fixed an issue where rehosting an existing co-op save re-applied every player's starting lord trait resources and treasury/wealth bonuses to their Stockpile every time the save was loaded. Starting packs are now granted only once on fresh campaigns (or once for a brand-new player joining a saved campaign for the very first time).
- **Guest Storehouse Shield Drop-Off Animation Freeze Fix (`coopnative v0.8.6`):** Fixed an issue where guest villagers (such as traders and unassigned workers) assigned to an unrallied militia unit were mistakenly locked by the client combat sync, blocking task completion and freezing them inside the Storehouse while dropping off Shields or handling early-game weapons. Unrallied militia villagers and soldiers hauling/dropping off equipment at Storehouses now complete their tasks and animations normally on guest PCs while rallied armies and combat stay fully Host-authoritative.

### Previous (v1.0.14)
- **Instant Lobby Kick Fix (`coopnative v0.8.5`):** Added lobby-relayed reliable keepalive heartbeats and lobby control fallback (`HANDSHAKE`, `LOBBY_STATE`, `CLIENT_READY`, `START_MATCH`, `PING`/`PONG`), plus raised Steam SDR `TimeoutInitial` (`10s -> 25s`) and `TimeoutConnected` (`20s -> 30s`), preventing clients from being kicked ~12s after joining a lobby when Steam P2P takes longer to connect or drops a relay route.
- **Steam P2P Channel-1 Recovery (`eResult=35`):** Properly closes and re-accepts failed Valve SDR sessions on `session_failed` and enables `AutoRestartBrokenSession` on both reliable and unreliable sends in `coopnative.dll` and `SteamBridge.exe`.
- **Mid-Game Disconnect & Transparent Re-Attach Fix:** Raised default peer/host silence timeouts to `30s`/`35s` (and `45s` while waiting in a live Steam lobby), removed the aggressive `4.5s` drop after transient `session_failed`, and added seamless 120s peer re-attach so returning mid-match traffic restores full bidirectional sync on the original peer slot instead of creating a dead ghost peer (`peers=0`).
- **Clean Leave Ghost Suppression:** Ignores trailing in-flight packets for 3s after a clean `PEER_LEAVE` / kick (while allowing immediate fresh rejoins) so departed players never respawn as empty phantom peers.

### Previous (v1.0.13)
- **Host Ambient-Sound CTD Fix (`coopnative v0.8.4`):** Added an AOB-verified native guard (`unitLocRefGuard` at `0x4DB81B0`) preventing `EXCEPTION_ACCESS_VIOLATION` (`+0x4DB81BF`) when `ASMUnit::getLocationRef` reads an invalid/non-canonical `masterPtr`.
- **Client-Raised Militia & Mercenary Squad Protection:** Fixed Host `census[cN]` and Client `calive` mutually killing freshly raised Client soldiers within a minute (fixing permanent villager loss, greyed-out Militia redeploy, undeplyable Mercenaries draining Treasury, and shrinking squads while marching home).
- **Phantom Extra-Unit Spike Fix:** Stopped per-soldier `spawnCompleteUnit` calls on squadded units (which spawned full 36-man squads per AI Manor retainer, causing `+343` extra units and sustained CPU load).
- **Allied Squad Command Guard:** Blocked Non-Host players natively (and in Lua) from moving, dragging, or rallying Host's squads, and fixed `RequestDisbandSquadDetour`'s `isAI` offset (`0xB80` -> `0x34D`).
- **Foreign Merchants, Trade Sync, Bandit Camps & Non-Host Weather:** Exempted `FreeMerchant`/`FreeLivestockMerchant` units from puppet locking (eliminating backward rubberbanding & lost carts), fixed `changeTradeRule` dropping rules, added owner-authoritative trade rule/target/route reconciliation in `delta.lua`, added Client->Host `world.campCleared` sync + 120s respawn guard to stop infinite Bandit Camp respawns, silenced non-local human pawn rain/FX + rebound `WeatherMaster` on Client, and resolved persistent `[squad] lord=5`, `[combat]` pacing, and `[bld]` Marketplace/upgrade-sibling mismatches.

### Previous (v1.0.12)
- **Client Storage-Cache CTD Fix (`coopnative v0.8.3`):** Added a signature-verified native guard (`storageCacheGuard` at `0x4C49280`) preventing `EXCEPTION_ACCESS_VIOLATION reading 0x1E0` (`+0x4C492A1`) in `ARegion::updateStorageCache` when `ASMUnit::performHit(12)` calls it with a null `unit->Region`, paired with Lua `Region` initialization/repair in `npc_mirror.lua`, a 60m civilian bind cap, and automatic release of persistently unbound non-combat extras.
- **Late-Join Steam Thread Heap Corruption CTD Fix (`0xC0000374`):** Serialized 100% of in-process Steamworks API calls onto UE5's `OnlineAsyncTaskThreadSteam` via an atomic Delay-Import/Import IAT hook on `SteamAPI_RunCallbacks`, eliminating concurrent mutations of Steamworks' unsynchronized `m_mapCallResults` RB-tree; added `COOP_FORCE_EXTERNAL_STEAM_BRIDGE=1` / `forceExternalSteamBridge` config toggle for A/B testing.
- **Paused Bandit Squad `[squad] lord=5` False Mismatch Fix:** Added an explicit `sqMode` (`"count"` / `"pos"`) field to `sync.hash` so Host and Client always hash `lord=5` in the exact same format, paired with a pause-aware combat clock and Client-side combat window aging.
- **Steam Outage / Re-Logon Resilience:** Prevented the lobby from falsely disbanding as `host_left` (or dropping active peers as `left_lobby`) when Steam momentarily drops lobby membership during a CM outage while P2P traffic stays alive, and added automatic non-destructive `rejoin_lobby` on `SteamServersConnected_t`.
- **Late-Join AI Lord Slot/Region Swap Fix:** Fixed brand-new late-joiners hijacking a running AI lord's pawn slot and region; late-joiners now spawn a fresh lord in their chosen open region, AI spawn assignments stay frozen while `in_game`, and crashed teammates reclaim their original human lord slot by SteamID even with a new `peerId`.

### Previous (v1.0.11)
- **Castle Creator Wall-Rebuild CTD Fix (`coopnative v0.8.2`):** Added a signature-verified native guard (`castleWallSnapGuard` at `0x4D47B20`) preventing `EXCEPTION_ACCESS_VIOLATION reading 0x8` (`+0x4D47CED`) inside Castle Planner (`RefreshCastlePlanner`) when rebuilding or opening Castle Creator on a wall whose `smoothPoints` spline array is empty after a save reload.

### Previous (v1.0.10)
- **Foreign Trader CTD Fix (`coopnative v0.8.1`):** Fixed a vanilla Manor Lords `0.8.117` (`26185246`) null-pointer crash at `ManorLords-Win64-Shipping+0x4E01B0C` (`reading 0x648` in `ASMUnit::transferGood` when a foreign trader buys goods) with a signature-verified runtime guard, alongside the `APawnCPP::extractSmoothSide` guard, dynamic UE5 reflection offset sync, and an in-process C++ Steamworks P2P bridge.
- **Persistent Desync & Pull-Loop Fixes (`bld`, `econ`, `combat`, `squad`):**
  - `SC.hash_bld` now skips auto-spawned / non-placeable types (market stalls `91–93`, tents, carts, rubble, bridges, army camps, AI plots) and matches `bld_sync` ownership rules.
  - `SC.hash_econ` skips unsyncable livestock (`STORAGE_ANIMALS`), aligns on game day (`±0.08d`), and `delta.apply` uses tolerance `1` on surgical pulls while `correct_stock` prioritizes storages with actual free capacity and distributes across up to 24 buildings.
  - Fixed `SC.hash_combat` hashing `"idle"` into `c301cf93` (bypassing the idle guard), blocked main-menu hash comparisons, and stopped idle bandit camp squads (`lord=5`) from triggering grid-boundary pulls and repeated move orders when already at target.
- **Security Hardening:** Strictly sanitized peer-supplied save slot names & enforced `SaveGames` directory containment in `coop_daemon.mjs`, `coat_renderer.mjs`, and `world_data.mjs`; restricted host `SAVE_SYNC_RETRY` to active co-op sync slots only; capped incoming save transfer buffers & chunk bounds; and added `Host`, `Origin`, `Sec-Fetch-Site`, and `Content-Type: application/json` CSRF protections to the local UI server.

### Previous (v1.0.9)
- **Mid-Game CTD Fix (`coopnative v0.7.3`):** Added a native detour guarding `APawnCPP::extractSmoothSide` (`0x4B3FC90`) against null `ownerPawn` during building setup/completion, auto-healed missing `ownerPawn` from `Region`, and routed all `bld_sync` upgrades/rebuilds through SEH-guarded `BeginUpgrade`.
- **Host Strategic Paper Map Fix:** Mirrored `PaperMapViewChanged`, `setMapMode`, `AResourceNode` decals, `mapPlane` material binding, and MPC zoom/desaturation flags across human pawns so the Host sees all hand-drawn icons, resource decals, settlements, and enemy camps on the Paper Map.
- **Forensic Log Collector & Exporter Fix:** Replaced the broken CMD-quoted PowerShell block in `3_COLLECT_AND_ANALYZE_LOGS.bat` with `tools/collect_logs.ps1`, added UTF-8 Windows Known Folder / OneDrive / Cyrillic / Turkish Desktop resolution + Steam registry `UE4SS.log` detection in both the `.bat` and in-game exporter, and fixed NTFS junction path matching in `analyze_sync_trace.mjs`.

---

## Quick Installation

> **Important — Manual Install Only (Do NOT use Vortex):**
> - **Do NOT install via Vortex.** Vortex treats the bundled `UE4SS v4.0.0` as a standalone MLUE4SS replacement and skips the installer.
> - **If you previously installed `MLUE4SS` (v3.0.1) or other UE4SS/PAK mods via Vortex, disable/remove them in Vortex first** — older `UE4SS v3.0.1` and outdated third-party mods crash Manor Lords `0.8.117` when starting a match.
> - Running `1_INSTALL.bat` automatically backs up conflicting legacy UE4SS files (`_ue4ss_vortex_backup\`), installs the required **UE4SS v4.0.0 (UE 5.5)**, and warns if other third-party mods remain installed.
> - **Requires Steam build `0.8.117`** (Steam beta branch).

### Windows
1. Download the official release archive from the **official GitHub** or **official Nexus Mods** page (**Manual Download**).
2. Extract the **entire** archive to an ASCII-only folder (e.g., `C:\ManorLordsCoop\`).
3. Double-click **`1_INSTALL.bat`** (one-time setup — automatically detects Manor Lords, replaces any older Vortex UE4SS v3.0.1 with bundled UE4SS v4.0.0, and deploys the Co-op mod).
4. Start the game via **`2_LAUNCH_GAME.bat`** (or directly through Steam after installation).

### Linux / Steam Deck (Proton)
1. Extract the official release archive to a permanent folder.
2. Run **`bash 1_INSTALL_LINUX.sh`** once to install the mod into your Steam / Proton directory.
3. Configure Steam Launch Options to `"<path>/2_LAUNCH_GAME_LINUX.sh" %command%` (or `WINEDLLOVERRIDES="dwmapi=n,b" %command%`).
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

If you encounter a desync or crash during a match:
1. Press **`F8`** in-game to bookmark the exact moment.
2. Open the Multiplayer Portal (**`F10`**) -> **Settings** -> **Export Sync Logs to Desktop**, OR double-click **`3_COLLECT_AND_ANALYZE_LOGS.bat`** after closing the game (on both Host and Client PCs).
3. A diagnostic ZIP archive (`ManorLords_SyncLog_*.zip`) and summary report are generated on your Desktop containing `UE4SS.log`, `daemon.log`, latest `CrashContext`, and forensic sync trace summaries.

---

## Legal Notice, Exclusivity & Anti-AI Protection

- **All Rights Reserved:** Copyright (c) 2026 Manor Lords Co-op Author. No open-source license is granted.
- **Official Distribution Only:** Only the Copyright Holder is authorized to distribute, update, patch, or publish bug fixes for this mod. Unofficial forks, re-uploads, repacks, or third-party patches are strictly prohibited without prior explicit written permission from the Copyright Holder.
- **No AI / LLM Extraction or Training:** All Text and Data Mining (TDM) and AI/LLM ingestion, training, extraction, refactoring, or reimplementation rights are expressly reserved under **EU Directive 2019/790 Article 4(3)** and **17 U.S.C. § 106**.
- **Copyright Management Information (CMI):** Removing [`LICENSE`](LICENSE) or per-file copyright headers violates **17 U.S.C. § 1202 (DMCA)**.
- **Third-Party Attribution:** MIT-licensed portions and third-party dependencies are documented in [`docs/THIRD_PARTY_NOTICES.md`](docs/THIRD_PARTY_NOTICES.md).
- **Disclaimer:** Unofficial fan modification. Not affiliated with Slavic Magic or Hooded Horse.

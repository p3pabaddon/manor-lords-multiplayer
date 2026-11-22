============================================================
  MANOR LORDS CO-OP & PVP (STEAM P2P) - INSTALLATION GUIDE
============================================================

COPYRIGHT & LICENSE NOTICE:
  Copyright (c) 2026 Manor Lords Co-op Author. All Rights Reserved.
  This mod is licensed strictly for personal, non-commercial gameplay
  of Manor Lords via official releases (Nexus Mods / official GitHub
  Releases). Modification, redistribution, unofficial forks/updates,
  reverse engineering, and AI/LLM ingestion or code extraction are
  strictly prohibited without prior explicit written permission from
  the Copyright Holder. See LICENSE for full binding terms.

PREREQUISITES:
- Steam must be running and logged in.
- Manor Lords must be installed via Steam (tested on build 0.8.117 / Steam beta branch).
- MANUAL INSTALL ONLY (DO NOT USE VORTEX):
  * Do NOT install this archive through Vortex.
  * If you previously installed MLUE4SS (v3.0.1) or other Manor Lords mods via Vortex,
    disable/remove them in Vortex first! Old UE4SS v3.0.1 and outdated UE4SS/PAK mods
    will crash Manor Lords 0.8.117 when starting a match.
  * 1_INSTALL.bat automatically backs up conflicting legacy UE4SS files into
    _ue4ss_vortex_backup\ and installs the required bundled UE4SS v4.0.0 (UE 5.5).
- NO port forwarding is required; all game traffic runs over Steam P2P.

============================================================
  WINDOWS INSTALLATION & LAUNCH
============================================================
STEP 1 - INSTALL (First-time setup or after updates):
1. Extract this folder from the ZIP into an ASCII-only path
   (for example: C:\ManorLordsCoop).
2. Double-click "1_INSTALL.bat".

STEP 2 - LAUNCH THE GAME:
1. Double-click "2_LAUNCH_GAME.bat" (launches Manor Lords via Steam).
   (Alternatively, launch Manor Lords directly from Steam and click
   "Multiplayer" in the Main Menu, or press F10.)

============================================================
  LINUX / STEAMOS (PROTON) INSTALLATION & LAUNCH
============================================================
- Cross-play between Windows Host <-> Linux Client works with the
  exact same version. On Linux/Steam Deck, the Co-op Portal opens in
  your web browser (http://127.0.0.1:27065) instead of WebView2 HUD.

STEP 1 - INSTALL (Terminal):
1. Extract this folder anywhere (e.g. ~/ManorLordsCoop).
2. Open a terminal inside the folder and run:
     bash 1_INSTALL_LINUX.sh
   (Custom game path:
     bash 1_INSTALL_LINUX.sh --game-dir "/path/to/Manor Lords/ManorLords/Binaries/Win64")

STEP 2 - STEAM LAUNCH OPTIONS (REQUIRED ON PROTON):
  Steam -> Right-click Manor Lords -> Properties -> General -> Launch Options
  Set to (copy the exact path printed by Step 1):
    "/path/to/ManorLordsCoop/2_LAUNCH_GAME_LINUX.sh" %command%
  (Minimal alternative: WINEDLLOVERRIDES="dwmapi=n,b" %command%)

STEP 3 - PLAY:
  Launch Manor Lords via Steam, then click "Multiplayer" (or press F10).
  On Steam Deck Game Mode, open http://127.0.0.1:27065 in Steam Browser.

============================================================
  HOW TO PLAY
============================================================
- HOST (Co-op / PvP / Free Diplomacy):
  1. Click "Multiplayer" (or press F10) in-game to open the integrated
     Multiplayer Portal.
  2. Follow "+ Create Lobby" -> Save Selection -> Character & Coat of Arms
     -> Map Region Selection & Game Settings.
  3. Open your room as Public or Password-Protected Private.

- CLIENT (Joining & Drop-in Live Sync):
  1. Click a Public/Private room in the lobby browser (or enter SteamID /
     Lobby Code via Direct Join).
  2. Click "Select / Edit Character" in the bottom-right of the lobby to
     confirm your lord, pick your starting region on the map, and click
     "Ready".
  3. Even if a match is already in progress, clicking "Join Active Game
     (Live Sync)" automatically pauses the world, syncs the save, and
     drops you in.

============================================================
  IN-GAME HOTKEYS
============================================================
- Top-Left Transparent HUD : Players, SteamID, ping (ms), ally/enemy
                             status, and live FPS.
- F3                       : Minimize or hide the top-left Realm Roster HUD
                             (cycles Full -> Minimized -> Hidden).
- F4                       : In-game Host & Steward Menu (Cheats,
                             Resource Multipliers, Live Speed Control Mode,
                             Players, and HUD display toggle).
- F7                       : Diplomacy Panel (Ally / Neutral / Enemy +
                             Ally Attack / Backstab Confirmation).
- F10                      : Toggle In-game Multiplayer Portal.
- F5 (Host)                : World Sync (pauses all players, Host saves,
                             everyone reloads in sync).
- F6 (Client)              : Reload Synced Save.
- F8                       : Drop a Forensic Sync Trace Bookmark.
- F9                       : Show Speed Vote Status.
- Alt / Ctrl / Shift + MMB : Tactical Map Pings (Attack / Defend / Build,
                             visible to all players for 15 seconds).

============================================================
  IMPORTANT NOTES & DIAGNOSTICS
============================================================
- Every player starts with their OWN lord, retinue, and village in their
  chosen map region (native multi-lord campaign).
- ALL players must run the EXACT same ManorLordsCoop version (run
  1_INSTALL.bat / 1_INSTALL_LINUX.sh on every PC; CRC checks prevent
  version mismatches).
- Synchronized systems include:
  * Buildings, roads, wooden bridges, burgage plots, fields, upgrades,
    demolitions, priorities, workers, tax/trade/production settings.
  * Castle Planner, manor walls, towers, gates, wood/stone wall tiers,
    and platform levels.
  * Host-authoritative combat & armies: melee/ranged hits, HP, morale,
    stamina, routs, deaths, mercenaries, formations, stances, and skills.
  * Retinue customization, claims, challenges, King's Favour, royal tax,
    Victory/GameOver, caravans, diplomacy, policies, weather, raids,
    fires, and Visit Mode.
  * Adaptive game-day & speed synchronization (1x-6x), speed voting,
    stall barrier, and periodic World Sync.
- If you encounter a desync (Windows): press F8 in-game to drop a
  bookmark, then double-click "3_COLLECT_AND_ANALYZE_LOGS.bat" on both
  PCs to package your trace logs cleanly to your Desktop.
- Linux/Proton log paths:
  1. <Manor Lords>/ManorLords/Binaries/Win64/ue4ss/UE4SS.log
  2. <SteamLibrary>/steamapps/compatdata/1363080/pfx/drive_c/users/steamuser/AppData/Local/ManorLords/Saved/CoopIPC/daemon.log
============================================================

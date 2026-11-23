============================================================
  MANOR LORDS MULTIPLAYER (CO-OP & PVP - STEAM P2P)
  ZERO-SCRIPT DROP-IN INSTALLATION GUIDE (NEXUS EDITION)
============================================================

COPYRIGHT & LICENSE NOTICE:
  Copyright (c) 2026 Manor Lords Co-op Author. All Rights Reserved.
  This mod is licensed strictly for personal, non-commercial gameplay
  of Manor Lords via official releases (Nexus Mods / official GitHub
  Releases). Modification, redistribution, unofficial forks/updates,
  reverse engineering, and AI/LLM ingestion or code extraction are
  strictly prohibited without prior explicit written permission from
  the Copyright Holder. See LICENSE_ManorLordsCoop.txt for full terms.

SUPPORTED LANGUAGES (SELECTABLE IN MULTIPLAYER MENU):
  English | Türkçe | Русский | Deutsch | 简体中文 | Français | Polski

============================================================
  PREREQUISITES & CLEANUP (IMPORTANT!)
============================================================
- Steam must be running and logged in (NO port forwarding needed; all
  networking runs securely over Steamworks P2P).
- Tested on Manor Lords Steam build 0.8.117 (UE 5.5).
- IMPORTANT - IF YOU PREVIOUSLY INSTALLED AN OLDER UE4SS / MLUE4SS:
  Before installing, remove/disable legacy MLUE4SS v3.0.1 in Vortex and
  delete any old "xinput1_3.dll" or root "UE4SS.dll" inside:
    ...\steamapps\common\Manor Lords\ManorLords\Binaries\Win64\
  This package already includes the exact required RE-UE4SS v4.0.0
  (dwmapi.dll + ue4ss\UE4SS.dll) pre-configured for Manor Lords 0.8.117.

============================================================
  WINDOWS INSTALLATION (NO .BAT / NO INSTALLER NEEDED!)
============================================================
OPTION A - MANUAL DROP-IN (RECOMMENDED):
  1. Open your Manor Lords game folder in Steam:
     Steam -> Right-click Manor Lords -> Manage -> Browse local files
     (e.g. ...\steamapps\common\Manor Lords\)
  2. Extract the "ManorLords" folder from this ZIP directly into your
     "Manor Lords" game folder (merge/overwrite if prompted).
     Verify that "dwmapi.dll" sits next to "ManorLords-Win64-Shipping.exe"
     inside: ManorLords\Binaries\Win64\
  3. Launch Manor Lords normally via Steam -> Play!
     Click "Multiplayer" in the Main Menu (or press F10).

OPTION B - VORTEX / MOD MANAGER:
  1. Download with Mod Manager (Vortex) and enable the mod.
  2. Deploy mods (make sure no conflicting MLUE4SS v3 / xinput1_3.dll mod
     is active at the same time).
  3. Launch Manor Lords normally via Steam -> Play!

============================================================
  LINUX / STEAMOS (PROTON) INSTALLATION
============================================================
  1. Extract the "ManorLords" folder from this ZIP directly into your
     "Manor Lords" game folder (same as Windows Option A).
  2. In Steam -> Right-click Manor Lords -> Properties -> Launch Options:
       WINEDLLOVERRIDES="dwmapi=n,b" %command%
  3. Launch Manor Lords via Steam and click "Multiplayer" (or press F10).
     On Linux/Steam Deck, the Multiplayer Portal opens at:
       http://127.0.0.1:27065

============================================================
  HOW TO PLAY
============================================================
- HOST (Co-op / PvP / Free Diplomacy):
  1. Click "Multiplayer" in the Main Menu (or press F10) to open the
     integrated Multiplayer Portal.
  2. Use the top-right language dropdown to choose your language at any time.
  3. Follow "+ Create Lobby" -> Save Selection -> Lord & Coat of Arms
     -> Map Region Selection & Game Rules.
  4. Host as a Public or Password-Protected Private lobby.

- CLIENT (Joining & Live Drop-In Sync):
  1. Pick a room in the Lobby Browser or use Direct Join (Lobby Code /
     Host SteamID64).
  2. Customize your Lord & Coat of Arms, pick your starting region on the
     map, and click "Ready".
  3. Late-joining an active match is supported via "Join Active Game
     (Live Sync)".

============================================================
  IN-GAME HOTKEYS
============================================================
- Top-Left HUD             : Players, ping (ms), ally/enemy status, FPS.
- F3                       : Minimize / hide top-left HUD (Full -> Mini -> Hidden).
- F4                       : Host & Steward Panel (Speed Control Mode,
                             Cheats, Resource Multipliers, Players).
- F7                       : Diplomacy & Trade Caravans Panel.
- F10                      : Toggle Multiplayer Portal.
- F5 (Host)                : Manual World Sync snapshot to all peers.
- F6 (Client)              : Reload Synced Save.
- F8                       : Drop Forensic Sync Trace Bookmark.
- F9                       : Show Speed Vote Status.
- Alt / Ctrl / Shift + MMB : Tactical Map Pings (Attack / Defend / Build).

============================================================
  EXPORTING DIAGNOSTIC LOGS (BUG REPORTS)
============================================================
- No batch script needed! Open the Multiplayer Portal (F10) -> click
  "Settings" -> click "Export Sync Logs to Desktop".
- This creates a ready-to-share ZIP archive (ManorLords_SyncLog_*.zip)
  and summary report on your Desktop containing your sync trace,
  daemon.log, UE4SS.log, and latest UE5 CrashContext (if any).

============================================================
  UNINSTALLING
============================================================
- Delete the following from ...\Manor Lords\ManorLords\Binaries\Win64\:
    * dwmapi.dll
    * ue4ss\  (folder)
- (Or simply click Uninstall/Disable in Vortex.)

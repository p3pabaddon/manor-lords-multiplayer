# Manor Lords Multiplayer Mod

Multiplayer mod for **Manor Lords** supporting up to **6 players** over **Steam P2P** (Co-op vs AI, PvP, and Free-for-All) with no port forwarding or dedicated server required.

## Download

- **Direct Download (v1.0.0):** [ManorLords_Multiplayer_Mod.zip](https://github.com/p3pabaddon/manor-lords-multiplayer/raw/main/ManorLords_Multiplayer_Mod.zip) (`48.7 MB`)
- **Nexus Mods:** https://www.nexusmods.com/manorlords/mods/465 *(exact same archive — currently going through Nexus's standard automated EXE security review)*

**SHA-256 (`ManorLords_Multiplayer_Mod.zip`):**
```text
AC6ADA6C33186F4C7E2A37BBC3F3B504CFEA075AA39C3B91E23D02C1A0923038
```

---

## Features

- **Up to 6 players** in a single session — **Co-op vs AI**, **PvP**, or **Free-for-All** with team/alliance support
- **Steam P2P networking** — invite friends directly through Steam or join from the in-game lobby browser (no port forwarding needed)
- **Built-in lobby UI & F10 overlay** — configure map, teams, AI lords, and match settings before launching
- **Synced gameplay** — region claims, town building, castle planner, armies/combat, trade, diplomacy, and victory/defeat
- **Save & load** — save multiplayer sessions and continue later with the same lobby
- **Windows & Linux / Steam Deck (Proton)** cross-play support

---

## Requirements

- Steam version of **Manor Lords** (Steam must be running and logged in)
- All players in the session must be on the **same mod version**

---

## Installation

### Windows

1. Extract `ManorLords_Multiplayer_Mod.zip` into a clean ASCII path (for example: `C:\ManorLordsCoop`).
2. Double-click **`1_INSTALL.bat`** (first-time setup or after updates).
3. Double-click **`2_LAUNCH_GAME.bat`** to start the game (or launch Manor Lords from Steam and click **Multiplayer** in the Main Menu, or press **F10**).

### Linux / Steam Deck (Proton)

1. Extract `ManorLords_Multiplayer_Mod.zip` (for example: `~/ManorLordsCoop`).
2. Open a terminal inside the extracted folder and run:
   ```bash
   bash 1_INSTALL_LINUX.sh
   ```
   *(If Manor Lords is in a custom Steam library: `bash 1_INSTALL_LINUX.sh --game-dir "/path/to/Manor Lords/ManorLords/Binaries/Win64"`)*
3. In Steam → Right-click **Manor Lords** → **Properties → General → Launch Options**, paste the launch command printed by Step 2:
   ```text
   "/path/to/ManorLordsCoop/2_LAUNCH_GAME_LINUX.sh" %command%
   ```
4. Launch Manor Lords from Steam and click **Multiplayer** (or press **F10**). On Linux / Steam Deck, the lobby UI opens in your browser at `http://127.0.0.1:27065`.

---

## Notes & Bug Reports

This is the first public release. Early, mid, and late game have been tested on our own setups, and community feedback from different hardware and longer sessions will help us iron out any remaining edge cases or desyncs.

If you run into a desync or bug, run `3_COLLECT_AND_ANALYZE_LOGS.bat` (Windows) and share the generated sync log zip in our Discord or on the Nexus Mods page.

## License

All Rights Reserved — see [LICENSE](LICENSE) for full terms.

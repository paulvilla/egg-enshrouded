# Enshrouded 1.0 Dedicated Server Egg for Pelican Panel

[![Enshrouded](https://img.shields.io/badge/Game-Enshrouded%201.0-blue)](https://enshrouded.com)
[![Pelican](https://img.shields.io/badge/Panel-Pelican%2FPterodactyl-green)](https://pelican.dev)

> **Author:** Paul Villa ([paulvilla.dev@gmail.com](mailto:paulvilla.dev@gmail.com))  
> **Original base:** vapokrocks / gOOvER proton egg  
> **Game version:** 1.0+ (Back to the Shroud / full release)

---

## Features

- **Proton runtime** (Windows build via Proton) — better performance than Wine on Linux hosts.
- **Difficulty presets** selectable from the panel: *Default, Relaxed, Hard, Survival, Custom*.
- **Group passwords** configurable from the panel for *Admin*, *Member*, *Friend* and *Visitor*.
- **Default query port** pre-selected to **15637**.
- **Safe initial config generation**: the server always installs with the *Default* preset first; change difficulty later from the panel after the first successful boot.
- **Idempotent install**: if `enshrouded_server.json` already exists, the installer skips it so user edits are never reset.

---

## Requirements

- Pelican Panel (or Pterodactyl v1.x+)
- Node with the **SteamCMD** Proton image available (`ghcr.io/parkervcp/steamcmd:proton`)
- At least **1 UDP port** allocated to the server (default 15637)

---

## Quick Start

1. **Import the egg** into your Pelican panel.  
   `Nests → Import Egg → Select` **`egg-enshrouded-1.0.json`**
2. **Create a server** using the new Enshrouded egg.
3. **Leave the difficulty on Default** for the first install.
4. **Install** the server and wait for SteamCMD to finish.
5. Once the server is running successfully, **stop** it.
6. Open the server's startup page, **change the difficulty preset** (or group passwords) and **start** the server again.
7. Pelican will patch `enshrouded_server.json` automatically on boot.

> ⚠️ **Do NOT select Relaxed, Hard, Survival or Custom before the very first install.**  
> Always install with **Default** first, then switch presets from the panel afterwards.

---

## Panel Variables

| Variable | Default | Description |
|----------|---------|-------------|
| Server Name | `My Server` | Public server name shown in the browser. |
| Steam Query Port | `15637` | UDP port used by the server browser. |
| Admin password | *(empty)* | Password for the **Admin** user group. |
| Member password | *(empty)* | Password for the **Member** user group. |
| Friend password | *(empty)* | Password for the **Friend** user group. |
| Visitor password | *(empty)* | Password for the **Visitor** user group. |
| Max Players | `16` | Maximum simultaneous players (1-16). |
| Server Configuration | `Default` | Difficulty preset. Install with Default, change later. |
| Auto Update | `1` | Update server files on each container boot. |
| Validate | `0` | Run Steam validation on next boot (slower). |

---

## User Groups

The egg creates three built-in groups with fixed permissions:

| Group | Kick/Ban | Inventories | Edit World | Edit Base | Extend Base |
|-------|----------|-------------|------------|-----------|-------------|
| **Admin** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Member** | ❌ | ✅ | ✅ | ✅ | ✅ |
| **Friend** | ❌ | ❌ | ✅ | ❌ | ❌ |
| **Visitor** | ❌ | ❌ | ❌ | ❌ | ❌ |

Passwords are injected during installation and can be updated later from the panel (requires a server restart).

---

## File Structure

```
enshrouded_server.json   ← Main config (generated on install, patched on boot)
savegame/                ← World saves
logs/                    ← Server logs
steamcmd/                ← SteamCMD binaries
.steam/sdk32/            ← Steam 32-bit libs
.steam/sdk64/            ← Steam 64-bit libs
```

---

## Troubleshooting

**Server shows `Version Mismatch` / does not appear in the browser**  
→ Make sure your panel node has **UDP port 15637** (or the port you chose) forwarded and allocated to the server.

**Changed difficulty but the file still shows Default**  
→ Perform a full **Stop → Start** cycle. A quick reload may not trigger `config.files` patching.

**Server does not start after switching preset**  
→ Ensure you performed the **very first install** with the **Default** preset. If you selected another preset during installation, reinstall the server cleanly with Default first.

---

## License

This egg is provided as-is for the Enshrouded community.  
Original proton image credit to [gOOvER](https://goover.dev).

---

*Happy hosting!* 🎮

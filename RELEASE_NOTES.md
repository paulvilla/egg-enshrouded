# Enshrouded 1.0 Dedicated Server Egg

**Compatible with Pelican Panel & Pterodactyl v1.x**

---

## What's Included

- **Proton Runtime** — Uses the Windows server build via Proton for better performance than Wine on Linux hosts.
- **Difficulty Presets** — Selectable directly from the panel:
  - `Default`
  - `Relaxed`
  - `Hard`
  - `Survival`
  - `Custom`
- **Configurable Group Passwords** — Set passwords from the panel for:
  - **Admin** — Full permissions (kick/ban, build, manage).
  - **Member** — Trusted player. Can build, use inventories and extend bases. Cannot kick/ban.
  - **Friend** — Temporary player. Can explore and fight, but cannot open inventories, edit bases or extend bases.
  - **Visitor** — Observer only, no permissions.
- **Pre-configured Default Port** — Query port defaults to **15637**.
- **Safe First Install** — The server always installs with the **Default** preset first. Change difficulty **after** the initial installation from the panel variables.
- **Non-destructive** — If `enshrouded_server.json` already exists, the installer skips it so manual user edits are preserved.

---

## How to Use

1. **Import the egg** into your panel.  
   `Nests → Import Egg → Paste the raw URL of egg-enshrouded-1.0.json`
2. **Create a server** using the Enshrouded egg.
3. **Leave the difficulty on `Default`** for the first install.
4. Run the **Install** process and wait for SteamCMD to finish.
5. Once installed and running, **stop** the server.
6. Change the **Server Configuration** preset (or group passwords) in the panel variables.
7. **Start** the server again — Pelican will patch the config file automatically.

> ⚠️ **Important:** Do **not** select `Relaxed`, `Hard`, `Survival` or `Custom` before the very first install. Always install with **Default** first, then switch presets afterwards.

---

## Panel Variables

| Variable | Default | Description |
|----------|---------|-------------|
| Server Name | `My Server` | Public name shown in the server browser. |
| Steam Query Port | `15637` | UDP port for server browser queries. |
| Admin password | *(empty)* | Password for the **Admin** group. |
| Friend password | *(empty)* | Password for the **Friend** group. |
| Visitor password | *(empty)* | Password for the **Visitor** group. |
| Max Players | `16` | Max simultaneous players (1-16). |
| Server Configuration | `Default` | Difficulty preset. Install with Default, change later. |
| Auto Update | `1` | Update server files on each container boot. |
| Validate | `0` | Validate files through Steam on next boot (slower). |

---

## Credits

- **Author:** paulvilla ([paulvilla.dev@gmail.com](mailto:paulvilla.dev@gmail.com))
- **Base:** Original proton egg by vapokrocks / gOOvER
- **Game:** Enshrouded 1.0 by Keen Games

---

## License

Provided as-is for the Enshrouded hosting community.

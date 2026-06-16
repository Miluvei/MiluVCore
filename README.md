# MiluVCore

Lightweight Paper plugin core — staff mode, vanish, and an extension system for modular addons.

## Features

- **Staff Mode** — Hotbar tools: player teleport (compass + GUI), block teleport, freeze (with Resistance 10 + auto-ban on quit), gamemode toggle, vanish toggle, exit
- **Vanish** — Full vanish with tab completion filtering, join/quit message suppression, fake leave/join broadcasts on toggle, message blocking
- **Extension API** — Drop-in JAR extensions that hook into `/vcore` commands and events
- **Auto-Updater** — Checks GitHub releases on startup, downloads updates, applies on next restart

## Commands

| Command | Aliases | Permission | Description |
|---------|---------|------------|-------------|
| `/vcore` | | `miluvcore.staff` | Main command (help, version, reload) |
| `/vanish` | `/v` | `miluvcore.vanish` | Toggle vanish |
| `/staffmode` | `/staff`, `/sm` | `miluvcore.staffmode` | Toggle staff mode |

## Installation

1. Drop `MiluVCore-1.0.0.jar` into `plugins/`
2. Restart the server
3. Configure `plugins/MiluVCore/config.yml` to taste

## Extensions

Place additional JARs (e.g. `MiluVCore-Moderation.jar`) in `plugins/` — they auto-register with the core on startup.

## Building

```bash
cd MiluVCore
JAVA_HOME=/usr/lib/jvm/java-21-openjdk ./gradlew :jar
Output: build/libs/MiluVCore-1.0.0.jar
Permissions
Permission
miluvcore.*
miluvcore.staff
miluvcore.vanish
miluvcore.vanish.see
miluvcore.staffmode
miluvcore.reload
Configuration
See config.yml and messages.yml in plugins/MiluVCore/ after first run.

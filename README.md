# MiluVCore

A lightweight, modular staff core for Paper servers with optional advanced moderation analytics via the **Sentry extension**.

---

## Core Module - `MiluVCore.jar`

### Staff Mode
Powerful staff hotbar toolkit designed for fast moderation:
- Teleport wand (Diamond)
- Random teleport (Nether Star)
- Freeze tool (Breeze Rod)
- Gamemode toggle (Clock)
- Vanish toggle (Potion)
- Exit staff mode (Red Dye)

---

### Vanish System
Fully configurable stealth mode for staff:
- Fake join and leave messages
- Tab list hiding
- Message blocking (`/msg`, `/tell`, `/w`)
- Configurable broadcast formats

---

### Staff Chat
Private moderation channel:
- `/sc` toggle
- `@` chat prefix support
- PlaceholderAPI support (e.g. `%luckperms_prefix%`)

---

### Freeze System
Player restriction utility for moderation:
- Movement lock
- Resistance X effect while frozen
- Auto-punish on disconnect (configurable action or duration)

---

### Auto-Updater
Built-in GitHub release updater:
- Checks for new versions on startup
- Automatically downloads and replaces JAR files
- Safe shutdown sync for pending updates
- Keeps `/plugins` up to date

---

### Configuration System
Smart versioned config management:
- Auto-merges new config keys on updates
- Preserves existing user settings
- Prevents config resets on upgrades

---

### Commands

| Command | Aliases | Permission |
|--------|---------|------------|
| `/vcore` | - | `miluvcore.staff` |
| `/vanish` | `/v` | `miluvcore.vanish` |
| `/staffmode` | `/staff`, `/sm` | `miluvcore.staffmode` |
| `/staffchat` | `/sc` | `miluvcore.staffchat` |

---

## Extension - `MiluVCore-Sentry.jar`

Advanced moderation analytics and cheat investigation toolkit.

---

### SUS Investigation System
- `/sus` dashboard GUI
- Cheat confidence scoring (0-100%)
- Flag history tracking
- Severity indicators
- Filtering by time and source

---

### GrimAC Integration
- Real-time `FlagEvent` capture
- Configurable VL threshold (default 5)
- Thread-safe event handling

---

### Staff Tools
- `/sus note <player> <text>`
- `/sus flag <player> <source> <check> [vl]`
- `/report <player> <reason>`
- Reports GUI: `/vcore reports`

---

### Alerts and Automation
- Configurable alert thresholds
- Per-player cooldown system
- Discord webhook embeds
- Auto-punish commands with `{player}` placeholder
- Sound and chat notifications

---

### Staff Monitoring
- `/vcore logs` (staff activity logs)
- `/vcore info <player>`
  - Online status
  - World and gamemode
  - Flag history
  - Confidence score

---

### PlaceholderAPI
- `%sus_flags_<player>%`
- `%sus_lastflag_<player>%`

---

### Commands

| Command | Permission |
|--------|------------|
| `/sus` | `miluvcore.inspect` |
| `/report` | default |
| `/vcore info` | `miluvcore.staff` |
| `/vcore logs` | `miluvcore.staff` |
| `/vcore reports` | `miluvcore.staff` |

---

## Installation

1. Put `MiluVCore-1.5.0.jar` into `plugins/`
2. Optional: add `MiluVCore-Sentry-1.0.0.jar`
3. Restart server
4. Edit `plugins/MiluVCore/config.yml`

---

## Building from Source

```bash
JAVA_HOME=/usr/lib/jvm/java-21-openjdk ./gradlew :core:jar

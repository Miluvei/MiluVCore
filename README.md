# MiluVCore

Staff tools for Paper servers. Modular core with optional Sentry extension for advanced moderation analytics.

----

## Core (MiluVCore.jar)

### Staff Mode
Powerful staff hotbar toolkit:

- Teleport tool (Diamond)
- Block teleport (Nether Star)
- Freeze tool (Breeze Rod)
- Gamemode toggle (Clock)
- Vanish toggle (Potion)
- Exit staff mode (Red Dye)

### Vanish System
Fully configurable stealth mode:

- Fake join and leave broadcasts
- Tab list hiding
- Message blocking (/msg, /tell, /w)
- Configurable broadcast formats

### Staff Chat
Private moderation channel:

- /sc toggle
- @ chat prefix support
- PlaceholderAPI support (e.g. %luckperms_prefix%)

### Freeze System
Player restriction utility:

- Movement lock
- Resistance 10 effect while frozen
- Auto-ban on disconnect (configurable duration)

### Auto-Updater
Built-in GitHub release updater:

- Checks for new versions on startup
- Automatically downloads and replaces JAR files
- Safe shutdown sync for pending updates
- Keeps /plugins up to date

### Configuration System
Versioned config management:

- Auto-merges new config keys on updates
- Preserves existing user settings
- Prevents config resets on upgrades

### Commands

| Command | Aliases | Permission |
|---------|--------|------------|
| /vcore | - | miluvcore.staff |
| /vanish | /v | miluvcore.vanish |
| /staffmode | /staff, /sm | miluvcore.staffmode |
| /staffchat | /sc | miluvcore.staffchat |

----

## Extension: Sentry (MiluVCore-Sentry.jar)
Drop into plugins/ alongside the core. Enables cheat investigation, alerts, reports, and staff analytics.

### SUS Investigation System

//sus opens a paginated dashboard showing flagged players with:
- Cheat confidence scoring (0-100%)
- Flag history with severity colors (NED SUPPORT)
- Filtering by source GrimAC/manual/all) and time range (1h/6h/24h/all)
- Anvil-based search for player names

### GrimAC Integration

- Real-time flag capture via GrimAC FlagEvent
- Configurable MIN-VL threshold (default 5) to reduce false positives
- Thread-safe Netty handling

### Staff Tools

- /sus note <player> <text> - Add staff notes
- /sus flag <player> <source> <check> [vl] - Manual flag logging
- /report <player> <reason> - Player reports
- Reports GUI: /vcore reports

### Alerts and Automation

- Configurable flag thresholds
- Per-player alert cooldown
- Discord webhook embeds with severity colors
- Auto-punish command with {player}, {check}, {vl} placeholders
- Sound and chat notifications
- Alert toggle per staff member (/sus toggle)

### Staff Monitoring

- /vcore logs - Staff activity logs GUI
- /vcore info <player> - Online status, world, gamemode, flags, confidence score

### PlaceholderAPI

- %sus_flags_<player>%
- %sus_lastflag_<player>%

### Commands

| Command | Permission |
|---------|-------------|
| /sus | miluvcore.inspect |
| /report | default |
| /vcore info | miluvcore.staff |
| /vcore logs | miluvcore.staff |
| /vcore reports | miluvcore.staff |

----

## Installation

1. Put MiluVCore-1.5.0.jar into plugins/
2. Optional: add MiluVCore-Sentry-1.0.0.jar for SUS + reports
3. Restart server
4. Edit plugins/MiluVCore/config.yml to taste

```

## Building from Source

```bash
JAVA_HOME=/usr/lib/jmv/java-21-openjdk ./gradlew :jar
cat output: build/libs/MiluVCore-1.5.0.jar
```

To build Sentry: git clone and run `Java_HOME=../../gradlew :extension-sentry:jar`. The Sentry JAR will be in `extension-sentry/build/libs/`.

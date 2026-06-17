# MiluVCore

Staff tools for Paper servers. Lightweight core + optional Sentry extension.

- ---

## Core (MiluVCore.jar)

### Staff Mode
Hotbar with teleport (diamond), block teleport (nether star), freeze (breeze rod), gamemode toggle (clock), vanish toggle (potion), exit (red dye).

### Vanish
Fake join/leave broadcasts (configurable format). Tab completion hiding. Message blocking (/msg, /tell, /w).

### Staff Chat
/sc toggle, @ prefix in chat. PlaceholderAPI support (%luckperms_prefix%).

### Freeze
Resistance 10 effect. Movement lock. Auto-ban on disconnect (configurable duration).

### Auto-Updater
Checks GitHub releases on startup. Downloads new JAR, deletes old ones, saves to plugins/. Waits for pending downloads on shutdown.

### Config Auto-Merge
Version-based config updater. New keys added automatically without overwriting existing settings.

| Command | Aliases | Permission |
|---------|--------|------------|
| /vcore |  | miluvcore.staff |
| /vanish | /v | miluvcore.vanish |
| /staffmode | /staff, /sm | miluvcore.staffmode |
| /staffchat | /sc | miluvcore.staffchat |

- ---

## Extension: Sentry (MiluVCore-Sentry.jar)
Drop into plugins/ alongside the core to enable:

--- SUS Investigation - /sus dashboard with cheat confidence (0-100%), flag history, severity colors, source/time filters
--- GrimAC Integration - Auto-captures flags via FlagEvent. Configurable min-VL filter (default 5). Thread-safe Netty handler.
--- Staff Notes - /sus note <player> <text>, viewable in player GUI
--- Manual Flags - /sus flag <player> <source> <check> [vl]
--- Staff Alerts - Configurable flag thresholds, per-player cooldown, alert toggle (/sus toggle), sound notifications
--- Discord Webhooks - Embedded flag alerts with severity-colored embeds
--- Auto-Punish - Console command on threshold breach with {player} placeholder
--- Staff Reports - /report <player> <reason>, review via /vcore reports GUI
--- Staff Logs - /vcore logs GUI showing recent staff activity
--- Player Info - /vcore info <player> shows confidence, flags, online status, world, gamemode
--- PlaceholderAPI - %sus_flags_<player>%, %sus_lastflag_<player>%

| Command | Permission |
|---------|-------------|
| /sus | miluvcore.inspect |
| /report | (default: true) |
| /vcore info | miluvcore.staff |
| /vcore logs | miluvcore.staff |
| /vcore reports | miluvcore.staff |

- ---

## Installation

1. Drop MiluVCore-1.5.0.jar into plugins/
2. (Optional) Drop MiluVCore-Sentry-1.0.0.jar for SUS + reports
#. Restart server
4. Configure plugins/MiluVCore/config.yml to taste

## Building from source

```bash
JAVA_HOME=/usr/lib/jmv/java-21-openjdk ./gradlew :core:jar
CAtput: build/libs/MiluVCore-1.5.0.jar
```

To build Sentry: pyloned on the core, build separately and drop into plugins/.
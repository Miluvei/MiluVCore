# MiluVCore v1.5.2

Staff tools for Paper 1.21+ servers. Modular core with four extensions for moderation, anti-cheat, client analysis, and connection limiting.

## Core (MiluVCore.jar)

### Staff Mode
- Hotbar toolkit: teleport tool, freeze tool, vanish toggle, gamemode switch
- Stealth mode: join/quit message blocking, pickup prevention, XP/armor drop blocking
- `/staffmode` (aliases: `/staff`, `/sm`)

### Vanish
- Full invisibility with fake join/leave broadcasts
- Tab list and message blocking (`/msg`, `/tell`, `/w`)
- `/vanish` (`/v`)

### Staff Chat
- Private staff-only chat channel
- `/staffchat` (`/sc`)

### Freeze
- Movement lock with Resistance 10 effect
- Auto-ban on disconnect (configurable duration)
- `/freeze <player>`

### Auto-Updater
- Checks GitHub releases on startup
- Downloads and swaps updated JARs automatically

### Configuration
- Versioned config system with auto-merge on updates
- Preserves user settings across upgrades

### Commands
| Command | Permission |
|---------|-----------|
| `/vcore` | `miluvcore.staff` |
| `/vanish` | `miluvcore.vanish` |
| `/staffmode` | `miluvcore.staffmode` |
| `/staffchat` | `miluvcore.staffchat` |

---

## Extension: Sentry (MiluVCore-Sentry.jar)

Anti-cheat investigation and alerting system.

### SUS Dashboard
- `/sus` opens a paginated GUI of flagged players
- Confidence scores (0-100%) with severity coloring
- Source filters (Vulcan / manual) and time range (1h/6h/24h/all)
- Anvil search for player names

### Anticheat Bridges
- Vulcan `VulcanFlagEvent` integration -- real-time flag capture
- GrimAC support via reflection

### Staff Tools
- `/sus note <player> <text>` -- add investigation notes
- `/sus flag <player> <source> <check> [vl]` -- manual flag logging
- `/report <player> <reason>` -- player reports
- `/vcore reports` -- pending reports GUI
- `/vcore logs` -- staff activity audit
- `/vcore info <player>` -- detailed player overview

### Alerts
- Discord webhook embeds with severity colors
- Auto-punish with `{player}`, `{check}`, `{vl}` placeholders
- Per-player alert cooldown
- Sound + chat notifications
- `/sus toggle` -- three-mode alert toggle per staff member

### PlaceholderAPI
- `%sus_flags_<player>%`, `%sus_lastflag_<player>%`

### Commands
| Command | Permission |
|---------|-----------|
| `/sus` | `miluvcore.inspect` |
| `/report` | `default` |
| `/vcore info` | `miluvcore.staff` |
| `/vcore logs` | `miluvcore.staff` |
| `/vcore reports` | `miluvcore.staff` |

---

## Extension: Moderation (MiluVCore-Moderation.jar)

Full moderation toolkit with punishment tracking.

### Commands
| Command | Permission |
|---------|-----------|
| `/vcore punish <player> [type] <reason>` | `miluvcore.punish` |
| `/vcore ban <player> <reason>` | `miluvcore.ban` |
| `/vcore unban <player>` | `miluvcore.ban` |
| `/vcore mute <player> <reason>` | `miluvcore.mute` |
| `/vcore unmute <player>` | `miluvcore.mute` |
| `/vcore warn <player> <reason>` | `miluvcore.punish` |
| `/vcore freeze <player>` | `miluvcore.freeze` |
| `/vcore reasons` | `miluvcore.staff` |
| `/vcore inspect <player>` | `miluvcore.inspect` |

### Features
- Punishment types with configurable durations
- Auto-expiring tempbans and mutes
- Ban screen builder with custom messages
- Reason classifier with severity presets
- Player history tracking

---

## Extension: IPLimiter (MiluVCore-IPLimiter.jar)

Limits concurrent connections from the same IP address.

### Configuration
```yaml
max-connections-per-ip: 1
bypass-permission: "miluvcore.iplimiter.bypass"
```

### Features
- Atomic connection counting per IP
- Automatic cleanup on disconnect
- Configurable kick message with color codes

---

## Extension: AntiSpoof (MiluVCore-AntiSpoof.jar)

Client spoof detection via brand analysis and channel monitoring.

### Detection
- **Brand analysis**: 200+ brand regex patterns detecting hacked clients (Wurst, Meteor, Rise, Vape, Future, etc.) and legitimate launchers (Lunar, Badlion, Forge, Fabric)
- **Channel monitoring**: detects blocked or illegal mod channels (Xaero Minimap, Baritone, SeedCracker, etc.)
- **Vanilla spoof**: flags players claiming vanilla with registered channels
- **Mod list decoding**: extracts mod names from `vv:mod_details` and `tiscm` channels when available
- **Geyser spoof**: detects Bedrock clients faking Java client brands

### Mod Database
- 200+ classified mod entries: ILLEGAL, LEGAL, SUSPICIOUS, UNKNOWN
- Cheat client detection (KillAura, Reach, AutoClicker, Scaffold, Velocity, XRay, etc.)
- 50+ hacked client brand patterns
- Performance/QOL mods recognized as legal

### Alerts
- Discord webhook embeds with mod classification, threat scoring, and client type detection
- In-game staff alerts (`antispoof.alerts` permission)
- Configurable punishments per violation type
- VPN/proxy detection via ip-api.com (optional)

### Commands
| Command | Permission |
|---------|-----------|
| `/am channels <player>` | `antispoof.command` |
| `/am brand <player>` | `antispoof.command` |
| `/am check [player]` | `antispoof.command` |
| `/am runcheck [player]` | `antispoof.admin` |
| `/am blockedchannels` | `antispoof.admin` |
| `/am blockedbrands` | `antispoof.admin` |
| `/am reload` | `antispoof.admin` |
| `/vcore am` | `antispoof.command` |

### PlaceholderAPI
- `%antispoof_brand%`, `%antispoof_channels%`, `%antispoof_channels_count%`
- `%antispoof_is_spoofing%`, `%antispoof_is_bedrock%`


## Install

1. Drop `MiluVCore-1.6.0.jar` into `plugins/`
2. Add any extensions you want: `MiluVCore-Sentry-1.6.0.jar`, `MiluVCore-Moderation-1.6.0.jar`, `MiluVCore-IPLimiter-1.6.0.jar`, `MiluVCore-AntiSpoof-1.6.0.jar`
3. Restart server
4. Edit configs in `plugins/MiluVCore/` and each extension's data folder

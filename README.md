# BetterDiscordPatcher

![macOS](https://img.shields.io/badge/macOS-supported-0A84FF)
![Windows](https://img.shields.io/badge/Windows-preview-FF9F0A)
![Python](https://img.shields.io/badge/python-3.x-34C759)

Small patcher that installs the BetterDiscord loader into Discord's desktop
core.

This branch contains Windows support groundwork. macOS is the stable path;
Windows install and patch flows still need testing on a Windows machine.

## Install

macOS:

```sh
curl -fsSL https://raw.githubusercontent.com/ctrlcmdshft/BetterDiscordPatcher/main/install.sh | sh
```

Windows preview:

```powershell
irm https://raw.githubusercontent.com/ctrlcmdshft/BetterDiscordPatcher/windows/install.ps1 | iex
```

## Commands

```sh
betterdiscord
betterdiscord --dry-run
betterdiscord --edit-config
betterdiscord --format-config
betterdiscord --cleanup-old --dry-run
betterdiscord --unpatch
betterdiscord --update
betterdiscord --uninstall
```

## Config

Config paths:

```text
~/.config/betterdiscord-patcher/config.json
%APPDATA%\BetterDiscordPatcher\config.json
```

Command-line options override config values. Reformat an existing config with:

```sh
betterdiscord --format-config
```

Generated config:

```json
{
  "discord_data": "~/Library/Application Support/discord",
  "bd_asar": "~/Library/Application Support/BetterDiscord/data/betterdiscord.asar",
  "download": true,
  "wait_update": true,
  "cleanup_before_install": true,
  "keep_versions": 1,
  "keep_open": false,
  "reopen": true,
  "notify": false
}
```

The example above shows macOS paths. Windows uses `%LOCALAPPDATA%` for Discord
data and `%APPDATA%` for BetterDiscord/config paths.

| Key | Meaning |
| --- | --- |
| `discord_data` | Discord data folder to patch. |
| `bd_asar` | Destination for `betterdiscord.asar`. |
| `download` | Download or refresh `betterdiscord.asar`. |
| `wait_update` | Wait for Discord's updater to finish before patching. |
| `cleanup_before_install` | Remove old Discord `app-*` folders before patching. |
| `keep_versions` | Number of Discord `app-*` versions to keep when cleaning. |
| `keep_open` | Patch without quitting Discord first. |
| `reopen` | Reopen Discord only if it was running before patching. |
| `notify` | Show macOS notifications. |

## Cleanup

Cleanup only removes old `app-*` folders and keeps the newest app version folder.

```sh
betterdiscord --cleanup-old --dry-run
betterdiscord --cleanup-old
```

## Uninstall

```sh
betterdiscord --unpatch
betterdiscord --uninstall
```

`--unpatch` removes the BetterDiscord loader from Discord. `--uninstall` removes
the script command and asks before removing config.

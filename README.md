# BetterDiscordPatcher

Small macOS script that patches Discord to load BetterDiscord.

## Install

```sh
curl -fsSL https://raw.githubusercontent.com/ctrlcmdshft/BetterDiscordPatcher/main/install.sh | sh
```

The installer creates a config file and asks whether to open it. If the command
is not found after install, add `~/.local/bin` to your `PATH`.

## Use

```sh
betterdiscord
```

Other useful commands:

```sh
betterdiscord --edit-config
betterdiscord --dry-run
betterdiscord --update
betterdiscord --unpatch
betterdiscord --uninstall
betterdiscord --help
```

## Config

Config lives at:

```text
~/.config/betterdiscord-patcher/config.json
```

Command-line options override config values.

## Notes

The script finds Discord's current `discord_desktop_core`, writes the
BetterDiscord loader to `index.js`, and downloads `betterdiscord.asar` with
ETag caching.

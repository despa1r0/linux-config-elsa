# Configuration inventory

Inventory date: 2026-09-29.

No source configuration was changed, moved, removed, or replaced. `INCLUDE` means that a copy was placed in this repository. Sensitive paths were not read or copied.

| Application / area | Source | Status |
|---|---|---|
| Bash | `~/.bashrc` | INCLUDE |
| Bash | `~/.bash_logout` | INCLUDE |
| Bash | `~/.profile` | INCLUDE |
| tmux | `~/.tmux.conf` | INCLUDE |
| Ghostty | `~/.config/ghostty/` | INCLUDE |
| Fastfetch | `~/.config/fastfetch/` | INCLUDE |
| VS Code settings | `~/.config/Code/User/settings.json` | INCLUDE |
| VS Code snippets | `~/.config/Code/User/snippets/` | SKIP — directory is empty |
| VS Code keybindings | `~/.config/Code/User/keybindings.json` | SKIP — not present |
| GitHub CLI portable config | `~/.config/gh/config.yml` | INCLUDE |
| GitHub CLI authentication | `~/.config/gh/hosts.yml` | SKIPPED — potentially sensitive |
| Git global config | `~/.gitconfig` | SKIPPED — potentially sensitive; credential-helper keys were detected without reading their values |
| VS Code history and state | `~/.config/Code/User/{History,globalStorage,workspaceStorage}` | SKIPPED — potentially sensitive session/history data |
| Docker CLI | `~/.docker/` | SKIPPED — potentially sensitive auth data |
| SSH material | `~/.ssh/`, `~/ssh_key`, `~/ssh_key.pub` | SKIPPED — sensitive key material |
| GnuPG | `~/.gnupg/` | SKIPPED — sensitive key material |
| AWS CLI | `~/.aws/` | SKIPPED — potentially sensitive cloud credentials |
| Azure CLI | `~/.azure/` | SKIPPED — potentially sensitive cloud credentials |
| Password/keyring data | `~/.local/share/keyrings/` | SKIPPED — sensitive |
| Vagrant | `~/.vagrant.d/` | SKIPPED — potentially contains private keys and credentials |
| Terraform local/project state | `~/.terraform/`, `~/.terraform.d/`, `~/terraform.tfstate*` | SKIPPED — potentially sensitive state/credentials |
| Environment files | `~/truecsroi/.env`, `~/truecsroi/.env.example`, `~/.codex/.tmp/plugins/plugins/hugging-face/skills/community-evals/examples/.env.example` | SKIPPED — potentially sensitive; names were found but contents were not read |
| Shell history | `~/.bash_history` | SKIPPED — potentially sensitive history |
| npm state | `~/.npm/` | SKIPPED — cache and potentially sensitive auth state |
| AI/dev assistant state | `~/.codex/`, `~/.copilot/`, `~/.gemini/`, `~/.opencode/`, `~/.config/opencode/` | SKIPPED — potentially sensitive auth/conversation state |
| Browser and online-app state | `~/.config/net.imput.helium/`, `~/.config/discord/` | SKIPPED — potentially sensitive cookies/session data |
| Evolution | `~/.config/evolution/`, `~/.local/share/evolution/` | SKIPPED — potentially sensitive account/personal data |
| Obsidian application state | `~/.config/obsidian/` | SKIPPED — application/session state; vault contents are outside dotfiles scope |
| VirtualBox | `~/.config/VirtualBox/` | SKIPPED — machine-specific state and potentially sensitive VM metadata |
| VLC | `~/.config/vlc/` | SKIPPED — generated state may contain recent-media paths |
| PulseAudio | `~/.config/pulse/` | SKIPPED — machine-specific state/cookies |
| Local executables | `~/.local/bin/` | SKIPPED — installed binaries/symlinks, not portable configuration |
| XDG autostart | `~/.config/autostart/` | SKIP — directory is empty |
| Enchant dictionaries | `~/.config/enchant/` | SKIP — files are empty |
| act | `~/.config/act/` | SKIP — directory is empty |
| User desktop entries | `~/.local/share/applications/` | SKIP — directory is empty |
| GNOME/dconf/extensions/theme state | `~/.config/dconf/`, GNOME-related XDG paths | SKIP — explicitly excluded from this backup |
| Other desktop/application state | remaining `~/.config/` and `~/.local/share/` state directories | SKIP — generated, machine-specific, cache/session, or outside portable dotfiles scope |

## Package/application inventories

| Inventory | File | Result |
|---|---|---|
| APT manual packages | `packages/apt-manual.txt` | Collected with `apt-mark showmanual` |
| Snap packages | `packages/snap.txt` | `snap list` timed out; active names/revisions were recovered read-only from `/snap/*/current` |
| VS Code extensions | `packages/vscode-extensions.txt` | `code --list-extensions` failed because Snap confinement refused to start; IDs were recovered from extension directory names |
| Python user packages | `packages/pip-user.txt` | `python3 -m pip list --user --format=freeze` returned no packages |
| Flatpak | — | Not installed |
| Homebrew/Linuxbrew | — | Not installed |
| pipx | — | Not installed |
| Cargo | — | Not installed |
| npm/pnpm/yarn | — | Not installed |

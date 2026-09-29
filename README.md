# Ubuntu dotfiles backup

This repository is a conservative backup of portable user configuration. It was created by copying safe configuration files; the originals remain in place and continue to be used by the current system. No Stow activation was performed here.

See [`CONFIGS.md`](CONFIGS.md) for the full include/skip inventory and security decisions.

## Layout

Each top-level configuration package follows GNU Stow layout and is intended to target the home directory:

- `bash/` — `.bashrc`, `.bash_logout`, and `.profile`
- `tmux/` — `.tmux.conf`
- `ghostty/` — `.config/ghostty/`
- `fastfetch/` — `.config/fastfetch/`
- `vscode/` — selected files under `.config/Code/User/`
- `gh/` — portable GitHub CLI config only; authentication is excluded
- `packages/` — package and extension inventories

## Prepare a new Ubuntu system

Install Git and GNU Stow through Ubuntu's package manager when you are ready to change the new system:

```bash
sudo apt update
sudo apt install git stow
```

Clone the repository (replace the placeholder with the confirmed repository URL):

```bash
git clone <repository-url> "$HOME/dotfiles"
cd "$HOME/dotfiles"
```

## Activate configurations manually

Always inspect the package and perform a dry run first. For example:

```bash
cd "$HOME/dotfiles"
stow --simulate --verbose --target="$HOME" bash
```

If Stow reports a conflict, stop. Review and compare the existing destination manually. Do not let an automated command remove or overwrite an existing configuration. Activate a package only after you have deliberately resolved every conflict and have a separate backup of anything important:

```bash
stow --verbose --target="$HOME" bash
```

Repeat the dry-run and activation separately for `tmux`, `ghostty`, `fastfetch`, `vscode`, or `gh`. Do not activate every package blindly.

## Restore VS Code extensions

Review the extension list first:

```bash
less packages/vscode-extensions.txt
```

Then, on a working VS Code installation, install reviewed entries one at a time:

```bash
xargs -r -n1 code --install-extension < packages/vscode-extensions.txt
```

The original inventory command could not start in the source system because Snap confinement refused to run VS Code. The saved list was reconstructed from installed extension directory names.

## Review package inventories

```bash
less packages/apt-manual.txt
less packages/snap.txt
less packages/pip-user.txt
```

`apt-manual.txt` records manually marked APT packages. `snap.txt` is a read-only fallback inventory of active Snap names and revisions because `snap list` timed out. An empty `pip-user.txt` means no user-site pip packages were reported. These files are inventories, not automatic installation scripts.

## Security

Authentication files, credentials, keys, histories, session databases, cloud configuration, Docker auth, GitHub CLI hosts, `.env` files, and infrastructure state are intentionally excluded. The `.gitignore` provides an additional guard, but it is not a substitute for reviewing `git diff --cached --name-only` before every commit and using a secret scanner where available.

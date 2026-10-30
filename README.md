# Dotfiles

Managed with [GNU Stow](https://www.gnu.org/software/stow/). Each top-level directory is a stow package. `--no-folding` is set in `.stowrc` so stow creates individual file symlinks (not directory symlinks), preventing credential leaks.

## Install

```sh
git clone <repo-url> ~/dotfiles
cd ~/dotfiles && stow nvim git zed yazi rex
```

## Structure

Each package mirrors its `~/.config/<app>/` layout:

```
<package>/<app>/files  ->  ~/.config/<app>/files
```

| Package | Contents |
| ------- | -------- |
| `nvim`  | Neovim config (kickstart-based), plugins in `lua/custom/plugins/` |
| `git`   | Global git ignore patterns |
| `zed`   | Zed editor preferences |
| `yazi`  | Yazi file manager config |
| `rex`   | Rex terminal config |

## Dependencies

### System

| Tool | Install |
| ---- | ------- |
| [GNU Stow](https://www.gnu.org/software/stow/) | `brew install stow` |
| [Neovim](https://neovim.io/) >= 0.12 | `brew install neovim` |
| [tree-sitter CLI](https://tree-sitter.github.io/) | `brew install tree-sitter-cli` |

### Rust

| Tool | Install |
| ---- | ------- |
| [rustup](https://rustup.rs/) | `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs \| sh` |
| rust-analyzer | `rustup component add rust-analyzer` |

Add `rust-analyzer` to every toolchain you use (stable, nightly, etc.).

### Auto-installed by Mason

lua_ls, stylua (>= 2.2.0), codelldb, delve, markdownlint

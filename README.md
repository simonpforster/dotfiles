# Dotfiles Configuration Management

This repository contains configuration files for various tools and applications, managed via [GNU Stow](https://www.gnu.org/software/stow/) to create symlinks in `~/.config/`.

## Install

```sh
cd ~/dotfiles && stow --target ~/.config .
```

## Dependencies

### System (Homebrew)

| Tool | Install | Used by |
|------|---------|---------|
| [Neovim](https://neovim.io/) ≥ 0.12 | `brew install neovim` | nvim config |
| [GNU Stow](https://www.gnu.org/software/stow/) | `brew install stow` | symlink management |
| [tree-sitter CLI](https://tree-sitter.github.io/) | `brew install tree-sitter-cli` | nvim treesitter parser compilation |
| [git](https://git-scm.com/) | usually pre-installed on macOS/Linux | git config |

### Rust (rustup)

| Tool | Install | Used by |
|------|---------|---------|
| [rustup](https://rustup.rs/) | `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs \| sh` | Rust toolchain management |
| rust-analyzer | `rustup component add rust-analyzer` | nvim LSP (via rustaceanvim) |

> **Note:** Add `rust-analyzer` to every toolchain you use (stable, nightly, etc.). Zed is a Rust application and requires rustup.

## Repository Structure

```
dotfiles/
├── README.md              # This file - project documentation
├── .gitignore            # Local ignore patterns for git
├── git/                  # Git ignore patterns for local repos
│   └── ignore            # Patterns to exclude from git tracking
├── nvim/                 # Neovim Lua configuration
│   ├── nvim/             # Main neovim config directory
│   │   ├── init.lua      # Primary configuration file
│   │   └── lua/custom/plugins/*.lua  # Custom plugin definitions
├── zed/                  # Zed editor settings (Rust-based IDE)
│   ├── settings.json     # Editor preferences and layout
│   └── settings_backup.json  # Previous settings backup  
└── yazi/                 # File manager configuration
    └── yazi.toml         # File manager configuration with nvim integration

## Best Practices

### Security

This repository follows security best practices:

- ✅ **No secrets**: No passwords, API keys, or tokens are committed to public repos
- ⚠️ **Local-only configs**: Some configurations in `~/.config/` may contain private data not tracked here (e.g., GitHub CLI auth)

### Shell Configurations

Shell configurations follow best practices:

- **Zsh**: Primary interactive shell with [Powerlevel10k](https://github.com/romkatv/powerlevel10k) prompt theme
- Each shell has its own configuration under `~/.config/{zsh,bash}/` after stow

### Git Workflow

This repository uses GNU Stow for symlink management:

1. **Clone**: `git clone <repo-url> ~/dotfiles`
2. **Install**: `cd ~/dotfiles && stow --target ~/.config .`
3. **Update**: Edit files in the repo, then `stow` again
4. **Rollback**: Use git to restore previous commit if needed

### Project-Specific Configs

Project-specific configurations (like `.claude/settings.local.json`) are excluded from the repository via `.gitignore`. These should be managed locally or through project-specific configuration management.

## Maintenance

- Keep this repository clean by removing unused directories
- Regularly update dependencies in the README.md table
- Document any changes to help future maintainers understand your setup

---

*Last updated: 2026-10-30*

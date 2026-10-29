# My dotfiles

## Install

```sh
stow --target ~/.config .
```

## Dependencies

### System

| Tool | Install | Used by |
|------|---------|---------|
| [Neovim](https://neovim.io/) ≥ 0.12 | `brew install neovim` | nvim config |
| [GNU Stow](https://www.gnu.org/software/stow/) | `brew install stow` | symlink management |
| [tree-sitter CLI](https://tree-sitter.github.io/) | `brew install tree-sitter-cli` | nvim treesitter parser compilation |

### Rust

| Tool | Install | Used by |
|------|---------|---------|
| [rustup](https://rustup.rs/) | `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs \| sh` | Rust toolchain management |
| rust-analyzer | `rustup component add rust-analyzer` | nvim LSP (via rustaceanvim) |

> **Note:** Add `rust-analyzer` to every toolchain you use (stable, nightly, etc.).

### Scala

| Tool | Install | Used by |
|------|---------|---------|
| [Metals](https://scalameta.org/metals/) | auto-managed by nvim-metals | nvim LSP for Scala |
| [Coursier](https://get-coursier.io/) | `brew install coursier` | Metals installation |

### Managed by Mason (auto-installed)

These are installed automatically by Mason on first launch:

- **lua_ls** — Lua LSP
- **stylua** — Lua formatter (requires ≥ 2.2.0 for LSP mode)
- **codelldb** — debug adapter
- **delve** — Go debugger
- **markdownlint** — Markdown linter


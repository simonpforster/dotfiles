# Security Guidelines for Public Dotfiles Repository

## ⚠️ This is a PUBLIC repository

This dotfiles repository will be shared publicly on GitHub. **Extra care must be taken** to ensure only non-confidential configurations are committed. When in doubt, do not commit the file.

---

## 🔒 Golden Rules

1. **Never commit secrets**: Passwords, API keys, tokens, or credentials
2. **Remove PII**: Personal identifiable information (email addresses, phone numbers)
3. **Sanitize company data**: Internal URLs, project paths, proprietary configurations
4. **No private keys**: SSH, GPG, or any cryptographic keys
5. **When in doubt → Leave it out**

---

## ✅ Safe to Commit (Public-Safe)

| Configuration Type | Examples | Why It's Safe |
|-------------------|----------|---------------|
| Shell configs | `.zshrc`, `.bashrc` | Generic shell settings, no secrets |
| Editor configs | Neovim Lua, Vimrc | UI preferences, LSP settings only |
| CLI configs (non-auth) | `gitconfig` without credentials | Protocol, aliases only |
| Terminal configs | Alacritty, Wezterm | Display preferences, key bindings |
| Git ignore patterns | Local repo exclusions | Safety rules for version control |

---

## ❌ Never Commit (Private/Confidential)

| File Type | Examples | Risk |
|-----------|----------|------|
| **Credentials** | OAuth tokens, PATs, service accounts | Account compromise within minutes of push |
| **API Keys** | `.env`, AWS credentials, service accounts | Cloud billing abuse, supply-chain attacks |
| **Private keys** | SSH private keys (`id_rsa`), GPG keys | Supply-chain attacks, impersonation |
| **PII** | Email addresses, phone numbers, full names | Privacy violation, doxxing risk |
| **Company data** | Internal URLs, project paths, proprietary configs | Employment disclosure, competitive intelligence leak |
| **Session data** | `.claude/settings.local.json`, browser cookies | Account takeover potential |

---

## 🔍 Security Checklist Before Committing

Before committing any file to this public repository:

- [ ] Does it contain passwords, tokens, or API keys? → **DO NOT COMMIT**
- [ ] Is there a username/email/phone number in the config? → **REVIEW AND REMOVE**
- [ ] Are there internal URLs (company-specific)? → ** REPLACE WITH GENERIC OR REMOVE**
- [ ] Does it contain company-hosted services or proprietary configs? → **DO NOT COMMIT**
- [ ] Is this session data or cache that changes frequently? → **IGNORE VIA .gitignore**

---

## 📁 Current Repository Contents (Verified Safe)

| File | Status | Reason |
|------|--------|--------|
| `git/ignore` | ✅ SAFE | Local repo exclusions pattern |
| `nvim/*` | ✅ SAFE | Neovim Lua configuration, no credentials |
| `zed/settings.json` | ✅ SAFE | Editor preferences only |
| `yazi/yazi.toml` | ✅ SAFE | File manager UI settings |

---

## 🛡️ Defense Layers (If Public Repo Created)

### Layer 1: Pre-commit Hooks
Use tools like `git-secrets` or `pre-commit` to scan for secrets before commit.

### Layer 2: File Permissions
Set sensitive files to mode `0600` if any must be committed:
```bash
chmod 0600 ~/.config/gh/hosts.yml
```

### Layer 3: Manual Review
Always manually review new files before committing, especially:
- New configuration files for tools you haven't used before
- Files from third-party applications with unknown security posture
- Files containing paths or URLs not in your personal workflow

---

## 📚 References & Best Practices

- [Secret Management Best Practices | Dotfiles](https://dotfiles.io/en/guides/secret-management/)
- [Three layers of secret defense for a public dotfiles repo](https://nick-liu.com/posts/public-dotfiles-secret-defense/)

---

## 🔄 Update Policy

When adding new files to this repository:

1. **Ask yourself**: "Would I be comfortable sharing this file publicly?"
2. If answer is NO → Do not commit, keep locally
3. If answer is YES but unsure → Remove sensitive information first
4. When in doubt → Leave it out

---

*Last reviewed: 2026-10-30*

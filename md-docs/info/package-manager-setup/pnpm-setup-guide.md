# pnpm Setup Guide

Complete guide to install and configure pnpm globally on all major operating systems.

## What is pnpm?

[pnpm](https://pnpm.io/) is a fast, disk space efficient package manager. It uses a content-addressable store to save disk space by linking packages instead of copying them.

### Key Benefits

- ⚡ **Fast** - Up to 2x faster than npm
- 💾 **Disk efficient** - Saves significant disk space
- 🔒 **Strict** - Creates a non-flat node_modules by default
- 📦 **Monorepo support** - Built-in workspace support

---

## macOS

<details>
<summary><strong>Using Homebrew (Recommended)</strong></summary>

```bash
brew install pnpm

# Verify installation
pnpm --version
```

</details>

<details>
<summary><strong>Using npm</strong></summary>

```bash
npm install -g pnpm

# Verify installation
pnpm --version
```

</details>

<details>
<summary><strong>Using curl</strong></summary>

```bash
curl -fsSL https://get.pnpm.io/install.sh | sh -

# Restart terminal or run
source ~/.zshrc

# Verify installation
pnpm --version
```

</details>

<details>
<summary><strong>Using Corepack (Node.js 16.13+)</strong></summary>

```bash
corepack enable
corepack prepare pnpm@latest --activate

# Verify installation
pnpm --version
```

</details>

---

## Windows

<details>
<summary><strong>Using npm (Recommended)</strong></summary>

```powershell
npm install -g pnpm

# Verify installation
pnpm --version
```

</details>

<details>
<summary><strong>Using PowerShell</strong></summary>

```powershell
iwr https://get.pnpm.io/install.ps1 -useb | iex

# Restart terminal
# Verify installation
pnpm --version
```

</details>

<details>
<summary><strong>Using Chocolatey</strong></summary>

```powershell
choco install pnpm

# Verify installation
pnpm --version
```

</details>

<details>
<summary><strong>Using Scoop</strong></summary>

```powershell
scoop install nodejs-lts pnpm

# Verify installation
pnpm --version
```

</details>

<details>
<summary><strong>Using Corepack</strong></summary>

```powershell
corepack enable
corepack prepare pnpm@latest --activate

# Verify installation
pnpm --version
```

</details>

---

## Linux

<details>
<summary><strong>Using curl (All Distros - Recommended)</strong></summary>

```bash
curl -fsSL https://get.pnpm.io/install.sh | sh -

# Restart terminal or run
source ~/.bashrc

# Verify installation
pnpm --version
```

</details>

<details>
<summary><strong>Using npm</strong></summary>

```bash
npm install -g pnpm

# Verify installation
pnpm --version
```

</details>

<details>
<summary><strong>Ubuntu/Debian via apt</strong></summary>

```bash
# Add pnpm repository
curl -fsSL https://get.pnpm.io/install.sh | sh -

# Verify installation
pnpm --version
```

</details>

<details>
<summary><strong>Arch Linux</strong></summary>

```bash
# Using AUR
yay -S pnpm

# Or using npm
npm install -g pnpm

# Verify installation
pnpm --version
```

</details>

<details>
<summary><strong>Using Corepack (All Distros)</strong></summary>

```bash
corepack enable
corepack prepare pnpm@latest --activate

# Verify installation
pnpm --version
```

</details>

---

## Configuration

### Set Store Directory

```bash
pnpm config set store-dir ~/.pnpm-store
```

### View Configuration

```bash
pnpm config list
```

### Enable Strict Peer Dependencies

```bash
pnpm config set strict-peer-dependencies true
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `pnpm install` | Install all dependencies |
| `pnpm add <package>` | Add a package |
| `pnpm add -D <package>` | Add a dev dependency |
| `pnpm remove <package>` | Remove a package |
| `pnpm update` | Update all packages |
| `pnpm run <script>` | Run a script |
| `pnpm test` | Run tests |

### Command Aliases

pnpm is also compatible with npm commands:

```bash
pnpm i        # Same as pnpm install
pnpm dev      # Same as pnpm run dev
```

---

## Migrating from npm/Yarn

```bash
# Remove existing node_modules and lock files
rm -rf node_modules package-lock.json yarn.lock

# Install with pnpm
pnpm install
```

---

## Troubleshooting

### Permission Denied

```bash
# Set custom global directory
pnpm config set global-dir ~/.pnpm-global
pnpm config set global-bin-dir ~/.pnpm-global/bin
export PATH=~/.pnpm-global/bin:$PATH
```

### Store Corruption

```bash
# Verify store integrity
pnpm store status

# Prune unused packages
pnpm store prune
```

### Slow First Install

The first install may be slower as pnpm builds its store. Subsequent installs will be much faster.

---

## Related Documentation

- [Official pnpm Documentation](https://pnpm.io/)
- [Main README](../../README.md)
- [Info Directory](./README.md)

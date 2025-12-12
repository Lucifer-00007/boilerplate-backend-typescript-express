# Bun Setup Guide

Complete guide to install and configure Bun globally on all major operating systems.

## What is Bun?

[Bun](https://bun.sh/) is a fast all-in-one JavaScript runtime and toolkit. It includes a package manager, bundler, and test runner, designed for speed.

### Key Benefits

- 🚀 **Blazing fast** - Up to 25x faster than npm
- 📦 **All-in-one** - Runtime, bundler, package manager, and test runner
- 🔄 **Drop-in replacement** - Compatible with npm and Node.js
- ⚡ **Native TypeScript** - No configuration needed

---

## macOS

<details>
<summary><strong>Using curl (Recommended)</strong></summary>

```bash
curl -fsSL https://bun.sh/install | bash

# Restart terminal or run
source ~/.zshrc

# Verify installation
bun --version
```

</details>

<details>
<summary><strong>Using Homebrew</strong></summary>

```bash
brew tap oven-sh/bun
brew install bun

# Verify installation
bun --version
```

</details>

<details>
<summary><strong>Using npm</strong></summary>

```bash
npm install -g bun

# Verify installation
bun --version
```

</details>

---

## Windows

> **Note**: Bun on Windows is currently in beta. For full stability, consider using WSL2.

<details>
<summary><strong>Using PowerShell (Recommended)</strong></summary>

```powershell
powershell -c "irm bun.sh/install.ps1 | iex"

# Restart terminal
# Verify installation
bun --version
```

</details>

<details>
<summary><strong>Using npm</strong></summary>

```powershell
npm install -g bun

# Verify installation
bun --version
```

</details>

<details>
<summary><strong>Using Scoop</strong></summary>

```powershell
scoop install bun

# Verify installation
bun --version
```

</details>

<details>
<summary><strong>Using WSL2 (Recommended for Stability)</strong></summary>

For the best experience on Windows, use WSL2:

```powershell
# Install WSL2 with Ubuntu (run as Administrator)
wsl --install -d Ubuntu
```

Then in Ubuntu:

```bash
curl -fsSL https://bun.sh/install | bash
source ~/.bashrc
bun --version
```

</details>

---

## Linux

<details>
<summary><strong>Using curl (All Distros - Recommended)</strong></summary>

```bash
curl -fsSL https://bun.sh/install | bash

# Restart terminal or run
source ~/.bashrc

# Verify installation
bun --version
```

</details>

<details>
<summary><strong>Using npm</strong></summary>

```bash
npm install -g bun

# Verify installation
bun --version
```

</details>

<details>
<summary><strong>Arch Linux</strong></summary>

```bash
# Using AUR
yay -S bun-bin

# Verify installation
bun --version
```

</details>

<details>
<summary><strong>Using Docker</strong></summary>

```bash
docker run --rm --init --ulimit memlock=-1:-1 oven/bun bun --version
```

</details>

---

## Update Bun

```bash
bun upgrade
```

---

## Configuration

Bun uses `bunfig.toml` for configuration:

```toml
# bunfig.toml
[install]
# Registry URL
registry = "https://registry.npmjs.org"

# Cache directory
cache = "~/.bun/install/cache"

[run]
# Automatically install missing dependencies
auto-install = true
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `bun install` | Install all dependencies |
| `bun add <package>` | Add a package |
| `bun add -d <package>` | Add a dev dependency |
| `bun remove <package>` | Remove a package |
| `bun update` | Update all packages |
| `bun run <script>` | Run a script |
| `bun test` | Run tests |
| `bun build` | Bundle your project |

### Running Scripts

```bash
# These are equivalent
bun run dev
bun dev
```

---

## Using with This Project

```bash
# Install dependencies
bun install

# Run development server
bun run dev

# Run tests
bun run test

# Build for production
bun run build
```

---

## Troubleshooting

### Installation Failed

```bash
# Uninstall and reinstall
rm -rf ~/.bun
curl -fsSL https://bun.sh/install | bash
```

### Command Not Found

Add Bun to your PATH:

```bash
# Add to ~/.bashrc or ~/.zshrc
export BUN_INSTALL="$HOME/.bun"
export PATH="$BUN_INSTALL/bin:$PATH"

# Reload shell
source ~/.bashrc
```

### Compatibility Issues

Bun is highly compatible with Node.js, but some edge cases may exist:

```bash
# Fall back to Node.js for specific scripts
node script.js
# Instead of
bun script.js
```

### Windows-Specific Issues

If you encounter issues on Windows:

1. Ensure you're using the latest Windows 10/11
2. Try running PowerShell as Administrator
3. Consider using WSL2 for better compatibility

---

## Comparison with Other Package Managers

| Feature | Bun | npm | Yarn | pnpm |
|---------|-----|-----|------|------|
| Install Speed | ⚡⚡⚡ | ⚡ | ⚡⚡ | ⚡⚡ |
| Disk Space | Good | High | High | Best |
| Built-in Bundler | ✅ | ❌ | ❌ | ❌ |
| Built-in Test Runner | ✅ | ❌ | ❌ | ❌ |
| Native TypeScript | ✅ | ❌ | ❌ | ❌ |

---

## Related Documentation

- [Official Bun Documentation](https://bun.sh/docs)
- [Main README](../../README.md)
- [Info Directory](./README.md)

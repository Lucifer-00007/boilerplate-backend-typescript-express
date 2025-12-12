# Yarn Setup Guide

Complete guide to install and configure Yarn globally on all major operating systems.

## What is Yarn?

[Yarn](https://yarnpkg.com/) is a fast, reliable, and secure dependency management tool for JavaScript projects. It's the **default and recommended** package manager for this project.

---

## macOS

<details>
<summary><strong>Using Homebrew (Recommended)</strong></summary>

```bash
# Install Homebrew if not installed
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Yarn
brew install yarn

# Verify installation
yarn --version
```

</details>

<details>
<summary><strong>Using npm</strong></summary>

```bash
npm install -g yarn

# Verify installation
yarn --version
```

</details>

<details>
<summary><strong>Using Corepack (Node.js 16.10+)</strong></summary>

```bash
# Enable Corepack
corepack enable

# Install latest Yarn
corepack prepare yarn@stable --activate

# Verify installation
yarn --version
```

</details>

---

## Windows

<details>
<summary><strong>Using npm (Recommended)</strong></summary>

```powershell
npm install -g yarn

# Verify installation
yarn --version
```

</details>

<details>
<summary><strong>Using Chocolatey</strong></summary>

```powershell
# Run PowerShell as Administrator
choco install yarn

# Verify installation
yarn --version
```

</details>

<details>
<summary><strong>Using Scoop</strong></summary>

```powershell
scoop install yarn

# Verify installation
yarn --version
```

</details>

<details>
<summary><strong>Using Official Installer</strong></summary>

1. Download the installer from [yarnpkg.com/getting-started/install](https://yarnpkg.com/getting-started/install)
2. Run the `.msi` installer
3. Restart your terminal
4. Verify: `yarn --version`

</details>

---

## Linux

<details>
<summary><strong>Ubuntu/Debian</strong></summary>

```bash
# Using npm (Recommended)
npm install -g yarn

# Or using apt repository
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt update && sudo apt install yarn

# Verify installation
yarn --version
```

</details>

<details>
<summary><strong>Fedora/RHEL/CentOS</strong></summary>

```bash
# Using npm
npm install -g yarn

# Or using dnf
sudo dnf install yarn

# Verify installation
yarn --version
```

</details>

<details>
<summary><strong>Arch Linux</strong></summary>

```bash
# Using pacman
sudo pacman -S yarn

# Verify installation
yarn --version
```

</details>

<details>
<summary><strong>Using Corepack (All Distros)</strong></summary>

```bash
# Enable Corepack (requires Node.js 16.10+)
corepack enable

# Install latest Yarn
corepack prepare yarn@stable --activate

# Verify installation
yarn --version
```

</details>

---

## Configuration

### Set Global Cache Directory

```bash
yarn config set cache-folder ~/.yarn-cache
```

### Check Current Configuration

```bash
yarn config list
```

### Set Registry (Optional)

```bash
# Use npm registry
yarn config set registry https://registry.npmjs.org
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `yarn install` | Install all dependencies |
| `yarn add <package>` | Add a package |
| `yarn add -D <package>` | Add a dev dependency |
| `yarn remove <package>` | Remove a package |
| `yarn upgrade` | Upgrade all packages |
| `yarn run <script>` | Run a script from package.json |

---

## Troubleshooting

### Permission Denied (Linux/macOS)

```bash
# Fix npm global permissions
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc

# Then reinstall yarn
npm install -g yarn
```

### Command Not Found

Ensure Yarn is in your PATH:

```bash
# Check where yarn is installed
which yarn

# Add to PATH if needed (add to ~/.bashrc or ~/.zshrc)
export PATH="$PATH:$(yarn global bin)"
```

---

## Related Documentation

- [Official Yarn Documentation](https://yarnpkg.com/getting-started)
- [Main README](../../README.md)
- [Info Directory](./README.md)

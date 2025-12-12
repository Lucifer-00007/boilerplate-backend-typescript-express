# npm Setup Guide

Complete guide to install and configure npm globally on all major operating systems.

## What is npm?

[npm](https://www.npmjs.com/) (Node Package Manager) is the default package manager for Node.js. It comes **bundled with Node.js**, so installing Node.js automatically installs npm.

---

## macOS

<details>
<summary><strong>Using Homebrew (Recommended)</strong></summary>

```bash
# Install Homebrew if not installed
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Node.js (includes npm)
brew install node

# Verify installation
node --version
npm --version
```

</details>

<details>
<summary><strong>Using nvm (Recommended for Version Management)</strong></summary>

```bash
# Install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash

# Restart terminal or run
source ~/.zshrc

# Install latest LTS Node.js (includes npm)
nvm install --lts

# Verify installation
npm --version
```

</details>

<details>
<summary><strong>Using Official Installer</strong></summary>

1. Download from [nodejs.org](https://nodejs.org/)
2. Run the `.pkg` installer
3. Follow the installation wizard
4. Verify: `npm --version`

</details>

---

## Windows

<details>
<summary><strong>Using Official Installer (Recommended)</strong></summary>

1. Download the LTS version from [nodejs.org](https://nodejs.org/)
2. Run the `.msi` installer
3. Ensure "Add to PATH" is checked
4. Restart your terminal

```powershell
# Verify installation
node --version
npm --version
```

</details>

<details>
<summary><strong>Using Chocolatey</strong></summary>

```powershell
# Run PowerShell as Administrator
choco install nodejs-lts

# Verify installation
npm --version
```

</details>

<details>
<summary><strong>Using nvm-windows</strong></summary>

1. Download from [github.com/coreybutler/nvm-windows](https://github.com/coreybutler/nvm-windows/releases)
2. Run the installer
3. Open a new terminal

```powershell
# Install latest LTS
nvm install lts
nvm use lts

# Verify
npm --version
```

</details>

<details>
<summary><strong>Using Scoop</strong></summary>

```powershell
scoop install nodejs-lts

# Verify installation
npm --version
```

</details>

---

## Linux

<details>
<summary><strong>Ubuntu/Debian</strong></summary>

```bash
# Using NodeSource (Recommended)
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs

# Verify installation
npm --version
```

</details>

<details>
<summary><strong>Fedora/RHEL/CentOS</strong></summary>

```bash
# Fedora
sudo dnf install nodejs npm

# Verify installation
npm --version
```

</details>

<details>
<summary><strong>Arch Linux</strong></summary>

```bash
sudo pacman -S nodejs npm

# Verify installation
npm --version
```

</details>

<details>
<summary><strong>Using nvm (All Distros - Recommended)</strong></summary>

```bash
# Install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash

# Restart terminal or run
source ~/.bashrc

# Install latest LTS
nvm install --lts

# Verify
npm --version
```

</details>

---

## Update npm

npm can update itself:

```bash
# Update to latest version
npm install -g npm@latest

# Check version
npm --version
```

---

## Configuration

### Set Global Package Directory (Linux/macOS)

Avoid permission issues by setting a user-owned directory:

```bash
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```

### View Configuration

```bash
npm config list
```

### Set Registry

```bash
npm config set registry https://registry.npmjs.org
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `npm install` | Install all dependencies |
| `npm install <package>` | Add a package |
| `npm install -D <package>` | Add a dev dependency |
| `npm uninstall <package>` | Remove a package |
| `npm update` | Update all packages |
| `npm run <script>` | Run a script from package.json |
| `npm test` | Run tests |

---

## Troubleshooting

### EACCES Permission Denied (Linux/macOS)

```bash
# Option 1: Change npm's default directory
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
export PATH=~/.npm-global/bin:$PATH

# Option 2: Fix ownership
sudo chown -R $(whoami) ~/.npm
```

### Slow Installation

```bash
# Use a faster registry mirror
npm config set registry https://registry.npmmirror.com
```

### Clear Cache

```bash
npm cache clean --force
```

---

## Related Documentation

- [Official npm Documentation](https://docs.npmjs.com/)
- [Main README](../../README.md)
- [Info Directory](./README.md)

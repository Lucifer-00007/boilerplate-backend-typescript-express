# Windows Setup Guide

Complete guide to set up the Node.js Express TypeScript boilerplate on Windows.

## Prerequisites

### 1. Install Node.js

<details>
<summary><strong>Option A: Using Official Installer (Recommended)</strong></summary>

1. Download the LTS version from [nodejs.org](https://nodejs.org/)
2. Run the installer and follow the prompts
3. Ensure "Add to PATH" is checked during installation
4. Restart your terminal/PowerShell

Verify installation:

```powershell
node --version
npm --version
```

</details>

<details>
<summary><strong>Option B: Using Chocolatey</strong></summary>

First, install Chocolatey (run PowerShell as Administrator):

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

Then install Node.js:

```powershell
choco install nodejs-lts
```

</details>

<details>
<summary><strong>Option C: Using nvm-windows</strong></summary>

1. Download nvm-windows from [github.com/coreybutler/nvm-windows](https://github.com/coreybutler/nvm-windows/releases)
2. Run the installer
3. Open a new PowerShell window

```powershell
# Install latest LTS version
nvm install lts

# Use the installed version
nvm use lts

# Verify
node --version
```

</details>

### 2. Install a Package Manager

<details>
<summary><strong>📦 npm (comes with Node.js)</strong></summary>

npm is installed automatically with Node.js. Verify installation:

```powershell
npm --version
```

</details>

<details>
<summary><strong>🧶 Yarn</strong></summary>

```powershell
# Using npm
npm install -g yarn

# Using Chocolatey
choco install yarn

# Verify installation
yarn --version
```

</details>

<details>
<summary><strong>🚀 pnpm</strong></summary>

```powershell
# Using npm
npm install -g pnpm

# Using Chocolatey
choco install pnpm

# Verify installation
pnpm --version
```

</details>

<details>
<summary><strong>🔥 Bun</strong></summary>

```powershell
# Using npm
npm install -g bun

# Using PowerShell
irm bun.sh/install.ps1 | iex

# Verify installation
bun --version
```

> **Note**: Bun on Windows is still experimental. Consider using WSL2 for full Bun support.

</details>

### 3. Install MongoDB

<details>
<summary><strong>Option A: Using Official Installer</strong></summary>

1. Download MongoDB Community Server from [mongodb.com/try/download/community](https://www.mongodb.com/try/download/community)
2. Run the installer
3. Choose "Complete" installation
4. Check "Install MongoDB as a Service"
5. Optionally install MongoDB Compass (GUI)

Verify installation:

```powershell
mongosh --eval "db.runCommand({ ping: 1 })"
```

</details>

<details>
<summary><strong>Option B: Using Chocolatey</strong></summary>

```powershell
# Run PowerShell as Administrator
choco install mongodb

# Start MongoDB service
net start MongoDB
```

</details>

<details>
<summary><strong>Option C: Using Docker</strong></summary>

```powershell
# Install Docker Desktop first (see below)
docker run -d -p 27017:27017 --name mongodb mongo:latest
```

</details>

### 4. Install Docker (Optional, for Docker workflows)

1. Enable WSL2:
   ```powershell
   # Run PowerShell as Administrator
   wsl --install
   ```
2. Restart your computer
3. Download and install [Docker Desktop](https://www.docker.com/products/docker-desktop/)
4. Ensure WSL2 backend is enabled in Docker Desktop settings

Verify installation:

```powershell
docker --version
docker-compose --version
```

### 5. Install Git

```powershell
# Using Chocolatey
choco install git

# Or download from https://git-scm.com/download/win
```

## Project Setup

### 1. Clone the Repository

```powershell
git clone <repository-url>
cd <project-name>
```

### 2. Install Dependencies

Choose your preferred package manager:

```powershell
# npm
npm install

# yarn
yarn install

# pnpm
pnpm install

# bun
bun install
```

### 3. Configure Environment Variables

```powershell
copy .env.example .env
```

Edit `.env` with your configuration using Notepad or VS Code:

```powershell
notepad .env
# or
code .env
```

### 4. Start the Development Server

```powershell
# npm
npm run dev

# yarn
yarn dev

# pnpm
pnpm dev

# bun
bun run dev
```

The server will start at `http://localhost:3000`.

## Troubleshooting

### Port 3000 already in use

```powershell
# Find process using port 3000
netstat -ano | findstr :3000

# Kill the process (replace PID with actual PID)
taskkill /PID <PID> /F
```

### MongoDB connection failed

```powershell
# Check if MongoDB service is running
Get-Service MongoDB

# Start MongoDB service
net start MongoDB
```

### Execution policy errors

```powershell
# Run PowerShell as Administrator
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### Long path issues

Enable long paths in Windows:

1. Open `gpedit.msc` (Group Policy Editor)
2. Navigate to: Computer Configuration > Administrative Templates > System > Filesystem
3. Enable "Enable Win32 long paths"

Or via PowerShell (as Administrator):

```powershell
New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" -Name "LongPathsEnabled" -Value 1 -PropertyType DWORD -Force
```

## Using WSL2 (Recommended for better compatibility)

For the best development experience on Windows, consider using WSL2 (Windows Subsystem for Linux):

```powershell
# Install WSL2 with Ubuntu
wsl --install -d Ubuntu

# After installation, open Ubuntu from Start menu
# Then follow the Linux setup guide
```

## Next Steps

- View API documentation at `http://localhost:3000/v1/docs`
- Run tests with `npm test` or `yarn test`
- Check the main [README](../../README.md) for more details

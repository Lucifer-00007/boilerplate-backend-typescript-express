# macOS Setup Guide

Complete guide to set up the Node.js Express TypeScript boilerplate on macOS.

## Prerequisites

### 1. Install Homebrew (if not installed)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 2. Install Node.js

<details>
<summary><strong>Option A: Using Homebrew</strong></summary>

```bash
brew install node
```

</details>

<details>
<summary><strong>Option B: Using nvm (Recommended)</strong></summary>

```bash
# Install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash

# Restart terminal or run
source ~/.zshrc

# Install latest LTS version
nvm install --lts

# Use the installed version
nvm use --lts
```

</details>

### 3. Install a Package Manager

<details>
<summary><strong>📦 npm (comes with Node.js)</strong></summary>

npm is installed automatically with Node.js. Verify installation:

```bash
npm --version
```

</details>

<details>
<summary><strong>🧶 Yarn</strong></summary>

```bash
# Using Homebrew
brew install yarn

# Or using npm
npm install -g yarn

# Verify installation
yarn --version
```

</details>

<details>
<summary><strong>🚀 pnpm</strong></summary>

```bash
# Using Homebrew
brew install pnpm

# Or using npm
npm install -g pnpm

# Verify installation
pnpm --version
```

</details>

<details>
<summary><strong>🔥 Bun</strong></summary>

```bash
# Using Homebrew
brew install oven-sh/bun/bun

# Or using curl
curl -fsSL https://bun.sh/install | bash

# Verify installation
bun --version
```

</details>

### 4. Install MongoDB

<details>
<summary><strong>Option A: Using Homebrew</strong></summary>

```bash
# Add MongoDB tap
brew tap mongodb/brew

# Install MongoDB Community Edition
brew install mongodb-community

# Start MongoDB as a service
brew services start mongodb-community

# Verify MongoDB is running
mongosh --eval "db.runCommand({ ping: 1 })"
```

</details>

<details>
<summary><strong>Option B: Using Docker</strong></summary>

```bash
# Install Docker Desktop from https://docker.com/products/docker-desktop
# Or using Homebrew
brew install --cask docker

# Run MongoDB container
docker run -d -p 27017:27017 --name mongodb mongo:latest
```

</details>

### 5. Install Docker (Optional, for Docker workflows)

```bash
# Install Docker Desktop
brew install --cask docker

# Start Docker Desktop from Applications
# Verify installation
docker --version
docker-compose --version
```

## Project Setup

### 1. Clone the Repository

```bash
git clone <repository-url>
cd <project-name>
```

### 2. Install Dependencies

Choose your preferred package manager:

```bash
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

```bash
cp .env.example .env
```

Edit `.env` with your configuration:

```bash
# Open with default editor
open -e .env

# Or use nano/vim
nano .env
```

### 4. Start the Development Server

```bash
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

```bash
# Find process using port 3000
lsof -i :3000

# Kill the process
kill -9 <PID>
```

### MongoDB connection failed

```bash
# Check if MongoDB is running
brew services list | grep mongodb

# Restart MongoDB
brew services restart mongodb-community
```

### Permission denied errors

```bash
# Fix npm permissions
sudo chown -R $(whoami) ~/.npm
```

## Next Steps

- View API documentation at `http://localhost:3000/v1/docs`
- Run tests with `npm test` or `yarn test`
- Check the main [README](../../README.md) for more details

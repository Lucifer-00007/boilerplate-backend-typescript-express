# Linux Setup Guide

Complete guide to set up the Node.js Express TypeScript boilerplate on Linux (Ubuntu/Debian, Fedora/RHEL, Arch).

## Prerequisites

### 1. Install Node.js

<details>
<summary><strong>Ubuntu/Debian</strong></summary>

**Option A: Using NodeSource (Recommended)**

```bash
# Install Node.js 20.x LTS
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs

# Verify installation
node --version
npm --version
```

**Option B: Using nvm**

```bash
# Install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash

# Restart terminal or run
source ~/.bashrc

# Install latest LTS version
nvm install --lts
nvm use --lts
```

</details>

<details>
<summary><strong>Fedora/RHEL/CentOS</strong></summary>

**Option A: Using dnf**

```bash
# Fedora
sudo dnf install nodejs npm

# RHEL/CentOS (enable EPEL first)
sudo dnf install epel-release
sudo dnf install nodejs npm
```

**Option B: Using nvm**

```bash
# Install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash

# Restart terminal or run
source ~/.bashrc

# Install latest LTS version
nvm install --lts
nvm use --lts
```

</details>

<details>
<summary><strong>Arch Linux</strong></summary>

```bash
# Using pacman
sudo pacman -S nodejs npm

# Verify installation
node --version
npm --version
```

</details>

### 2. Install a Package Manager

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
# Using npm (all distros)
npm install -g yarn

# Ubuntu/Debian
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt update && sudo apt install yarn

# Fedora
sudo dnf install yarn

# Arch
sudo pacman -S yarn

# Verify installation
yarn --version
```

</details>

<details>
<summary><strong>🚀 pnpm</strong></summary>

```bash
# Using npm (all distros)
npm install -g pnpm

# Using curl
curl -fsSL https://get.pnpm.io/install.sh | sh -

# Verify installation
pnpm --version
```

</details>

<details>
<summary><strong>🔥 Bun</strong></summary>

```bash
# Using curl (all distros)
curl -fsSL https://bun.sh/install | bash

# Restart terminal or run
source ~/.bashrc

# Verify installation
bun --version
```

</details>

### 3. Install MongoDB

<details>
<summary><strong>Ubuntu/Debian</strong></summary>

```bash
# Import MongoDB public key
curl -fsSL https://pgp.mongodb.com/server-7.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg --dearmor

# Add MongoDB repository (Ubuntu 22.04)
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | \
   sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list

# Install MongoDB
sudo apt-get update
sudo apt-get install -y mongodb-org

# Start MongoDB
sudo systemctl start mongod
sudo systemctl enable mongod

# Verify
mongosh --eval "db.runCommand({ ping: 1 })"
```

</details>

<details>
<summary><strong>Fedora/RHEL/CentOS</strong></summary>

```bash
# Create repo file
sudo tee /etc/yum.repos.d/mongodb-org-7.0.repo << 'EOF'
[mongodb-org-7.0]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/9/mongodb-org/7.0/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://pgp.mongodb.com/server-7.0.asc
EOF

# Install MongoDB
sudo dnf install -y mongodb-org

# Start MongoDB
sudo systemctl start mongod
sudo systemctl enable mongod
```

</details>

<details>
<summary><strong>Arch Linux</strong></summary>

```bash
# Using AUR (yay)
yay -S mongodb-bin

# Start MongoDB
sudo systemctl start mongodb
sudo systemctl enable mongodb
```

</details>

<details>
<summary><strong>Using Docker (All Distros)</strong></summary>

```bash
# Install Docker first (see below)
docker run -d -p 27017:27017 --name mongodb mongo:latest
```

</details>

### 4. Install Docker (Optional, for Docker workflows)

<details>
<summary><strong>Ubuntu/Debian</strong></summary>

```bash
# Remove old versions
sudo apt-get remove docker docker-engine docker.io containerd runc

# Install prerequisites
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg

# Add Docker's official GPG key
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add repository
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Add user to docker group (logout/login required)
sudo usermod -aG docker $USER
```

</details>

<details>
<summary><strong>Fedora</strong></summary>

```bash
# Install Docker
sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Start Docker
sudo systemctl start docker
sudo systemctl enable docker

# Add user to docker group
sudo usermod -aG docker $USER
```

</details>

<details>
<summary><strong>Arch Linux</strong></summary>

```bash
# Install Docker
sudo pacman -S docker docker-compose

# Start Docker
sudo systemctl start docker
sudo systemctl enable docker

# Add user to docker group
sudo usermod -aG docker $USER
```

</details>

### 5. Install Git

```bash
# Ubuntu/Debian
sudo apt install git

# Fedora
sudo dnf install git

# Arch
sudo pacman -S git
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
nano .env
# or
vim .env
# or
code .env
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
sudo lsof -i :3000

# Kill the process
kill -9 <PID>
```

### MongoDB connection failed

```bash
# Check MongoDB status
sudo systemctl status mongod

# Restart MongoDB
sudo systemctl restart mongod

# Check logs
sudo journalctl -u mongod
```

### Permission denied for npm global packages

```bash
# Option 1: Change npm's default directory
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc

# Option 2: Fix permissions
sudo chown -R $(whoami) ~/.npm
```

### Docker permission denied

```bash
# Add user to docker group
sudo usermod -aG docker $USER

# Logout and login again, or run
newgrp docker
```

## Next Steps

- View API documentation at `http://localhost:3000/v1/docs`
- Run tests with `npm test` or `yarn test`
- Check the main [README](../../README.md) for more details

# Info

This directory contains informational documentation and setup guides for the project.

## OS-Specific Setup Guides

Get started with the project on your operating system:

| Operating System | Guide | Description |
|------------------|-------|-------------|
| 🍎 **macOS** | [macos-setup.md](./project-setup/macos-setup.md) | Homebrew, Node.js, MongoDB, Docker setup |
| 🪟 **Windows** | [windows-setup.md](./project-setup/windows-setup.md) | Chocolatey, Node.js, MongoDB, Docker, WSL2 setup |
| 🐧 **Linux** | [linux-setup.md](./project-setup/linux-setup.md) | Ubuntu/Debian, Fedora, Arch installation |

## Package Manager Setup Guides

Install your preferred package manager globally:

| Package Manager | Guide | Description |
|-----------------|-------|-------------|
| 📦 **npm** | [npm-setup-guide.md](./package-manager-setup/npm-setup-guide.md) | Comes with Node.js, standard package manager |
| 🧶 **Yarn** | [yarn-setup-guide.md](./package-manager-setup/yarn-setup-guide.md) | Default for this project, required for Docker |
| 🚀 **pnpm** | [pnpm-setup-guide.md](./package-manager-setup/pnpm-setup-guide.md) | Fast, disk space efficient |
| 🔥 **Bun** | [bun-setup-guide.md](./package-manager-setup/bun-setup-guide.md) | All-in-one JavaScript runtime |

## Package Manager Compatibility

| Package Manager | Local Dev | Docker |
|-----------------|-----------|--------|
| npm | ✅ | ❌ |
| Yarn | ✅ | ✅ (Required) |
| pnpm | ✅ | ❌ |
| Bun | ✅ | ❌ |

> ⚠️ **Note**: Docker workflows require Yarn due to `yarn.lock` dependency.

## Purpose

Store general information, guides, and reference materials related to:

- Project setup and configuration
- Architecture decisions
- Feature documentation
- API guides
- Development guidelines

## Naming Convention

Use descriptive, kebab-case filenames:
- `feature-name-guide.md`
- `setup-instructions.md`
- `api-reference.md`

## Related Documentation

- [Main README](../../README.md) - Project overview and commands
- [Contributing Guide](../../CONTRIBUTING.md) - How to contribute
- [Changelog](../../CHANGELOG.md) - Version history

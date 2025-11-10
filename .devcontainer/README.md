# Dev Container Setup

This dev container provides a consistent development environment for the CNN project across all platforms (Linux, macOS, Windows).

## What's Included

- **C++ Toolchain**: g++, CMake, build-essential (from Microsoft's base image)
- **C++ Dependencies**: OpenCV, libmicrohttpd (pre-installed)
- **Java**: OpenJDK 17 (installed via Dev Container Feature from GitHub)
- **Tools**: git, curl, wget, vim
- **Auto-cleanup**: Stale build directories are cleaned on container start

## Prerequisites

1. [Docker Desktop](https://www.docker.com/products/docker-desktop/)
2. [VS Code](https://code.visualstudio.com/)
3. [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## Getting Started

1. Open this repository in VS Code
2. When prompted, click "Reopen in Container" (or press `F1` and select "Dev Containers: Reopen in Container")
3. Wait for the container to build (first time only, ~3-5 minutes)
4. You're ready to code!

## Building the Project

### Backend (C++)
All dependencies (OpenCV, libmicrohttpd) are pre-installed!

```bash
cd backend
./build.sh
```

Or manually:
```bash
cd backend
mkdir build && cd build
cmake ..
make
```

### Frontend (Java)
```bash
cd frontend
javac -d bin src/com/classifier/**/*.java
```

## Troubleshooting

### Container build is slow on first run
- First build downloads Microsoft's base image (~1-2GB) and Java from GitHub
- Subsequent builds are much faster due to Docker layer caching
- The setup avoids Ubuntu's ARM64 repositories entirely for maximum reliability

### Why This Setup?
This dev container uses:
- **Microsoft's C++ base image** - Pre-built, tested, and cached
- **Dev Container Features for Java** - Downloads from GitHub (ghcr.io) instead of Ubuntu's problematic ARM64 mirrors
- This approach completely avoids the hash sum mismatch errors common with Ubuntu ARM64 repositories

### Container fails to build
- If issues persist, clear Docker cache: `docker system prune -a`
- Then rebuild: `CMD/CTRL + Shift + P` → "Dev Containers: Rebuild Container"

### Port conflicts
- The container forwards port 8080 by default
- Change the port in `devcontainer.json` if needed

## Architecture Support

This dev container works on:
- ✅ ARM64 (Apple Silicon M1/M2/M3)
- ✅ AMD64 (Intel/AMD x86_64)

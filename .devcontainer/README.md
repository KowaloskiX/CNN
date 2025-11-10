# Dev Container Setup

This dev container provides a consistent development environment for the CNN project across all platforms (Linux, macOS, Windows).

## What's Included

- **C++ Toolchain**: g++, CMake, build-essential
- **Java**: OpenJDK 17
- **Tools**: git, curl, wget, vim

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
```bash
cd backend
mkdir -p build
cd build
cmake ..
make
```

### Frontend (Java)
```bash
cd frontend
# Compile Java files
javac -d bin src/com/classifier/**/*.java
```

## Troubleshooting

### Container fails to build on M2 Mac
- The Dockerfile uses Ubuntu (not Debian) for better ARM64 support
- If you still have issues, try: Docker Desktop → Settings → Use Rosetta for x86/amd64 emulation

### Port conflicts
- The container forwards port 8080 by default
- Change the port in `devcontainer.json` if needed

## Architecture Support

This dev container works on:
- ✅ ARM64 (Apple Silicon M1/M2/M3)
- ✅ AMD64 (Intel/AMD x86_64)

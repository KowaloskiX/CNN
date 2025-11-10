# Use Microsoft's official C++ dev container base image
# This includes C++ build tools (g++, cmake, git, etc.) pre-installed
# Java will be installed via dev container features (see devcontainer.json)
FROM mcr.microsoft.com/devcontainers/cpp:ubuntu-22.04

# Install project-specific dependencies
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        libopencv-dev \
        libmicrohttpd-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Set working directory
WORKDIR /workspace

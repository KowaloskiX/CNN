# Use Microsoft's official C++ dev container base image
# This avoids Ubuntu ARM64 mirror sync issues and includes build tools pre-installed
FROM mcr.microsoft.com/devcontainers/cpp:ubuntu-22.04

# Prevent interactive prompts during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Install Java (build tools already included in base image)
RUN apt-get update \
    && apt-get install -y --no-install-recommends openjdk-17-jdk \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Set Java environment variables
ENV JAVA_HOME=/usr/lib/jvm/default-java
ENV PATH="${JAVA_HOME}/bin:${PATH}"

# Set working directory
WORKDIR /workspace

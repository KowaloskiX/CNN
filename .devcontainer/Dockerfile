# Use Ubuntu instead of Debian for better ARM64 (M2 Mac) support
FROM ubuntu:22.04

# Prevent interactive prompts during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Install packages with retry logic to handle mirror issues
RUN apt-get clean && rm -rf /var/lib/apt/lists/* \
    && apt-get update --fix-missing || apt-get update --fix-missing \
    && apt-get install -y --no-install-recommends \
    build-essential \
    cmake \
    git \
    openjdk-17-jdk \
    curl \
    wget \
    vim \
    ca-certificates \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Create a non-root user
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt-get update --fix-missing || apt-get update --fix-missing \
    && apt-get install -y --no-install-recommends sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Set Java environment variables
# Ubuntu creates a default-java symlink that points to the correct architecture
ENV JAVA_HOME=/usr/lib/jvm/default-java
ENV PATH="${JAVA_HOME}/bin:${PATH}"

# Switch to non-root user
USER $USERNAME

# Set working directory
WORKDIR /workspace

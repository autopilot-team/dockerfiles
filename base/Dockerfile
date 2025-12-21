# syntax=docker/dockerfile:1
FROM jdxcode/mise:2025.12.0 AS base

ARG TARGETARCH
ENV PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1
WORKDIR /app

# Set shell options for safer pipe handling
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Install system dependencies, canvas runtime deps, Docker, and tini
# hadolint ignore=DL3008
RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y apt-transport-https build-essential ca-certificates curl gnupg libvips-dev libcairo2 libpango-1.0-0 libpangocairo-1.0-0 libjpeg62-turbo libgif-dev librsvg2-2 python3 pkg-config lsb-release && \
    curl -L https://github.com/krallin/tini/releases/download/v0.19.0/tini-static-${TARGETARCH} -o /usr/bin/tini && \
    chmod +x /usr/bin/tini && \
    curl -sLf --retry 3 --tlsv1.2 --proto "=https" 'https://packages.doppler.com/public/cli/gpg.DE2A7741A397C129.key' | gpg --dearmor -o /usr/share/keyrings/doppler-archive-keyring.gpg && \
    echo "deb [signed-by=/usr/share/keyrings/doppler-archive-keyring.gpg] https://packages.doppler.com/public/cli/deb/debian any-version main" | tee /etc/apt/sources.list.d/doppler-cli.list && \
    mkdir -p /etc/apt/keyrings && \
    curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \"$(lsb_release -cs)\" stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null && \
    apt-get update -qq && \
    apt-get install --no-install-recommends -y doppler docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin && \
    rm -rf /var/lib/apt/lists/*

# hadolint ignore=DL3016
RUN npm install -g node-gyp

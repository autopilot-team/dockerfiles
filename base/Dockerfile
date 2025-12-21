# syntax=docker/dockerfile:1
FROM jdxcode/mise:2025.12.0 AS base

ARG TARGETARCH
ENV PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1
WORKDIR /app

# Install system dependencies, canvas runtime deps, and tini
# hadolint ignore=DL3008
RUN apt update -qq && \
    apt install --no-install-recommends -y apt-transport-https build-essential ca-certificates curl gnupg libvips-dev libcairo2 libpango-1.0-0 libpangocairo-1.0-0 libjpeg62-turbo libgif-dev librsvg2-2 python3 pkg-config && \
    curl -L https://github.com/krallin/tini/releases/download/v0.19.0/tini-static-${TARGETARCH} -o /usr/bin/tini && \
    chmod +x /usr/bin/tini && \
    curl -sLf --retry 3 --tlsv1.2 --proto "=https" 'https://packages.doppler.com/public/cli/gpg.DE2A7741A397C129.key' | gpg --dearmor -o /usr/share/keyrings/doppler-archive-keyring.gpg && \
    echo "deb [signed-by=/usr/share/keyrings/doppler-archive-keyring.gpg] https://packages.doppler.com/public/cli/deb/debian any-version main" | tee /etc/apt/sources.list.d/doppler-cli.list && \
    apt update -qq && \
    apt install -y doppler && \
    rm -rf /var/lib/apt/lists/*

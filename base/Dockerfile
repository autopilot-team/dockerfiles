# syntax=docker/dockerfile:1
FROM jdxcode/mise:2025.12.0 AS base

ARG TARGETARCH
ENV PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1
WORKDIR /app

# Install system dependencies, canvas runtime deps, and tini
# hadolint ignore=DL3008
RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y wget libvips-dev libcairo2 libpango-1.0-0 libpangocairo-1.0-0 libjpeg62-turbo libgif-dev librsvg2-2 && \
    wget --progress=dot:giga --no-check-certificate -O /usr/bin/tini https://github.com/krallin/tini/releases/download/v0.19.0/tini-static-${TARGETARCH} && \
    chmod +x /usr/bin/tini && \
    rm -rf /var/lib/apt/lists/*

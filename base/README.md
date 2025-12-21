# Base Docker Image

Docker image based on [jdxcode/mise:2025.12.0](https://hub.docker.com/r/jdxcode/mise) with additional system dependencies for common development needs.

## What is Mise?

Mise is a polyglot tool version manager. It replaces tools like asdf, nvm, pyenv, rbenv, etc.

## Features

- Based on official mise image (2025.12.0)
- Pre-configured working directory at `/app`
- System dependencies for common use cases:
  - libvips for image processing
  - Cairo and Pango for canvas operations
  - JPEG, GIF, and SVG support
  - Tini process manager for proper signal handling
- Playwright browser download disabled (set `PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1`)
- Multi-architecture support (ARM64, AMD64)

## Usage

```bash
docker pull <your-dockerhub-username>/base:latest
docker run --rm <your-dockerhub-username>/base:latest mise --version
```

## Building Locally

```bash
docker build -t base:local --build-arg TARGETARCH=amd64 .
# For ARM64:
# docker build -t base:local --build-arg TARGETARCH=arm64 .
```

## Use Cases

This base image is ideal for:
- Web development projects requiring canvas manipulation
- Applications using image processing libraries
- Polyglot development environments with mise
- Projects needing proper process management with tini

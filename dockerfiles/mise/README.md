# Mise Docker Image

Docker image based on [jdxcode/mise:2025.12.0](https://hub.docker.com/r/jdxcode/mise).

## What is Mise?

Mise is a polyglot tool version manager. It replaces tools like asdf, nvm, pyenv, rbenv, etc.

## Usage

```bash
docker pull <your-dockerhub-username>/mise:latest
docker run --rm <your-dockerhub-username>/mise:latest mise --version
```

## Building Locally

```bash
docker build -t mise:local .
```

## Features

- Based on official mise image (2025.12.0)
- Pre-configured working directory at `/app`
- Mise data and config directories set up
- Ready to use for polyglot development environments

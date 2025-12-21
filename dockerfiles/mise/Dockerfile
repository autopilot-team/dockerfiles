# syntax=docker/dockerfile:1
FROM jdxcode/mise:2025.12.0 AS base

# Set working directory
WORKDIR /app

# Set environment variables
ENV MISE_DATA_DIR=/app/.mise
ENV MISE_CONFIG_DIR=/app/.config/mise

# Create necessary directories and verify mise installation
RUN mkdir -p ${MISE_DATA_DIR} ${MISE_CONFIG_DIR} && \
    mise --version

# Default command - note that entrypoint is already "mise"
CMD ["version"]

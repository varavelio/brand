# Use node as the base image
FROM node:24.14.0-trixie

# Install task
COPY --from=ghcr.io/varavelio/container-tools/task:3.54.0 /usr/local/bin/task /usr/local/bin/task

# Install dprint
COPY --from=ghcr.io/varavelio/container-tools/dprint:0.61.1 /usr/local/bin/dprint /usr/local/bin/dprint

# Set build time variables
ARG DEBIAN_FRONTEND=noninteractive

RUN set -e && \
    # Update and install system dependencies
    apt-get update -qq && \
    apt-get install -yqq --no-install-recommends \
        git wget curl zip unzip p7zip-full tree ripgrep python3 python3-pip && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /workspaces/brand

# Command just to keep the container running
CMD ["sleep", "infinity"]

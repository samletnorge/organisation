FROM node:24-bookworm-slim

# Native build dependencies for Backstage packages (including scaffolder deps).
RUN apt-get update \
    && apt-get install -y --no-install-recommends python3 g++ build-essential libsqlite3-dev \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

# Disable Node snapshots for compatibility with some Backstage backend plugins.
ENV NODE_OPTIONS="--no-node-snapshot"

COPY . .

RUN corepack enable \
    && yarn install --immutable \
    && yarn tsc \
    && yarn build:backend

EXPOSE 7007

CMD ["node", "packages/backend", "--config", "app-config.yaml", "--config", "app-config.production.yaml"]

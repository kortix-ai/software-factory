# An example dev image. Adapt it to the repository: its runtimes at their pinned
# versions, its system packages, git and gh. No COPY from the repository: the
# agents clone the code at run time.
FROM node:22-bookworm
RUN apt-get update \
 && apt-get install -y --no-install-recommends git curl ca-certificates gh \
 && rm -rf /var/lib/apt/lists/*
RUN corepack enable

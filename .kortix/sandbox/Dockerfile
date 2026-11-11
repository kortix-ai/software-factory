# An example dev image. Adapt it to the repository: its runtimes at their pinned
# versions, its system packages, git, gh and jq (the factory's scripts need all
# three). No COPY from the repository: the agents clone the code at run time.
FROM node:22-bookworm
RUN apt-get update \
 && apt-get install -y --no-install-recommends git curl ca-certificates gh jq \
 && rm -rf /var/lib/apt/lists/*
RUN corepack enable
# The `tests` source runs the repository's end-to-end tests. When they use a
# browser, install it here at the version the lockfile pins, for example:
# RUN npx --yes playwright@<version> install --with-deps chromium

# yet-another-userver-demo

## Prerequisites

### git clone

Clone with `--recurse-submodules` option or run `git submodule update --init`

### devcontainers/cli

```bash
npm install -g @devcontainers/cli
```

## Requirements
- docker 24.0.7
- docker compose 2.21.0
- devcontainers/cli (optional)

## Build

### Docker

You can build a project manually with `docker`. You have to build an image and run a containers with `cmake` commands:
```bash
docker pull pavelbezpravel/yet-another-userver-demo-build-base:0.1.0

docker run \
  --rm \
  -it \
  -u 1000:1000 \
  -v "$(pwd)":/workspaces/yet-another-userver-demo \
  -w "/workspaces/yet-another-userver-demo" \
  pavelbezpravel/yet-another-userver-demo-build-base:0.1.0 \
  cmake \
  --preset=release

docker run \
  --rm \
  -it \
  -u 1000:1000 \
  -v "$(pwd)":/workspaces/yet-another-userver-demo \
  -w "/workspaces/yet-another-userver-demo" \
  pavelbezpravel/yet-another-userver-demo-build-base:0.1.0 \
  cmake \
  --build \
  --preset=release
```

### Dev Container Cli

Also, you can build a project with [devcontainers](https://containers.dev/) in an easy and convenient way.
Your IDE (e.g. Clion) or code editor (e.g. VS Code) can run and attach to devcontainer.

You can use devcontainers/cli to set up environment and build the project manually via bash:
```bash
devcontainer up --workspace-folder .

devcontainer exec --workspace-folder . \
  cmake \
  --preset=release

devcontainer exec --workspace-folder . \
  cmake \
  --build \
  --preset=release
```

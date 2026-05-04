# StellarStack Planets

Container image definitions ("planets") for the StellarStack panel — the
replacement for Pterodactyl's eggs / yolks. Each subdirectory holds one
runtime environment, with a `Dockerfile` and (where applicable) an
`entrypoint.sh` and any helper files.

## Layout

```
games/      Game-specific images (Hytale, Rust, Source-engine, …)
go/         Go runtime, one tag per minor version
installers/ Base install-stage images
java/       OpenJDK + OpenJ9 variants, one tag per major version
nodejs/     Node.js LTS / current images
oses/       Vanilla OS bases
python/     CPython images
```

## Built images

Every `Dockerfile` in this repo is built for **`linux/amd64`** and
**`linux/arm64`** by the `Build planet images` workflow and pushed to
GitHub Container Registry. The image name follows the directory path:

```
ghcr.io/stellarstackoss/stellarstack-planets/<path>:latest
ghcr.io/stellarstackoss/stellarstack-planets/<path>:<short-sha>
```

Example:

```
ghcr.io/stellarstackoss/stellarstack-planets/java/21:latest
ghcr.io/stellarstackoss/stellarstack-planets/games/rust:latest
```

The workflow runs on every push to `main` and can be triggered manually
with an optional substring filter to rebuild a subset (e.g. `java/21`).

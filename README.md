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
GitHub Container Registry as a single package (`planets`) with one tag
per planet. The tag is the directory path with `/` → `_`:

```
ghcr.io/stellarstackoss/planets:<category>_<variant>
ghcr.io/stellarstackoss/planets:<category>_<variant>-<short-sha>
```

Examples:

```
ghcr.io/stellarstackoss/planets:java_25
ghcr.io/stellarstackoss/planets:games_rust
ghcr.io/stellarstackoss/planets:nodejs_20
ghcr.io/stellarstackoss/planets:python_3.10
```

The workflow runs on every push to `main` and can be triggered manually
with an optional substring filter to rebuild a subset (e.g. `java_25`).

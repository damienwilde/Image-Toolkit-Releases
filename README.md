# Image Toolkit — Releases

Public distribution point for [Image Toolkit](https://github.com/damienwilde/Image-Toolkit).
This repository contains **only release artifacts and update feeds** — the source is private.

It exists because update feeds must be fetchable without authentication:

- **macOS (Sparkle)** reads `image_toolkit_appcast.xml` from this repo's raw URL.
- **Windows / Linux (electron-updater)** read `latest.yml`, `latest-linux.yml` and the
  installers attached to each GitHub Release, using the plain `github` provider —
  no token embedded in the app, and no GitHub API rate limit.

Previously the macOS feed lived in a secret gist with binaries on Google Drive.
Neither is a CDN, and neither keeps a versioned history.

## Layout

| Path | Purpose |
|---|---|
| `image_toolkit_appcast.xml` | Sparkle appcast for the macOS app |
| Release assets | `.zip`/`.dmg` (macOS), `.exe` (Windows), `.AppImage` (Linux), plus electron-updater's `latest*.yml` |

## Publishing

Tagging `v*` on the private source repo runs the build workflow, which packages every
platform on its own runner and publishes here. Nothing is built by hand.

# Mockphine
Mock API Server

This repository hosts release tooling and the public issue tracker for Mockphine.

## Support & Issues

Use GitHub Issues to report bugs or request features. Please select the most relevant issue template and include logs or screenshots when possible.

## Screenshots

Product screenshots and visual assets belong in the screenshots/ folder.

## Release repository

This repository contains release tooling only. The application source code lives in a separate repo.

## Updater integration (external app)

- Embed the updater public key in src-tauri/tauri.conf.json under plugins.updater.pubkey.
- Set the updater endpoint to https://github.com/MockphineApp/Mockphine/releases/latest/download/latest.json.
- After download_and_install, request app restart.

## Release workflow

- Build macOS .app.tar.gz artifacts (arm64 and x86_64) in the app repo or CI.
- Trigger the GitHub Actions workflow with tag, version, and artifact URLs.
- Provide TAURI_PRIVATE_KEY and TAURI_PRIVATE_KEY_PASSWORD secrets in this repo.

## Local latest.json generation

- bun install
- bun run release:latest-json -- --version X.Y.Z --product-name Mockphine --tag vX.Y.Z --bundle-dir /path/to/artifacts

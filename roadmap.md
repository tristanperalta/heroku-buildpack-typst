# Roadmap

## High Priority

- [x] Replace cargo build with pre-built binary download from GitHub Releases
  - Download the pre-built `typst` binary directly instead of installing the entire Rust toolchain and compiling from source
  - Reduces build time from minutes to seconds and shrinks the cache from hundreds of MB to a few MB

- [x] Add `TYPST_VERSION` config var support
  - Allow users to pin a specific Typst version via `heroku config:set TYPST_VERSION=0.14.2`
  - Default to a known stable version when not set
  - Enables reproducible builds

## Medium Priority

- [x] Detect architecture (amd64/arm64)
  - Heroku Cedar runs on `linux/amd64`, but Fir supports `arm64`
  - Automatically select the correct binary for the platform

- [x] Improve README with usage docs
  - Installation instructions
  - Config var documentation (`TYPST_VERSION`)
  - Usage examples
  - Multi-buildpack setup guidance

## Low Priority

- [x] Smarter `bin/detect`
  - Check for `.typ` files or a config var instead of always matching
  - Avoids running unnecessarily in multi-buildpack setups

- [x] Add `bin/release` script
  - Return default process types or config if needed

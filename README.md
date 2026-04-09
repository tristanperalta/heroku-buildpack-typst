# Heroku Buildpack for Typst

A [Heroku buildpack](https://devcenter.heroku.com/articles/buildpacks) that installs the [Typst](https://typst.app/) CLI on your Heroku app.

## Installation

```sh
heroku buildpacks:add https://github.com/tristanperalta/heroku-buildpack-typst
```

When using multiple buildpacks, add it before or after your primary buildpack as needed:

```sh
heroku buildpacks:add --index 1 https://github.com/tristanperalta/heroku-buildpack-typst
```

## Configuration

### `TYPST_VERSION`

Set the Typst version to install. Defaults to `0.14.2`.

```sh
heroku config:set TYPST_VERSION=0.14.2
```

Available versions can be found on the [Typst releases page](https://github.com/typst/typst/releases).

## How It Works

1. Downloads a pre-built Typst binary from [GitHub Releases](https://github.com/typst/typst/releases)
2. Caches the binary between builds (keyed by version)
3. Installs it to `/app/.heroku/bin` and adds it to `PATH`
4. Automatically detects the platform architecture (x86_64 / aarch64)

## Usage

After deploying, `typst` is available in your app's PATH:

```sh
heroku run typst --version
heroku run typst compile document.typ
```

## License

MIT

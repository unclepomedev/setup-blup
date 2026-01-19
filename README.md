# setup-blup

A GitHub Action to install [blup](https://github.com/unclepomedev/blup) (Blender Version Manager) and set up Blender
environments with built-in caching support.

Supports **Linux**, **Windows**, and **macOS**.

[![Test Action](https://github.com/unclepomedev/setup-blup/actions/workflows/test.yml/badge.svg)](https://github.com/unclepomedev/setup-blup/actions/workflows/test.yml)

## Usage

### Basic Usage (Stable Version)

```yaml
steps:
  - uses: actions/checkout@v6

  - name: Setup Blender 4.5 LTS
    uses: unclepomedev/setup-blup@v0
    with:
      blender-version: '4.5.0'
      cache: true

  - name: Run Blender
    run: blup run -- --background --version
```

### Daily / Experimental Builds

```yaml
steps:
  - uses: actions/checkout@v6

  # Install the latest Alpha/Beta version (e.g., matching '5.1')
  - name: Setup Blender Daily
    uses: unclepomedev/setup-blup@v0
    with:
      blender-version: 'daily' # or specific version like '5.1'
      daily: true

  - name: Run Blender
    run: blup run -- --background --version
```

### Inputs

| Input             | Description                                                                                         | Default  | Required |
|:------------------|:----------------------------------------------------------------------------------------------------|:---------|:---------|
| `blender-version` | The Blender version to install (e.g., `4.2.0`, `5.0`, `daily`). If empty, only `blup` is installed. | `''`     | No       |
| `daily`           | Set to `true` to search for daily builds.                                                           | `false`  | No       |
| `cache`           | Enable caching for downloaded Blender binaries.                                                     | `true`   | No       |
| `blup-version`    | Specific version of `blup` to use (e.g., `v0.1.0`). Defaults to the latest release.                 | `latest` | No       |

## License

MIT

# Install QHYCCD SDK

GitHub Action to install [QHYCCD SDK](https://www.qhyccd.com) on Linux, Windows, and macOS.

## Usage

```yaml
- uses: ivonnyssen/qhyccd-sdk-install@v2
  with:
    version: "25.09.29"
```

### With caching disabled

```yaml
- uses: ivonnyssen/qhyccd-sdk-install@v2
  with:
    version: "25.09.29"
    cache: false
```

## Inputs

| Name | Description | Default |
|------|-------------|---------|
| `version` | QHYCCD SDK version to install (required) | - |
| `cache` | Enable caching of downloaded files | `true` |

## Features

- **Automatic PATH Configuration**: On Windows and macOS, the SDK binaries are automatically added to `PATH`, so you can use them immediately in subsequent steps without manual configuration.
- **Smart Caching**: Optional caching of downloaded SDK files to speed up workflow runs.
- **Cross-Platform**: Handles platform-specific installation differences automatically.

## Supported Platforms

- Linux (x64) - Installs SDK to system paths via install script
- Windows (x64) - Extracts SDK and automatically adds to PATH
- macOS (Intel/Apple Silicon) - Extracts SDK and automatically adds to PATH

## Local Testing with act

This action works with [act](https://github.com/nektos/act) for local testing. The cache steps will fail gracefully in act (since act doesn't support GitHub's cache actions), but the SDK will still download and install correctly. You can leave caching enabled - the action will simply skip cache operations and download the SDK directly.

Alternatively, you can explicitly disable caching when testing locally:

```yaml
- uses: ivonnyssen/qhyccd-sdk-install@v2
  with:
    version: "25.09.29"
    cache: false
```

## Example Workflow

```yaml
name: Test with QHYCCD SDK

on:
  push:
    branches: [main]
  pull_request:

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v6
      
      - name: Install QHYCCD SDK
        uses: ivonnyssen/qhyccd-sdk-install@v2
        with:
          version: "25.09.29"
      
      - name: Build project
        run: |
          # Your build commands here
          make build
```

## Version Format

The version should match the QHYCCD SDK release format (e.g., "25.09.29").

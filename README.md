# Install QHYCCD SDK

GitHub Action to install [QHYCCD SDK](https://www.qhyccd.com) on Linux, Windows, and macOS.

## Usage

```yaml
- uses: ivonnyssen/qhyccd-sdk-install@v1
  with:
    version: "25.09.29"
```

### With caching disabled

```yaml
- uses: ivonnyssen/qhyccd-sdk-install@v1
  with:
    version: "25.09.29"
    cache: false
```

## Inputs

| Name | Description | Default |
|------|-------------|---------|
| `version` | QHYCCD SDK version to install (required) | - |
| `cache` | Enable caching of downloaded files | `true` |

## Outputs

| Name | Description |
|------|-------------|
| `version` | Installed QHYCCD SDK version |

## Supported Platforms

- Linux (x64)
- Windows (x64)
- macOS (Intel/Apple Silicon)

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
        uses: ivonnyssen/qhyccd-sdk-install@v1
        with:
          version: "25.09.29"
      
      - name: Build project
        run: |
          # Your build commands here
          make build
```

## Version Format

The version should match the QHYCCD SDK release format (e.g., "25.09.29").

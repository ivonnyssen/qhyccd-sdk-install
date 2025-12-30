# Install QHYCCD SDK

GitHub Action to install [QHYCCD SDK](https://www.qhyccd.com) on Linux, Windows, and macOS.

## Usage

```yaml
- uses: ivonnyssen/qhyccd-sdk-install@v1
  with:
    version: "24.12.27"
```

### With caching disabled

```yaml
- uses: ivonnyssen/qhyccd-sdk-install@v1
  with:
    version: "24.12.27"
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

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Install QHYCCD SDK
        uses: ivonnyssen/qhyccd-sdk-install@v1
        with:
          version: "24.12.27"
      
      - name: Build project
        run: |
          # Your build commands here
          make build
```

## Version Format

The version should match the QHYCCD SDK release format (e.g., "24.12.27").

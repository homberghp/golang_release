# golang_release
multiplatform release

## About
A simple "Hello, World!" Go application demonstrating multi-platform releases using GitHub Actions.

## Building

To build the application locally:

```bash
go build -o golang_release .
```

## Running

After building, run the application:

```bash
./golang_release
```

Expected output:
```
Hello, World!
```

## Multi-Platform Releases

This repository uses GitHub Actions to automatically build binaries for multiple platforms when a tag is pushed:

- Linux (amd64, arm64)
- macOS (amd64, arm64)
- Windows (amd64)

### Creating a Release

To create a new release:

1. Create and push a tag:
   ```bash
   git tag v1.0.0
   git push origin v1.0.0
   ```

2. GitHub Actions will automatically:
   - Build binaries for all supported platforms
   - Create a GitHub release
   - Upload all binaries as release assets

### Downloading Releases

Pre-built binaries for all platforms are available on the [Releases](../../releases) page.

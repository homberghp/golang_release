# golang_release
multiplatform release

A simple hello-world Go program with automated multi-platform releases via GitHub Actions.

## Description

This repository demonstrates how to build and release Go binaries for multiple platforms (Linux, Windows, macOS) using GitHub Actions. When you push a tag, the workflow automatically builds binaries for all platforms and uploads them to a single GitHub release.

## Building Locally

```bash
# Build for Linux
GOOS=linux GOARCH=amd64 go build -o golang_release-linux-debian main.go

# Build for Windows
GOOS=windows GOARCH=amd64 go build -o golang_release-windows.exe main.go

# Build for macOS
GOOS=darwin GOARCH=amd64 go build -o golang_release-macos main.go
```

## Running

```bash
# Run directly with Go
go run main.go

# Or run the compiled binary
./golang_release-linux-debian
```

## Release Process

The release workflow is triggered automatically when you push a tag that starts with 'v':

```bash
# Create and push a tag
git tag v1.0.0
git push origin v1.0.0
```

### Workflow Overview

The `.github/workflows/release.yml` workflow consists of two jobs:

1. **build**: Builds binaries for all three platforms in parallel
   - Uses a matrix strategy for Linux, Windows, and macOS
   - Uploads each binary as an artifact
   - Permissions: `contents: read`

2. **release**: Creates a GitHub release and uploads all binaries
   - Downloads all artifacts from the build job
   - Creates a new GitHub release with the tag name
   - Uploads all three platform binaries to the same release:
     - `golang_release-linux-debian` (Linux/Debian)
     - `golang_release-windows.exe` (Windows)
     - `golang_release-macos` (macOS)
   - Permissions: `contents: write`

The workflow clearly demonstrates how to build and upload binaries for multiple platforms to a single release.

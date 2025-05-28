# MerlyMentor

Multi-platform continuous integration for MerlyMentor installation.

## Overview

This repository runs automated MerlyMentor installation across multiple platforms using GitHub Actions.

## Supported Platforms

- **Linux AMD64** (`ubuntu-latest`)
- **Linux ARM64** (`ubuntu-24.04-arm`)
- **macOS Intel** (`macos-13`)
- **macOS Apple Silicon** (`macos-latest`)
- **Windows AMD64** (`windows-latest`)

## Setup

1. **Add Secret**: Set `MM_KEY` in repository secrets with your MerlyMentor license key
2. **Push to main**: CI runs automatically on push/PR to main branch
3. **Manual trigger**: Use "Run workflow" button for on-demand testing

## Workflow

The CI pipeline:

1. Checks out code across all platforms
2. Downloads and installs MerlyMentor using the universal installer
3. Runs inference tests (platform-specific executables)
4. Reports results independently per platform (`fail-fast: false`)

## Local Testing

```bash
# Test installation locally
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/merly-ai/MPCC-Universal/main/install.sh)" -- -k YOUR_KEY_HERE
```

## Troubleshooting

- **"Bad CPU type"**: Architecture mismatch - installer downloaded wrong binary
- **Windows bash errors**: Uses Git Bash available on GitHub runners
- **Failed platforms**: Other platforms continue running independently

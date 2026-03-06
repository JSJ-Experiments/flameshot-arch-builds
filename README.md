# flameshot-arch-builds

This repo builds an Arch Linux package for the latest commit on `master` from:

- `https://github.com/JSJ-Experiments/flameshot`

## What it does

- Uses a `flameshot-git` style `PKGBUILD`
- Pulls source directly from the upstream git repo during the workflow run
- Builds on GitHub Actions inside an `archlinux:latest` container
- Uploads the built package and a SHA256 file as workflow artifacts
- Publishes the package files to GitHub Releases, one prerelease per upstream commit

## Triggers

- Manual runs via `workflow_dispatch`

## Notes

- The package currently targets `x86_64`, which matches GitHub-hosted Linux runners.
- No webhook is required for the current setup because builds only run when manually triggered.
- GitHub Actions artifacts are always downloaded as a `.zip`; use the GitHub Release asset if you want the raw `.pkg.tar.zst` file with its normal filename.

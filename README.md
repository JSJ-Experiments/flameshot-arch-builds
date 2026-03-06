# flameshot-arch-builds

This repo builds an Arch Linux package for the latest commit on `master` from:

- `https://github.com/JSJ-Experiments/flameshot`

## What it does

- Uses a `flameshot-git` style `PKGBUILD`
- Pulls source directly from the upstream git repo during the workflow run
- Builds on GitHub Actions inside an `archlinux:latest` container
- Uploads the built package and a SHA256 file as workflow artifacts

## Triggers

- Pushes to this repo's `master` branch
- Manual runs via `workflow_dispatch`
- A scheduled run every 6 hours
- Optional `repository_dispatch` event named `upstream-flameshot-updated`

## Notes

- The package currently targets `x86_64`, which matches GitHub-hosted Linux runners.
- No webhook is required because the schedule will pick up new upstream commits automatically.
- If you want immediate rebuilds on upstream pushes, you can later add a webhook or another workflow that sends `repository_dispatch` to this repo.

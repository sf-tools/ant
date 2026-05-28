# sf-tools/ant — CI mirror

CI-only mirror for **[themackabu/ant](https://github.com/themackabu/ant)**.

This repository contains **no source code**, only GitHub Actions workflows.
Every run checks out the upstream repo at a chosen ref and builds it on
[Blacksmith](https://blacksmith.sh)-hosted GitHub Actions runners (macOS,
Windows, and Linux on both x86_64 and aarch64).

## Why does this exist?

Blacksmith installs as a GitHub App at the **organization** level. The canonical
`themackabu/ant` repository is owned by a personal account, so the Blacksmith
app cannot run there. This mirror lives under the `sf-tools` org so the app can
be installed and the workflows can target Blacksmith runners.

## How a build is triggered

Every workflow is **manual-only**. There is no automatic dispatch from upstream
pushes. Open the **Actions** tab in this repository and use *Run workflow*,
supplying the upstream ref (branch, tag, or sha) to build.

## Workflows

| File | Purpose |
| --- | --- |
| [`build.yml`](.github/workflows/build.yml) | Build every platform (Linux glibc/musl × x64/aarch64, macOS x64/aarch64, Windows x64) and both Nanos sandbox images. |
| [`build-single.yml`](.github/workflows/build-single.yml) | Build a single chosen platform. |
| [`build-musl-sandboxes.yml`](.github/workflows/build-musl-sandboxes.yml) | Build the two musl variants and the matching Nanos sandbox images. |
| [`build-nanos.yml`](.github/workflows/build-nanos.yml) | Build a Nanos sandbox image for an existing musl artifact. Also callable as a reusable workflow. |
| [`build-platform.yml`](.github/workflows/build-platform.yml) | Reusable per-platform build (called by the workflows above). |

## Runner labels

| Platform | Blacksmith runner |
| --- | --- |
| Linux x86_64 (glibc + musl) | `blacksmith-8vcpu-ubuntu-2404` |
| Linux aarch64 (glibc + musl) | `blacksmith-8vcpu-ubuntu-2404-arm` |
| macOS (x64 + aarch64) | `blacksmith-12vcpu-macos-15` |
| Windows x86_64 | `blacksmith-8vcpu-windows-2025` |

> **Note:** Blacksmith's macOS fleet is Apple Silicon (M4) only. The
> `macos-x64` job runs on the same `blacksmith-12vcpu-macos-15` ARM hardware
> and produces an `x86_64-macos` binary via Zig cross-compilation, matching
> what `versions.json` already specifies for that target.

## Issues and PRs

Open issues and pull requests in the upstream repository:
<https://github.com/themackabu/ant>. This mirror is build infrastructure only.

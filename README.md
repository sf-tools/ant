# sf-tools/ant — CI mirror

CI-only mirror for **[themackabu/ant](https://github.com/themackabu/ant)**.

This repository contains **no source code**, only GitHub Actions workflows.
Every run checks out the upstream repo at a chosen ref and builds it on
[Depot](https://depot.dev)-hosted GitHub Actions runners (macOS, Windows, and
Linux on both x86_64 and aarch64).

## Why does this exist?

Depot installs as a GitHub App at the **organization** level. The canonical
`themackabu/ant` repository is owned by a personal account, so the Depot app
cannot run there. This mirror lives under the `sf-tools` org so the app can be
installed and the workflows can target Depot runners.

## Workflows

| File                                                                     | Purpose                                                                                                              |
| ------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------- |
| [`build.yml`](.github/workflows/build.yml)                               | Build every platform (Linux glibc/musl × x64/aarch64, macOS x64/aarch64, Windows x64) and both Nanos sandbox images. |
| [`build-single.yml`](.github/workflows/build-single.yml)                 | Build a single chosen platform.                                                                                      |
| [`build-musl-sandboxes.yml`](.github/workflows/build-musl-sandboxes.yml) | Build the two musl variants and the matching Nanos sandbox images.                                                   |
| [`build-nanos.yml`](.github/workflows/build-nanos.yml)                   | Build a Nanos sandbox image for an existing musl artifact. Also callable as a reusable workflow.                     |
| [`build-platform.yml`](.github/workflows/build-platform.yml)             | Reusable per-platform build (called by the workflows above).                                                         |

## Issues and PRs

Open issues and pull requests in the upstream repository:
<https://github.com/themackabu/ant>. This mirror is build infrastructure only.

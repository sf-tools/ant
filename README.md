# 🐜 CI mirror

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

## Issues and PRs

Open issues and pull requests in the upstream repository:
<https://github.com/themackabu/ant>. This mirror is build infrastructure only.

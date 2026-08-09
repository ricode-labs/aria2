# Repository Instructions

## Repository Scope

This repository is a GitHub Actions release builder for aria2 binaries. It is not the upstream aria2 source tree.

Before making assumptions about aria2 configuration, TLS behavior, or build options, consult the official aria2 manual: https://aria2.github.io/manual/en/html/README.html

The workflow at `.github/workflows/build.yml` is the executable source of truth. The upstream aria2 source archive is downloaded during CI.

There is no local application source, package manifest, or test suite in this repository. Do not add generated binaries, downloaded source trees, or `dist/` output to the repository.

## Build Targets

The workflow builds `aria2c` binaries for these targets:

- `linux-x86_64`, with static application dependencies and dynamic system OpenSSL 3
- `linux-arm64`, with static application dependencies and dynamic system OpenSSL 3
- `windows-x86_64` using MSYS2 UCRT64
- `macos-arm64`

Keep each platform's dependency paths, compiler flags, link settings, and verification checks intact when editing the workflow.

## Versions

`ARIA2_VERSION` defaults to `1.37.0` and can be overridden only through the manually dispatched workflow input.

## CI Behavior

Pull requests build and test the binaries, but do not publish releases. Pushes do not trigger the workflow.

Manual workflow dispatch builds all platform targets and then runs the `release` job after they succeed.

Platform verification includes `make check` and `aria2c --version`. Linux verifies dynamic system OpenSSL 3, rejects dynamic application dependencies, and performs an HTTPS request without `--ca-certificate`; macOS checks the `arm64` architecture and Homebrew library paths with `otool`.

## Release Behavior

Manual dispatch publishes tag `aria2-${ARIA2_VERSION}` and marks that release as Latest. If a release for the same tag already exists, the workflow deletes the existing release before creating it again.

Release asset names are fixed and do not include the aria2 version or `static`:

- `aria2-linux-x86_64.tar.gz`
- `aria2-linux-arm64.tar.gz`
- `aria2-macos-arm64.tar.gz`
- `aria2-windows-x86_64.zip`

The release tag carries the aria2 version. Latest download URLs should use GitHub's `/releases/latest/download/` route with the fixed asset names.

## Validation

Changes to `.github/workflows/build.yml` should be validated by running the affected GitHub Actions job. Local checks are limited because the actual build happens in CI across Linux, Windows, and macOS runners.

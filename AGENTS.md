# Repository Instructions

## Repository Scope

This repository is a GitHub Actions release builder for aria2 static binaries. It is not the upstream aria2 source tree.

The workflow at `.github/workflows/build.yml` is the executable source of truth. Upstream aria2 source archives and OpenSSL source archives are downloaded during CI.

There is no local application source, package manifest, or test suite in this repository. Do not add generated binaries, downloaded source trees, or `dist/` output to the repository.

## Build Targets

The workflow builds static `aria2c` binaries for these targets:

- `linux-x86_64`
- `windows-x86_64` using MSYS2 UCRT64
- `macos-arm64`

Keep each platform's dependency paths, compiler flags, static-link settings, and verification checks intact when editing the workflow.

## Versions

`ARIA2_VERSION` defaults to `1.37.0` and can be overridden only through the manually dispatched workflow input.

`OPENSSL_VERSION` is pinned in the workflow. When changing it, update related build assumptions and release notes together.

## CI Behavior

Pull requests build and test the binaries, but do not publish releases. Pushes do not trigger the workflow.

Manual workflow dispatch builds all three platform targets and then runs the `release` job after they succeed.

Platform verification includes `make check` and `aria2c --version`. Linux additionally rejects dynamic dependencies with `ldd`; macOS checks the `arm64` architecture and Homebrew library paths with `otool`.

## Release Behavior

Manual dispatch publishes tag `aria2-${ARIA2_VERSION}` and marks that release as Latest.

Release asset names are fixed and do not include the aria2 version or `static`:

- `aria2-linux-x86_64.tar.gz`
- `aria2-macos-arm64.tar.gz`
- `aria2-windows-x86_64.zip`

The release tag carries the aria2 version. Latest download URLs should use GitHub's `/releases/latest/download/` route with the fixed asset names.

## Validation

Changes to `.github/workflows/build.yml` should be validated by running the affected GitHub Actions job. Local checks are limited because the actual build happens in CI across Linux, Windows, and macOS runners.

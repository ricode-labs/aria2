# aria2 static binaries

**English** | [简体中文](README.zh.md) | [日本語](README.ja.md)

`aria2c` binaries built with GitHub Actions for Linux, Windows, and macOS. The Linux binary statically links application dependencies and dynamically links system OpenSSL 3, using the operating system's CA certificate store.

This repository is a release builder. The upstream aria2 source archive is downloaded during CI, built, tested with `make check` and `aria2c --version`, and published to GitHub Releases.

## Downloads

These links always resolve to the latest published release:

- Linux x86_64: https://github.com/ricode-labs/aria2/releases/latest/download/aria2-linux-x86_64.tar.gz
- macOS arm64: https://github.com/ricode-labs/aria2/releases/latest/download/aria2-macos-arm64.tar.gz
- Windows x86_64: https://github.com/ricode-labs/aria2/releases/latest/download/aria2-windows-x86_64.zip

The release tag contains the aria2 version, for example `aria2-1.37.0`.

## Release Assets

- `aria2-linux-x86_64.tar.gz`
- `aria2-macos-arm64.tar.gz`
- `aria2-windows-x86_64.zip`

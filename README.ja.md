# aria2 静的バイナリ

[English](README.md) | [简体中文](README.zh.md) | **日本語**

GitHub Actions で Linux、Windows、macOS 向けにビルドした `aria2c` バイナリです。Linux バイナリはアプリケーション依存関係を静的リンクし、システムの OpenSSL 3 と CA 証明書ストアを動的に使用します。

このリポジトリはリリースビルダーです。CI で upstream の aria2 ソースアーカイブをダウンロードし、ビルドしたうえで `make check` と `aria2c --version` によりテストし、GitHub Releases に公開します。

## ダウンロード

次のリンクは常に最新の公開リリースを指します：

- Linux x86_64: https://github.com/ricode-labs/aria2/releases/latest/download/aria2-linux-x86_64.tar.gz
- macOS arm64: https://github.com/ricode-labs/aria2/releases/latest/download/aria2-macos-arm64.tar.gz
- Windows x86_64: https://github.com/ricode-labs/aria2/releases/latest/download/aria2-windows-x86_64.zip

リリースタグには aria2 のバージョンが含まれます。例：`aria2-1.37.0`。

## リリース資産

- `aria2-linux-x86_64.tar.gz`
- `aria2-macos-arm64.tar.gz`
- `aria2-windows-x86_64.zip`

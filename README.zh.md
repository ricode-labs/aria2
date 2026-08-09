# aria2 静态二进制文件

[English](README.md) | **简体中文** | [日本語](README.ja.md)

使用 GitHub Actions 为 Linux、Windows 和 macOS 构建的 `aria2c` 二进制文件。Linux 二进制静态链接应用依赖，动态链接系统 OpenSSL 3，并使用操作系统的 CA 证书库。

本仓库是一个发布构建器。CI 会下载上游 aria2 源码包，完成构建，使用 `make check` 和 `aria2c --version` 进行测试，然后发布到 GitHub Releases。

## 下载

以下链接始终指向最新发布版本：

- Linux x86_64: https://github.com/ricode-labs/aria2/releases/latest/download/aria2-linux-x86_64.tar.gz
- macOS arm64: https://github.com/ricode-labs/aria2/releases/latest/download/aria2-macos-arm64.tar.gz
- Windows x86_64: https://github.com/ricode-labs/aria2/releases/latest/download/aria2-windows-x86_64.zip

发布标签包含 aria2 版本号，例如 `aria2-1.37.0`。

## 发布资产

- `aria2-linux-x86_64.tar.gz`
- `aria2-macos-arm64.tar.gz`
- `aria2-windows-x86_64.zip`

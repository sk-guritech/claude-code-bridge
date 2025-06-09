# claude-code-bridge

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Claude Codeの端末制御を拡張するexpectスクリプト - TCPソケット経由でのリモート制御とリアルタイムログ出力を実現

[English README](README_en.md)

## 概要

`claude-code-bridge`は、Claude Codeの対話型インタフェースを維持しながら、以下の機能を提供するexpectスクリプトです：

- 🖥️ **端末ログ出力** - リアルタイムで端末内容をファイルに記録
- 🌐 **TCP経由の制御** - ネットワーク経由でClaude Codeに入力を送信
- 🔄 **プロセス間通信** - 他のツールやスクリプトとの連携が可能
- ⌨️ **通常操作の維持** - 標準的な対話的操作も同時に利用可能

## 動機

devcontainer環境でClaude Codeを使用する際の以下の課題を解決します：

- 長時間タスク中の入力待ちを見逃してしまう問題
- 複数プロジェクトでの入力待ち状態の把握困難
- TTY依存の入力方式による制約

## インストール

### 前提条件

- `expect` コマンド
- `claude` (Claude Code CLI)

### セットアップ

```bash
# リポジトリのクローン
git clone https://github.com/YOUR_USERNAME/claude-code-bridge.git
cd claude-code-bridge

# 実行権限の付与
chmod +x claude-code-bridge.exp
```

## 使い方

### 基本的な起動

```bash
# デフォルト設定（ポート9999）で起動
./claude-code-bridge.exp

# カスタムポートで起動
./claude-code-bridge.exp 8080
```

### 端末ログの監視

別のターミナルで以下を実行：

```bash
tail -f /tmp/claude-code-terminal.log
```

### リモートコマンドの送信

```bash
# テキストを入力してEnterキーを送信
echo "send hello world" > /dev/tcp/localhost/9999

# Enterキーのみを送信
echo "enter" > /dev/tcp/localhost/9999

# 上矢印キー
echo "up" > /dev/tcp/localhost/9999

# 下矢印キー
echo "down" > /dev/tcp/localhost/9999
```



## ライセンス

[MIT License](LICENSE)

## Author

**Sakaguchi Ryo**  
📧 sakaguchi@sk-techfirm.com

- GitHub: [@sk-guritech](https://github.com/sk-guritech)

## 謝辞

このプロジェクトは、devcontainer環境でClaude Codeをより効率的に使用したいという需要から生まれました。

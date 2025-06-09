# claude-code-bridge

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

An expect script that extends Claude Code terminal control - Enables remote control via TCP socket and real-time log output

[日本語 README](README_ja.md)

## Overview

`claude-code-bridge` is an expect script that maintains Claude Code's interactive interface while providing the following features:

- 🖥️ **Terminal Logging** - Records terminal content to a file in real-time
- 🌐 **TCP-based Control** - Send input to Claude Code over the network
- 🔄 **Inter-process Communication** - Enables integration with other tools and scripts
- ⌨️ **Preserved Normal Operation** - Standard interactive operations remain available

## Motivation

This script solves the following challenges when using Claude Code in devcontainer environments:

- Missing input prompts during long-running tasks
- Difficulty tracking input-waiting states across multiple projects
- Limitations of TTY-dependent input methods

## Installation

### Prerequisites

- `expect` command
- `claude` (Claude Code CLI)

### Setup

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/claude-code-bridge.git
cd claude-code-bridge

# Grant execution permissions
chmod +x claude-code-bridge.exp
```

## Usage

### Basic Launch

```bash
# Launch with default settings (port 9999)
./claude-code-bridge.exp

# Launch with custom port
./claude-code-bridge.exp 8080
```

### Monitor Terminal Logs

In another terminal:

```bash
tail -f /tmp/claude-code-terminal.log
```

### Send Remote Commands

```bash
# Input text and send Enter key
echo "send hello world" > /dev/tcp/localhost/9999

# Send Enter key only
echo "enter" > /dev/tcp/localhost/9999

# Up arrow key
echo "up" > /dev/tcp/localhost/9999

# Down arrow key
echo "down" > /dev/tcp/localhost/9999
```

## License

[MIT License](LICENSE)

## Author

**Sakaguchi Ryo**  
📧 sakaguchi@sk-techfirm.com

- GitHub: [@sk-guritech](https://github.com/sk-guritech)

## Acknowledgments

This project was born from the need to use Claude Code more efficiently in devcontainer environments.

# OOO Copilot Agent Guide

This is the single top-level guide to use Ouroboros from any project folder when your runtime is GitHub Copilot.

## Scope

- Runtime in this guide: Copilot only
- Ignore Kiro, Codex, OpenCode, and other runtime guides unless you intentionally switch runtime
- Works across any repository after one global install

## Read These First

1. [docs/getting-started.md](docs/getting-started.md)
2. [docs/runtime-guides/copilot.md](docs/runtime-guides/copilot.md)
3. [docs/cli-reference.md](docs/cli-reference.md)

Optional:

1. [docs/config-reference.md](docs/config-reference.md)
2. [docs/platform-support.md](docs/platform-support.md)

## One-Time Machine Setup

```bash
gh auth login
pipx install 'ouroboros-ai[mcp]'
ouroboros setup --runtime copilot
```

If pipx is not available, use uv tool install or pip install:

```bash
uv tool install 'ouroboros-ai[mcp]'
# or
pip install 'ouroboros-ai[mcp]'
```

## Any Project Startup Checklist

Run these inside the target project folder:

```bash
command -v ooo || command -v ouroboros
ouroboros --version
ouroboros status health
```

If command lookup fails, add user bin path and restart shell:

```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

Optional shortcut if missing:

```bash
ln -sfn "$HOME/.local/bin/ouroboros" "$HOME/.local/bin/ooo"
```

## How To Instruct Copilot Agent In Another Folder

Use this prompt template:

```text
Before starting, follow only Copilot runtime docs:
1) docs/getting-started.md
2) docs/runtime-guides/copilot.md
3) docs/cli-reference.md
Do not use Kiro/Codex/OpenCode paths.
Verify command availability with:
- command -v ooo || command -v ouroboros
- ouroboros status health
Then continue task execution.
```

## Command Usage Model

- In normal terminal: use ouroboros commands
- In agent session that supports skills: use ooo commands
- If ooo is unavailable, use ouroboros equivalent commands

Examples:

```bash
# Terminal workflow
ouroboros init start "Describe your goal" --llm-backend copilot
ouroboros auto "Describe your goal"
```

```text
# Agent session workflow
ooo interview "Describe your goal"
ooo auto "Describe your goal"
```

## Copilot Chat In VS Code

1. Open target repo in VS Code
2. Use Copilot Chat Agent mode for terminal-execution requests
3. Approve command execution prompts

Suggested request:

```text
Run ouroboros status health in terminal and summarize the result.
```

## Troubleshooting

- Model not available:
  - Re-run: ouroboros setup --runtime copilot
  - Refresh discovered model list
- MCP not connected in Copilot session:
  - Restart Copilot session after setup
- Setup blocks in automation:
  - Use: ouroboros setup --runtime copilot --non-interactive
- Python version issue:
  - Ensure Python 3.12+

## Quick Reference

```bash
ouroboros setup --runtime copilot
ouroboros status health
ouroboros config show
ouroboros init start "Your goal" --llm-backend copilot
ouroboros auto "Your goal"
```

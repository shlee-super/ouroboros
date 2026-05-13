<p align="right">
  <strong>English</strong> | <a href="./README.ko.md">한국어</a> | <a href="./README.zh-CN.md">简体中文</a>
</p>

<p align="center">
  <br/>
  ◯ ─────────── ◯
  <br/><br/>
  <img src="./docs/images/ouroboros.png" width="520" alt="Ouroboros">
  <br/><br/>
  <strong>O U R O B O R O S</strong>
  <br/><br/>
  ◯ ─────────── ◯
  <br/>
</p>

<p align="center">
  <strong>Stop prompting. Start specifying.</strong>
  <br/>
  <sub>Agent OS for replayable, specification-first AI coding workflows</sub>
</p>

<p align="center">
  <a href="https://pypi.org/project/ouroboros-ai/"><img src="https://img.shields.io/pypi/v/ouroboros-ai?color=blue" alt="PyPI"></a>
  <a href="https://github.com/Q00/ouroboros/actions/workflows/test.yml"><img src="https://img.shields.io/github/actions/workflow/status/Q00/ouroboros/test.yml?branch=main" alt="Tests"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-green" alt="License"></a>
</p>

<p align="center">
  <a href="#quick-start">Quick Start</a> ·
  <a href="#use-it-from-any-project">Any Project</a> ·
  <a href="#vscode-copilot-chat-terminal-flow">VS Code Copilot Chat</a> ·
  <a href="#common-commands">Commands</a> ·
  <a href="#troubleshooting">Troubleshooting</a>
</p>

**Turn a vague idea into a verified, working codebase.**

Ouroboros is an Agent OS for AI coding: a local-first runtime layer that turns non-deterministic agent work into a replayable, observable, policy-bound execution contract.

It replaces ad-hoc prompting with a structured workflow: interview, seed, execute, evaluate, evolve.

---

## Quick Start

### 1) Install

```bash
curl -fsSL https://raw.githubusercontent.com/Q00/ouroboros/main/scripts/install.sh | bash
```

Alternative installs:

```bash
pip install ouroboros-ai
pip install 'ouroboros-ai[mcp]'
pipx install 'ouroboros-ai[mcp]'
uv tool install 'ouroboros-ai[mcp]'
```

### 2) Verify

```bash
ouroboros --version
ouroboros status health
```

### 3) Configure Runtime

```bash
ouroboros setup
```

Examples:

```bash
ouroboros setup --runtime copilot
ouroboros setup --runtime codex
ouroboros setup --runtime claude
```

### 4) Start Your First Workflow

Terminal flow:

```bash
ouroboros init start "Build a task management CLI"
```

Agent-session flow:

```text
> ooo interview "Build a task management CLI"
```

---

## Use It From Any Project

You do not need to install Ouroboros separately per repository. One global install works across projects.

Recommended baseline checks in a project terminal:

```bash
command -v ouroboros
ouroboros --version
```

If command lookup fails after install, add user bin path to your shell startup file:

```bash
export PATH="$HOME/.local/bin:$PATH"
```

Then restart the shell and verify again.

Optional shortcut command:

```bash
ln -sfn "$HOME/.local/bin/ouroboros" "$HOME/.local/bin/ooo"
```

---

## VS Code Copilot Chat Terminal Flow

Use this when you want Copilot Chat to execute `ooo` or `ouroboros` in the integrated terminal.

### One-Time Setup

```bash
gh auth login
pipx install 'ouroboros-ai[mcp]'
ouroboros setup --runtime copilot
```

### Operational Checklist

1. Open any repository in VS Code.
2. In the integrated terminal, verify commands:

```bash
command -v ooo || command -v ouroboros
ouroboros status health
```

3. In Copilot Chat, use Agent mode for terminal-execution requests.
4. Approve execution prompts when asked.

Example prompt to Copilot Chat:

```text
Run `ouroboros status health` in terminal and summarize the output.
```

Non-interactive setup is available for automation or CI:

```bash
ouroboros setup --runtime copilot --non-interactive
```

Copilot runtime guide: [docs/runtime-guides/copilot.md](./docs/runtime-guides/copilot.md)

---

## Common Commands

Terminal commands:

```bash
ouroboros --help
ouroboros setup
ouroboros init start "Describe your project goal"
ouroboros auto "Describe your project goal"
ouroboros config show
ouroboros status
ouroboros status health
```

Agent-session commands:

```text
> ooo help
> ooo interview "Describe your project goal"
> ooo auto "Describe your project goal"
> ooo status
```

Full reference: [docs/cli-reference.md](./docs/cli-reference.md)

---

## Configuration And Data

Default directory: `~/.ouroboros/`

- `config.yaml`: runtime and model configuration
- `credentials.yaml`: key storage (chmod 600 recommended)
- `ouroboros.db`: event store
- `seeds/`: generated seed specs
- `logs/`: runtime logs

Config docs: [docs/config-reference.md](./docs/config-reference.md)

---

## Troubleshooting

| Issue | Check | Fix |
| :--- | :--- | :--- |
| `ouroboros: command not found` | `echo $PATH` and `command -v ouroboros` | Add `~/.local/bin` to PATH and restart shell |
| Python version error | `python3 --version` | Use Python 3.12 or newer |
| Copilot runtime model errors | `ouroboros config show` | Re-run `ouroboros setup --runtime copilot` |
| Interactive setup blocks automation | Prompt is waiting for input | Use `--non-interactive` |
| MCP integration not visible | Runtime config and client config mismatch | Re-run `ouroboros setup --runtime <runtime>` |

Platform support: [docs/platform-support.md](./docs/platform-support.md)

Uninstall: [UNINSTALL.md](./UNINSTALL.md)

---

## Learn More

- Getting started: [docs/getting-started.md](./docs/getting-started.md)
- Runtime guides: [docs/runtime-guides/](./docs/runtime-guides/)
- Seed authoring: [docs/guides/seed-authoring.md](./docs/guides/seed-authoring.md)
- Architecture: [docs/architecture.md](./docs/architecture.md)

---

## License

MIT. See [LICENSE](./LICENSE).

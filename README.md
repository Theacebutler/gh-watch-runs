# gh-watch-runs

Interactive TUI to browse and watch GitHub Actions workflow runs.

Combines `gh`, `jq`, and `fzf-tmux` for a searchable list of recent runs in a tmux popup with a detail preview pane. Selecting a run streams its live logs via `gh run watch`.

## Prerequisites

- [gh](https://cli.github.com/) — GitHub CLI (authenticated via `gh auth login`)
- [jq](https://jqlang.github.io/jq/) — JSON processor
- [fzf](https://github.com/junegunn/fzf) — fuzzy finder (provides `fzf-tmux`)
- [tmux](https://github.com/tmux/tmux) — terminal multiplexer

## Installation

```bash
git clone https://github.com/<user>/gh-watch-runs.git
# optionally add to PATH
ln -s "$PWD/gh-watch-runs/gh-watch-runs" ~/.local/bin/
```

## Usage

```bash
gh-watch-runs
```

Run from inside any git repository connected to GitHub. No arguments needed.

## How it works

1. Verifies `gh` is installed and authenticated.
2. Lists up to 50 recent workflow runs via `gh run list --json`.
3. Pipes into `fzf-tmux` for interactive selection with a preview panel showing title, branch, status, conclusion, event, URL, and run ID.
4. On selection, calls `gh run watch <databaseId>` to stream live logs.

## License

MIT

---
name: setup
description: Install the Expert LSP binary for the expert-lsp plugin
disable-model-invocation: true
---

# Install Expert LSP

Check if Expert is installed, and install it if not.

## Steps

1. Check if `expert` is in PATH: `which expert`
2. If found, check version: `expert --version`
3. If NOT found, install via one of these methods:

### Via escript (recommended)
```bash
mix escript.install hex expert_lsp
```

### Via Burrito release (single binary)
Download the latest release from https://github.com/elixir-tools/expert/releases and place it in your PATH.

### Via asdf
```bash
asdf plugin add expert
asdf install expert latest
asdf global expert latest
```

4. Verify: `expert --version`
5. Restart Claude Code to pick up the LSP server.

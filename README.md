# expert-lsp — Elixir Code Intelligence for Claude Code

A Claude Code plugin that connects the [Expert LSP](https://expert-lsp.org) — the official unified Elixir language server — to give Claude real-time code intelligence while working on Elixir projects.

## What Claude gains

- **Auto-diagnostics**: After every file edit, Expert analyzes changes and reports errors, warnings, and missing imports. Claude sees issues immediately and fixes them in the same turn.
- **Code navigation**: Go to definition, find references, hover for type info, list symbols — precise navigation instead of grep-based search.

## Requirements

- **Claude Code** v1.0.33+
- **Expert LSP** binary installed and in your `$PATH`

## Install the plugin

```bash
# From the Claude Code CLI
claude plugin install expert-lsp@<marketplace>

# Or load locally for development
claude --plugin-dir /path/to/expert-lsp
```

## Install Expert LSP

The plugin configures the connection but doesn't include the server binary. Install Expert:

```bash
# Via escript (recommended)
mix escript.install hex expert_lsp

# Via Burrito release (single binary)
# Download from https://github.com/elixir-tools/expert/releases

# Via asdf
asdf plugin add expert && asdf install expert latest && asdf global expert latest
```

Verify: `expert --version`

## Supported file types

| Extension | Language ID |
|-----------|------------|
| `.ex`     | elixir     |
| `.exs`    | elixir     |
| `.heex`   | elixir     |

## How it works

This plugin provides an `.lsp.json` configuration that tells Claude Code how to connect to Expert via stdio transport. Expert runs as a subprocess, analyzing your project files and providing real-time diagnostics and navigation.

## Expert LSP vs ElixirLS

Expert is the [official unified Elixir language server](https://elixir-lang.org/blog/2024/08/15/welcome-elixir-language-server-team/), created by the Elixir core team by merging the three previous implementations (ElixirLS, Lexical, Next LS). It's built on the Lexical codebase with Next LS components for single-binary releases and protocol abstraction.

Expert is currently in release candidate status. If you encounter issues, you can fall back to the `elixir-ls-lsp` plugin which uses the legacy ElixirLS server.

## Configuration

The plugin uses sensible defaults. Expert is started with `--stdio` transport and will auto-restart up to 3 times if it crashes.

## License

MIT

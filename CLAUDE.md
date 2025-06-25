# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a pre-commit hooks collection for Elixir projects. It provides reusable hooks that can be integrated into any Elixir project using the pre-commit framework.

## Architecture

The repository has a minimal structure focused on providing pre-commit hook definitions:

- `.pre-commit-hooks.yaml` - Defines available hooks for use by other projects
- Currently provides two hooks:
  - `mix-format`: Formats Elixir files with mix format
  - `mix-credo`: Runs Credo static analysis in strict mode

## Development Notes

### Adding New Hooks

When adding new hooks to `.pre-commit-hooks.yaml`:
- Use `language: system` as hooks rely on system-installed Elixir/Mix
- Match Elixir files with pattern `\.exs?$`
- Ensure the entry command returns non-zero exit code on failure

### Testing Hooks

To test hooks work correctly:
1. Create a test Elixir project
2. Add this repository to the project's `.pre-commit-config.yaml`
3. Run `pre-commit run --all-files`

### Common Tasks

- **Add a new hook**: Edit `.pre-commit-hooks.yaml` to add new hook definitions
- **Update existing hooks**: Modify the entry command or file patterns in `.pre-commit-hooks.yaml`

## Important Context

- This is not an Elixir application - it's a configuration repository for pre-commit
- No Mix project structure or dependencies needed
- Hooks assume Mix and required tools (format, credo) are available on the system where they run
# AGENTS.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Overview

kubefzf is a collection of bash scripts providing fzf-based interactive menus for common Kubernetes operations. The scripts replace or enhance typical kubectl workflows with fuzzy-find selection.

## Requirements

- `fzf` - fuzzy finder (core dependency)
- `kubectl` - configured with cluster access
- `jq` - JSON processing
- zsh or bash shell

## Scripts

- `podadmin` - Pod management: exec, logs, describe, restart, delete, set image, rollout restart
- `svcadmin` - Service management: port-forward, edit, describe, view endpoints
- `select_pod` - Simple pod selector helper

## Running

Scripts are executable and run directly:

```bash
./podadmin
./svcadmin
```

## Architecture

Each script follows the same pattern:
1. Fetch Kubernetes resources as JSON via `kubectl get -o json`
2. Store data in exported shell variables (`POD_DATA`, `SERVICES_DATA`) for fzf preview access
3. Use fzf with `--preview` to display resource details
4. Present action menu after selection
5. Execute kubectl commands based on user choice

Key fzf bindings used across scripts:
- `ctrl-d` - describe resource
- `ctrl-y` - JSON view
- `ctrl-u/e` - scroll preview
- `ctrl-f/b` - page preview

## Notes for Development

- Preview commands run in fzf subshells, requiring `export -f` for function access
- JSON data is exported to environment variables to avoid repeated API calls
- Uses `jq` to filter `.metadata.managedFields` from output for cleaner display

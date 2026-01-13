# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

OpenCoWork is an open-source implementation of Claude CoWork - a local-first AI collaborative assistant with sandboxed execution, built on the Claude Agent SDK.

## Architecture

Three-layer architecture:

1. **UI Layer** (Tauri/Electron/Web) - Workspace authorization, task queue UI, permission dialogs, file diff preview
2. **OpenCoWork Engine** (Headless Core) - Task scheduler, run manager, permission/policy layer, checkpoint handling, plugin/skill loader, MCP connector lifecycle
3. **Sandbox/Runner** (Per-Run Isolation) - Claude Agent SDK runtime, workspace mounts, network proxy, process isolation (bwrap + seccomp)

### Cross-Platform Sandboxing

- **macOS**: Apple Virtualization Framework (VZVirtualMachine) + bwrap
- **Windows**: WSL2 / Hyper-V + bwrap
- **Linux**: bwrap + seccomp directly

All network traffic routes through host-side proxy for allowlisting and auditing.

## Key Design Principles

- Agent SDK as the kernel - build on Claude Agent SDK, don't rewrite the agent loop
- Local-first by default - no mandatory cloud dependency
- Security by default - directory boundaries, permission approval, rollback, audit trails
- Outputs-first mode - generated files go to outputs directory by default

## Links

- Website: https://openco.work
- GitHub: https://github.com/opencowork-ai/opencowork

<div align="center">

# OpenCoWork

**Open-source Claude CoWork for everyone.**

An AI collaborative assistant with sandboxed execution, built on Claude Agent SDK.

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/opencowork-ai/opencowork/pulls)

[Website](https://openco.work) · [Documentation](https://openco.work/docs) · [Roadmap](https://openco.work/roadmap)

</div>

---

## Why OpenCoWork?

[Claude CoWork](https://claude.com/blog/cowork-research-preview) is powerful but closed-source. We're building an open alternative that:

- 🔒 **Runs locally** — Your data never leaves your machine
- 🛡️ **Sandboxed execution** — VM + bwrap isolation like the original
- ↩️ **One-click rollback** — Automatic checkpoints, instant recovery
- 🔌 **Extensible** — Skills, MCP connectors, plugins

## Architecture

```
┌───────────────────────────────────────────┐
│              UI Layer                     │
│       Tauri / Electron / Web              │
└─────────────────┬─────────────────────────┘
                  │
┌─────────────────▼─────────────────────────┐
│         OpenCoWork Engine                 │
│  Task queue · Permissions · Checkpoints   │
└─────────────────┬─────────────────────────┘
                  │
┌─────────────────▼─────────────────────────┐
│        Sandbox (Per-Run)                  │
│  Claude Agent SDK · bwrap · Network proxy │
└───────────────────────────────────────────┘
```

### Cross-Platform Sandboxing

| Platform | Method |
|:---------|:-------|
| macOS | Apple Virtualization Framework + bwrap |
| Windows | WSL2 / Hyper-V + bwrap |
| Linux | bwrap + seccomp |

## Status

> 🚧 **Early Development** — Star to follow progress

- [x] Architecture design
- [ ] Engine core
- [ ] Sandbox providers
- [ ] Desktop app

## Contributing

We welcome contributions! Check [issues](https://github.com/opencowork-ai/opencowork/issues) for good first tasks.

## License

[Apache 2.0](LICENSE)

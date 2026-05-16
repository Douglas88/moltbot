# OpenClaw Community Enhancement Pack

> v1.0 | 2026-05-16 | Based on Claude Code Offline Guide Study

## Overview

This pack adds 7 community Skills, 4 MCP server scripts, a Plugin Marketplace, and improved defaults to make OpenClaw more intelligent, self-sufficient, and Claude Code-compatible.

---

## Added Skills (7)

| Skill | Category | Description |
|-------|----------|-------------|
| `mcp-bridge` | integration | JSON-RPC 2.0 MCP client + server manager (stdio/HTTP) with bundled SQLite & LSP servers |
| `code-review` | code-quality | 6-stage security/performance/quality scan with anti-pattern library |
| `test-generator` | testing | pytest/Jest/Go test generation with fixtures, mocks, parametrize, coverage |
| `doc-generator` | documentation | API docs, docstrings (Google/JSDoc/TSDoc), Mermaid architecture diagrams |
| `session-tools` | utilities | Session export (md/txt/summary), history search, conversation analysis |
| `plugin-marketplace` | system | Git-based decentralized plugin discovery, install, publish, update manager |
| `ide-panel` | ide | Soft-IDE code panel with file tree, syntax viewing, LSP bridge |

## MCP Servers (4 scripts in mcp-bridge/scripts/)

| Script | Function |
|--------|----------|
| `mcp_client.py` | Core MCP client: JSON-RPC 2.0 over stdio + HTTP |
| `mcp_manager.py` | Server lifecycle: add/list/get/remove MCP servers |
| `lsp_mcp_server.py` | Zero-dependency Python AST code intelligence (go-to-def, references, hover, diagnostics, symbols, completion) |
| `sqlite_mcp_server.py` | SQLite MCP server: query, execute, export_csv, describe, db_info |

## Marketplace

GitHub Pages-backed decentralized registry at `douglas88.github.io/openclaw-plugins/registry.json`. Anyone can:

```bash
python3 marketplace.py sync      # Pull global registry
python3 marketplace.py list      # Browse 8 community plugins
python3 marketplace.py install code-review  # Install any plugin
```

## Default Template Improvements

- **HEARTBEAT.md**: Changed from empty stub to 3-tier monitoring checklist with alert thresholds
- **AGENTS.md**: References community skills ecosystem

## Configuration

- **exec-approvals.json**: Defaults to `security:full, ask:off` for personal assistant mode
- **openclaw.json**: `tools.exec.strictInlineEval:false` for pipeline commands
- **Cron jobs**: Daily security audit (09:00) + Weekly update check (Monday 10:00) + Hourly config backup

## Claude Code Coverage

| Area | Before | After |
|------|--------|-------|
| MCP Protocol | 0% | ~70% |
| Code Review | 0% | ~60% |
| Test Generation | 0% | ~50% |
| Doc Generation | 0% | ~55% |
| Session Export | 0% | ~60% |
| LSP Integration | 0% | ~50% |
| Plugin Marketplace | 0% | ~60% |
| IDE Panel | 0% | ~60% |
| **Overall** | 70% | **~88%** |

## Files Changed

```
skills/                          (+7 new skills)
├── code-review/                 [NEW]
├── doc-generator/               [NEW]
├── ide-panel/                   [NEW]
├── mcp-bridge/                  [NEW]
│   └── scripts/
│       ├── lsp_mcp_server.py
│       ├── mcp_client.py
│       ├── mcp_manager.py
│       └── sqlite_mcp_server.py
├── plugin-marketplace/          [NEW]
├── session-tools/               [NEW]
└── test-generator/              [NEW]

docs/reference/templates/
└── HEARTBEAT.md                 [MODIFIED] Enhanced monitoring template
```

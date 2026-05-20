<div align="center">

# BitCode Framework

**Modular low-code ERP platform**

JSON is the source code. Go is the runtime. Modules are the packaging.

[![Go](https://img.shields.io/badge/Go-1.24+-00ADD8?logo=go)](https://go.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?logo=typescript)](https://www.typescriptlang.org/)
[![Rust](https://img.shields.io/badge/Rust-1.80+-000000?logo=rust)](https://www.rust-lang.org/)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

</div>

---

## What is BitCode?

BitCode is a JSON-driven platform for building business applications. You define models, APIs, processes, views, and workflows in JSON — the Go engine reads them at runtime and produces a fully functional application. Inspired by Odoo, Frappe, and NocoBase.

**Write once in JSON. Run anywhere Go runs.**

## Repositories

### Core Runtime

| Repo | Description |
|------|-------------|
| [go-json](https://github.com/bitcode-framework/go-json) | General-purpose JSON/JSONC programming language engine. 20 step types, 135+ built-in functions, lambda expressions, pattern matching, structs, I/O modules, web server. Embeddable in Go. |
| [go-json-runtimes](https://github.com/bitcode-framework/go-json-runtimes) | Script runtime engines for go-json. Goja (JS), QuickJS (JS ES2023), Yaegi (Go), WASM (wazero), Node.js, Python. Opt-in, zero heavy pulls. |

### UI Layer

| Repo | Description |
|------|-------------|
| [ui-stencil-web-components](https://github.com/bitcode-framework/ui-stencil-web-components) | 119 Stencil Web Components for enterprise applications. Fields, charts (ECharts), data tables, layout, dialogs, media viewers. Framework-agnostic. Works in plain HTML. |
| [ui-tauri](https://github.com/bitcode-framework/ui-tauri) | Tauri 2.0 native shell. Wraps Stencil components into desktop (Win/Mac/Linux) and mobile (iOS/Android) apps with offline SQLite, sync, and native capabilities. |

### Full Platform

| Repo | Description |
|------|-------------|
| [bitcode](https://github.com/bitcode-framework/bitcode) | Complete monorepo — Go engine + components + Tauri shell. The source of truth for all packages. |

### Samples & Tools

| Repo | Description |
|------|-------------|
| [erp](https://github.com/bitcode-framework/erp) | Sample ERP application (CRM + HRM) built with BitCode. |
| [pg_fast_data_transfer](https://github.com/bitcode-framework/pg_fast_data_transfer) | Fast PostgreSQL data transfer utility. |

## Architecture

```
JSON Definitions (models, APIs, views, workflows)
        |
  BitCode Go Engine
  ├── Compiler — JSON → AST
  ├── Runtime — Process executor, agents, workflow engine
  ├── go-json — Embedded JSON programming language
  ├── go-json-runtimes — Python, JS, Go script orchestration
  └── HTTP Server — Fiber v2, REST, GraphQL, WebSocket
        |
  Stencil Web Components (119 components)
        |
  Tauri Native Shell (desktop + mobile)
```

## Tech Stack

| Layer | Technology |
|-------|------------|
| Runtime | Go 1.24+, Fiber v2, GORM |
| Scripting | go-json (JSON/JSONC programming language), expr-lang |
| Database | SQLite, PostgreSQL, MySQL, MongoDB |
| Components | Stencil.js, ECharts, Tiptap, CodeMirror, Leaflet |
| Native Shell | Tauri 2.0 (Rust) |
| Plugins | TypeScript, Python via JSON-RPC |

## Key Features

- **JSON-driven development** — Models, APIs, processes, views, workflows — all defined in JSON
- **Auto-CRUD** — One JSON file = full REST API with pagination, search, filtering
- **GraphQL + WebSocket** — Auto-generated from model definitions
- **RBAC security** — JWT auth, field-level encryption (AES-256-GCM), audit logging, 2FA
- **Workflow engine** — State machines with permission-gated transitions
- **Process engine** — 14 step types, DAG executor, parallel execution
- **go-json scripting** — Standalone JSON programming language with 135+ functions
- **Multi-database** — SQLite, PostgreSQL, MySQL, MongoDB
- **Offline mode** — Local SQLite, outbox pattern, delta sync, conflict resolution
- **119 Web Components** — Standalone, framework-agnostic, themed, i18n (11 languages)
- **Desktop + Mobile** — Tauri 2.0 native shell with barcode scanning, biometric auth

## Quick Start

```bash
# Install the CLI
go install github.com/bitcode-framework/bitcode/cmd/bitcode@latest

# Run (SQLite, zero config)
bitcode serve
```

Server starts at `http://localhost:8080`. SQLite database created automatically.

## License

All repositories are [MIT licensed](https://opensource.org/licenses/MIT).

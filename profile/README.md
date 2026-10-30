<div align="center">

# BitCode Framework

**AI-Native, Metadata-Driven Application Framework**

Build any application — ERP, CRM, HRM, inventory, project management, or custom business logic — from JSON definitions.

> **Work in Progress** — Actively developed. Not production-ready yet.

[![Go](https://img.shields.io/badge/Go-1.24+-00ADD8?logo=go)](https://go.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?logo=typescript)](https://www.typescriptlang.org/)
[![Rust](https://img.shields.io/badge/Rust-1.80+-000000?logo=rust)](https://www.rust-lang.org/)
[![Status](https://img.shields.io/badge/status-WIP-yellow.svg)]()

</div>

---

## What is BitCode?

BitCode is a modular, metadata-driven framework that reads JSON definitions and produces running applications. Define your data models, APIs, business processes, views, and workflows in JSON — the Go engine interprets them at runtime.

It is **not just an ERP**. BitCode is a general-purpose application framework that happens to ship with ERP-grade modules. Use it for:

- **ERP** — Accounting, inventory, procurement, manufacturing
- **CRM** — Contacts, deals, pipeline, activities
- **HRM** — Employees, attendance, payroll, recruitment
- **Project Management** — Tasks, sprints, timesheets
- **Custom Business Apps** — Any domain-specific workflow

Inspired by Odoo, Frappe, and NocoBase. Designed for extensibility from day one.

**JSON is the source code. Go is the runtime. Modules are the packaging.**

## How It Works

```
JSON Metadata (models, APIs, views, workflows, permissions)
        |
  BitCode Engine (Go)
  |-- Compiler      JSON -> validated AST
  |-- Runtime       Process executor, DAG engine, agents, workflow
  |-- go-json       Embedded JSON/JSONC programming language
  |-- Security      RBAC, record rules, field-level encryption, audit log
  `-- Server        REST, GraphQL, WebSocket, SSR templates
        |
  UI Schema         Framework-neutral schema types + reactive engine
        |
  Renderers         React/Vue/React Native, Flutter, Web Components
        |
  Tauri Native Shell (desktop + mobile, offline-first)
```

## Live Demos

Everything below runs in the browser. No install, no signup.

| Demo | What you can do |
|------|-----------------|
| **[ui — component showcase](https://bitcode-framework.github.io/ui/)** | Browse the cross-framework component library, rendered live from Mitosis sources |
| **[ui-flutter — Flutter showcase](https://bitcode-framework.github.io/ui-flutter/)** | Same schema and tokens rendered by native Flutter widgets |
| **[ui-schema — reactive engine](https://bitcode-framework.github.io/ui-schema/)** | Edit a form and watch declared reactions recompute |
| **[go-json — language playground](https://bitcode-framework.github.io/go-json/)** | Write and run JSON programs; the engine is compiled to WebAssembly |
| **[expr-js — expression playground](https://bitcode-framework.github.io/expr-js/)** | Evaluate expr-lang expressions with the TypeScript port |
| **[go-json-runtimes — script bridge](https://bitcode-framework.github.io/go-json-runtimes/)** | Run a go-json program that calls into JavaScript through a `script:` import |
| **[ui-web-components — gallery (deprecated)](https://bitcode-framework.github.io/ui-web-components/demo/)** | The original Stencil component gallery, kept for reference while users migrate |

## Repositories

### Application Platform

| Repo | Description |
|------|-------------|
| [bitcode](https://github.com/bitcode-framework/bitcode) | Full monorepo — Go engine, UI packages, Tauri shell. Source of truth. |

### UI Layer

The UI layer is split by responsibility: one source of truth for schema, and one renderer per platform.

| Repo | Description | Demo |
|------|-------------|------|
| [ui-schema](https://github.com/bitcode-framework/ui-schema) | Canonical UI schema types plus the headless, framework-neutral reactive engine. No DOM dependency. | [demo](https://bitcode-framework.github.io/ui-schema/) |
| [ui](https://github.com/bitcode-framework/ui) | Cross-framework components built on Mitosis, compiled to React, Vue, React Native, and Web Components. | [demo](https://bitcode-framework.github.io/ui/) |
| [ui-flutter](https://github.com/bitcode-framework/ui-flutter) | Contract-driven Flutter widgets and schema renderer, ported from the same schema and tokens. | [demo](https://bitcode-framework.github.io/ui-flutter/) |
| [ui-tauri](https://github.com/bitcode-framework/ui-tauri) | Tauri 2.0 native shell: desktop (Windows/macOS/Linux) and mobile (iOS/Android), offline SQLite, native bridge. | *(native app — no web demo)* |
| [ui-web-components](https://github.com/bitcode-framework/ui-web-components) | **Deprecated.** The original Stencil-based Web Components set. Kept for reference; migrate to `ui`, `ui-schema`, and `ui-flutter`. | [demo](https://bitcode-framework.github.io/ui-web-components/demo/) |

> **`ui-web-components` is deprecated.** The Stencil-based component set has been superseded by
> [ui](https://github.com/bitcode-framework/ui), [ui-schema](https://github.com/bitcode-framework/ui-schema),
> and [ui-flutter](https://github.com/bitcode-framework/ui-flutter). Existing users should migrate.

### Language & Runtime

| Repo | Description | Demo |
|------|-------------|------|
| [go-json](https://github.com/bitcode-framework/go-json) | Standalone JSON/JSONC programming language engine. 20 step types, 200+ built-in functions, structs, lambdas, I/O modules, built-in web server. | [playground](https://bitcode-framework.github.io/go-json/) |
| [go-json-runtimes](https://github.com/bitcode-framework/go-json-runtimes) | Script runtime engines for go-json: goja, QuickJS, Yaegi, WASM, Node.js, Python. Opt-in, zero heavy pulls. | [playground](https://bitcode-framework.github.io/go-json-runtimes/) |
| [expr-js](https://github.com/bitcode-framework/expr-js) | TypeScript port of [expr-lang/expr](https://github.com/expr-lang/expr) v1.17.8 — the expression engine behind go-json and the UI layer. | [playground](https://bitcode-framework.github.io/expr-js/) |

## Architecture at a Glance

| Concern | Approach |
|---------|----------|
| **Data** | Models defined in JSON, auto-migrated. UUID primary keys throughout. |
| **Logic** | Processes (DAG + linear), workflows (state machines), and go-json scripts |
| **API** | REST, GraphQL, and WebSocket generated from the same model definitions |
| **UI** | One schema, many renderers — React/Vue/RN, Flutter, Web Components |
| **Security** | Group-based permissions, record rules, field-level encryption, audit log |
| **Offline** | Tauri shell with local SQLite, outbox, and sync with conflict resolution |
| **Native** | Desktop + mobile via Tauri, barcode scanning, biometric auth, push notifications |
| **Multi-DB** | SQLite, PostgreSQL, MySQL, MongoDB |

## Tech Stack

| Layer | Technology |
|-------|------------|
| Runtime | Go 1.24+, Fiber v2, GORM |
| Scripting | go-json, expr-lang, Python, JavaScript, Go (via runtimes) |
| Database | SQLite, PostgreSQL, MySQL, MongoDB |
| Components | Mitosis, React, Vue, React Native, Flutter |
| Native Shell | Tauri 2.0 (Rust) |

## Quick Start

The engine source lives in the `bitcode` monorepo. The packages below
install and run on their own.

**go-json CLI** — standalone JSON/JSONC language engine:

```bash
# full build, with script runtimes (goja, QuickJS, Yaegi, Node, Python)
go install github.com/bitcode-framework/go-json-runtimes/cmd/go-json@v0.1.4

# lite build, core language only, no script runtimes
go install github.com/bitcode-framework/go-json/cmd/go-json-lite@v0.1.2
```

The UI packages are not published to npm yet. Use them straight from source:

```bash
git clone https://github.com/bitcode-framework/ui-schema
git clone https://github.com/bitcode-framework/ui
```

Want to see it running first? The
**[go-json playground](https://bitcode-framework.github.io/go-json/)** and the
**[ui showcase](https://bitcode-framework.github.io/ui/)** need no install at all.

## Project Status

BitCode is under active development and not yet production-ready. The core engine, the go-json language, and the UI packages are all functional and covered by test suites. See each repository for its current status.

## License

Each repository carries its own license. Check the `LICENSE` file in the repository you are using.

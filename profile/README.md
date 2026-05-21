<div align="center">

# BitCode Framework

**AI-Native, Metadata-Driven Application Framework**

Build any application — ERP, CRM, HRM, inventory, project management, or custom business logic — from JSON definitions.

> **Work in Progress** — Actively developed. Not production-ready yet.

[![Go](https://img.shields.io/badge/Go-1.24+-00ADD8?logo=go)](https://go.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?logo=typescript)](https://www.typescriptlang.org/)
[![Rust](https://img.shields.io/badge/Rust-1.80+-000000?logo=rust)](https://www.rust-lang.org/)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
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
  ├── Compiler — JSON → validated AST
  ├── Runtime — Process executor, DAG engine, agents, workflow
  ├── go-json — Embedded JSON/JSONC programming language
  ├── Security — RBAC, record rules, field-level encryption, audit log
  └── Server — REST, GraphQL, WebSocket, SSR templates
        |
  Stencil Web Components (119 components)
        |
  Tauri Native Shell (desktop + mobile, offline-first)
```

## Repositories

### Core Engine

| Repo | Description |
|------|-------------|
| [bitcode](https://github.com/bitcode-framework/bitcode) | Full monorepo — Go engine + components + Tauri shell. Source of truth. |
| [go-json](https://github.com/bitcode-framework/go-json) | Standalone JSON/JSONC programming language engine. 20 step types, 135+ functions, lambda, pattern matching, structs, I/O modules, web server. Embeddable. |
| [go-json-runtimes](https://github.com/bitcode-framework/go-json-runtimes) | Script runtimes for go-json — Goja (JS), QuickJS, Yaegi (Go), WASM, Node.js, Python. Each opt-in. |

### UI & Native

| Repo | Description |
|------|-------------|
| [ui-stencil-web-components](https://github.com/bitcode-framework/ui-stencil-web-components) | 119 Stencil Web Components. Fields, charts, data tables, dialogs, media viewers. Framework-agnostic, works in plain HTML. |
| [ui-tauri](https://github.com/bitcode-framework/ui-tauri) | Tauri 2.0 native shell. Desktop (Win/Mac/Linux) + Mobile (iOS/Android). Offline SQLite, native bridge, sync engine. |

### Samples & Tools

| Repo | Description |
|------|-------------|
| [erp](https://github.com/bitcode-framework/erp) | Sample ERP application (CRM + HRM) built with BitCode. |
| [pg_fast_data_transfer](https://github.com/bitcode-framework/pg_fast_data_transfer) | Fast PostgreSQL data transfer utility. |

## Capabilities

| Area | What You Get |
|------|-------------|
| **Data Layer** | Models with 30+ field types, relationships (many2one, one2many, many2many), computed fields, validations, sanitization |
| **API** | Auto-CRUD from model definitions, REST + GraphQL + WebSocket, OpenAPI/Swagger |
| **Business Logic** | Process engine (14 step types), workflow state machines, model lifecycle events, DAG executor |
| **Security** | RBAC with record rules, JWT auth, 2FA, field-level encryption (AES-256-GCM), audit log, rate limiting |
| **Scripting** | go-json language + external scripts (Python, JS, Go) orchestrated from JSON programs |
| **Views** | List, form, kanban, calendar, chart — auto-generated from model metadata |
| **UI** | 119 Web Components, 4-level data fetching, 3-level validation, theming, i18n (11 languages) |
| **Offline** | Local SQLite, outbox pattern, delta sync, field-level conflict resolution |
| **Native** | Desktop + mobile via Tauri, barcode scanning, biometric auth, push notifications |
| **Multi-DB** | SQLite, PostgreSQL, MySQL, MongoDB |

## Tech Stack

| Layer | Technology |
|-------|------------|
| Runtime | Go 1.24+, Fiber v2, GORM |
| Scripting | go-json, expr-lang, Python, JavaScript, Go (via runtimes) |
| Database | SQLite, PostgreSQL, MySQL, MongoDB |
| Components | Stencil.js, ECharts, Tiptap, CodeMirror, Leaflet, FullCalendar |
| Native Shell | Tauri 2.0 (Rust) |

## Quick Start

```bash
go install github.com/bitcode-framework/bitcode/cmd/bitcode@latest
bitcode serve
```

Server at `http://localhost:8080`. SQLite created automatically. Zero config.

## Project Status

BitCode is under active development. Core engine is functional with 570+ tests passing. See individual repos for detailed status.

## License

[MIT](https://opensource.org/licenses/MIT)

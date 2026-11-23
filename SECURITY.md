# Security & Vulnerability Disclosure Policy — PureForge-Studio

**Vendor:** PureForge-Studio  
**Security Contact:** `uo7vhd510@mozmail.com`  
**Privacy & Scope Justification Policy:** [PRIVACY.md](./PRIVACY.md)

## 1. "Runs on Atlassian" Zero-Egress Guarantee
All seven **PureForge-Studio** applications run 100% natively on Atlassian Forge (`nodejs24.x`) with:
- **Zero outbound network egress** (`permissions.external` omitted on every app).
- **Zero external servers or third-party databases** (all state stored exclusively inside the customer's encrypted Atlassian Forge `storage:app` partition).
- **Zero external CDN assets** (all CSS, SVG, and JavaScript assets are bundled locally inside the Forge Custom UI static resource).

## 2. Automated DevSecOps & Quality Gates
Every commit across the PureForge-Studio monorepo is gated by:
- **Static Application Security Testing (SAST):** Ruff Bandit (`S`), blind-exception bans (`BLE`), Pyright strict type checking, and AST/regex bans on `eval()`, `new Function()`, `XMLHttpRequest`, and external `fetch("http...")`.
- **Software Composition Analysis (SCA):** Weekly scheduled `pip-audit` against locked dependencies, `bandit -ll` security scans, and `detect-secrets` full-tree entropy scanning.
- **Curated Throwaway-Tree Mutation Probes:** 12 automated Python and Node 24 mutation probes verifying zero-egress manifest auditing, Marketplace license enforcement, XSS/SVG entity escaping, CSV formula injection blocking (`=CMD`, `+powershell`), and destructive-operation confirmation guards.

## 3. Reporting a Vulnerability
If you believe you have discovered a security vulnerability in any **PureForge-Studio** application:
1. Email **`uo7vhd510@mozmail.com`** with `[SECURITY]` in the subject line (or open a ticket on https://github.com/Pureforge-Studio/docs/issues without public exploit details).
2. We acknowledge receipt within **2 business days (48 hours)** and deploy verified security patches to the Atlassian Forge `production` environment in accordance with the Atlassian Marketplace Security Bug Fix Policy.

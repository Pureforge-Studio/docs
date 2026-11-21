# Pure-Forge Inbound Webhook & Alert-to-Issue Router (`Jira` & `Confluence`)

![Pure-Forge Inbound Webhook & Alert-to-Issue Router](./assets/webhook_router_prod_clean.png)

## 1. What Problem Does This App Solve?

When production monitoring tools (**PagerDuty, Datadog, Sentry, GitHub Actions, or custom webhook emitters**) fire an alert storm, engineering teams using standard Jira or Confluence webhook integrations run into three painful failures:
1. **Alert Storms Flood Your Jira Backlog:** A 5-minute database replica lag spike can fire 80+ identical webhook notifications, creating 80 duplicate Jira tickets that overwhelm your on-call engineer.
2. **Brittle JSON Field Mapping & "Entity Not Found" Errors:** Legacy webhook plugins fail when extracting nested JSON properties (such as `alert.title`, `alert.severity`, or `alert.service`) or fail with `"Entity not found"` when saving routing rules.
3. **External Webhook Relay Security Risks:** Many third-party webhook connectors route your incident payloads through external vendor servers outside Atlassian Cloud.

**Pure-Forge Inbound Webhook & Alert-to-Issue Router** runs **100% inside Atlassian Forge with zero external data egress** (**"Runs on Atlassian"**). It validates inbound JSON payloads, extracts nested fields via deterministic dot-paths, coalesces duplicate alert-storm deliveries via SHA-256 fingerprinting, and routes unique alerts into atomic Jira issue or Confluence incident batches with an idempotent replay journal.

---

## 2. Key Capabilities at a Glance

- **SHA-256 Alert-Storm Deduplication & Coalescing:** Automatically groups identical alerts sharing the same target project, source system, service name, and summary into a single Jira issue while recording the exact coalesced occurrence count (e.g., `16x coalesced`).
- **Deterministic Dot-Path JSON Field Mapper (`No eval()`):** Map any nested JSON property (such as `alert.title`, `alert.severity`, `alert.service`) directly to Jira issue fields without writing custom scripts or exposing regex/eval vulnerabilities.
- **Built-In Presets for PagerDuty, Datadog, Sentry & GitHub Actions:** Test and preview your routing rules immediately against realistic multi-event alert storms before enabling live routing.
- **Idempotent Dead-Letter Replay Safety Guard:** Replaying historical webhook batches requires explicit `confirm_replay=True` verification (`Amber Refusal` guard) so operators never trigger accidental duplicate ticket floods.
- **Fail-Closed XSS & Prototype Pollution Protection:** Any inbound webhook containing `<script>` tags, inline event handlers, or `__proto__` / `constructor.prototype` tokens is immediately blocked (`Red Fault` guard) before touching Jira or Confluence REST APIs.

---

## 3. Step-by-Step Quickstart Guide

### Step 1: Open the Router in Jira or Confluence
- **In Jira:** Open any Jira issue and click the **Pure-Forge Inbound Webhook & Alert-to-Issue Router** panel beneath the issue summary.
- **In Confluence:** Type `/Pure-Forge Inbound Webhook` on any incident or runbook page to insert the live routing studio macro.

### Step 2: Configure Your Target Project & JSON Dot-Paths
1. Enter your **Target Jira Project Key** (for example, `OPS` or `PLAT`) and **Target Issue Type** (such as `Incident` or `Bug`).
2. Set the **Summary Dot-Path** (`alert.title`), **Severity Dot-Path** (`alert.severity`), and **Service Dot-Path** (`alert.service`) matching your inbound JSON structure.

### Step 3: Preview & Coalesce Inbound Alert Batches
1. Select a preset (**PagerDuty Alert Storm**, **Datadog APM Latency**, **Sentry Unhandled Exception**, or **GitHub Actions Failure**) or paste a custom JSON array of webhook deliveries into the **Live Inbound Webhook JSON Batch Inspector**.
2. Click **Route & Coalesce Webhook Batch**.
3. Review the **SHA-256 Fingerprint**, **Extracted Summary**, **Storm Dedup Count**, and **Replay Journal ID** (`whj-...`) for each atomic 25-issue batch.

---

## 4. Security, Privacy & Support

- **Runs on Atlassian (Zero External Egress):** All payload parsing, SHA-256 fingerprinting, and replay journaling execute inside Atlassian's managed Node 24 Forge runtime and Forge app storage.
- **Need Help?** Visit our **[Support & SLA Page](./SUPPORT.md)** or open an issue on **[GitHub Issues](https://github.com/Pureforge-Studio/docs/issues)**.

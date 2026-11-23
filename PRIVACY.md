# Privacy Policy & Forge Scope Justifications — PureForge-Studio

**Effective Date:** November 20, 2026  
**Last Updated:** November 22, 2026  
**Vendor:** PureForge-Studio  

## 1. 100% Zero-Egress Architecture ("Runs on Atlassian")
All seven Atlassian Cloud applications published by **PureForge-Studio** run exclusively on the native **Atlassian Forge (`nodejs24.x`)** platform with **zero external network egress** (`permissions.external` is completely omitted from every app's `manifest.yml`):

1. **Pure-Forge SVG Mermaid Studio** (`studio.pureforge.svg-mermaid-studio`)
2. **Pure-Forge Markdown Tree Studio** (`studio.pureforge.markdown-tree-studio`)
3. **Pure-Forge Bulk Label Governance** (`studio.pureforge.bulk-label-governance`)
4. **Pure-Forge Inbound Webhook & Alert Router** (`studio.pureforge.inbound-webhook-alert-router`)
5. **Pure-Forge Zero-Egress CSV & JSON Table Studio** (`studio.pureforge.csv-json-table-studio`)
6. **Pure-Forge Space Glossary & Acronym Dictionary** (`studio.pureforge.space-glossary-dictionary`)
7. **Pure-Forge Inactive User & License Seat Optimizer** (`studio.pureforge.inactive-user-seat-optimizer`)

## 2. Personal Data & PII Declaration
- **No Personal Data Collected, Transmitted, or Stored Outside Atlassian:** Our applications **do not** collect, copy, cache, transmit, or store any End-User Personal Data or Personally Identifiable Information (PII) outside your Atlassian Cloud instance.
- **No External Servers or Third-Party Processors:** All application compute executes inside Atlassian-managed Forge functions and your web browser. All diagram sources, Markdown tree snapshots, label rollback journals, webhook routing journals, CSV/JSON datasets, glossary dictionaries, and anonymized seat audit snapshots are stored exclusively inside your own Atlassian Cloud tenant via the native Atlassian Forge Storage API (`storage:app`, encrypted at rest with AES-256 by Atlassian).
- **No Analytics, Cookies, or External CDNs:** Our applications embed zero third-party tracking scripts, zero external fonts/icons/CDNs, and zero telemetry beacons.

---

## 3. Scope-by-Scope Forge Permission Justifications (`manifest.yml`)

Every **PureForge-Studio** application follows strict least-privilege scoping. Below is the explicit functional justification for every Forge OAuth 2.0 scope declared across our 7 applications:

| Application | Declared Forge Scopes (`manifest.yml`) | Scope-by-Scope Functional Justification |
| :--- | :--- | :--- |
| **1. Pure-Forge SVG Mermaid Studio** | `storage:app`<br>`read:confluence-content.all`<br>`read:jira-work` | • **`storage:app`**: Persists per-page and per-issue Mermaid diagram definitions and viewport zoom/pan settings inside the customer's isolated Forge storage partition.<br>• **`read:confluence-content.all`**: Reads the host Confluence page's Atlassian Document Format (ADF) body when the user clicks *Auto-Detect Page Blocks* so existing `mermaid` code blocks on the page can be rendered as vector SVGs without copy-pasting.<br>• **`read:jira-work`**: Reads the host Jira issue's description and comment code blocks when the macro/panel runs inside a Jira issue view so embedded architecture diagrams render inline. |
| **2. Pure-Forge Markdown Tree Studio** | `storage:app`<br>`read:confluence-content.all`<br>`write:confluence-content` | • **`storage:app`**: Stores imported `.md` folder-tree snapshots, parent-child topological hierarchy state, and recovery checkpoints in Forge app storage.<br>• **`read:confluence-content.all`**: Reads existing Confluence space page titles and parent-child hierarchy to prevent duplicate sibling title collisions before import and to assemble hierarchical `.ZIP` Markdown exports.<br>• **`write:confluence-content`**: Creates and updates nested Confluence pages in parent-first topological order when a user imports a multi-folder Markdown tree. |
| **3. Pure-Forge Bulk Label Governance** | `storage:app`<br>`read:confluence-content.all`<br>`write:confluence-content`<br>`read:jira-work`<br>`write:jira-work` | • **`storage:app`**: Persists color-token taxonomy definitions and atomic rollback journals (`rbj-*`) so any bulk label merge, rename, or delete operation can be undone with 1 click.<br>• **`read:confluence-content.all` & `read:jira-work`**: Paginates across Confluence content labels and Jira issue labels using cursor pagination (bypassing legacy 200-label UI truncation) to build the live label usage inventory.<br>• **`write:confluence-content` & `write:jira-work`**: Applies atomic batch label renames, multi-label merges, and confirmed bulk label removals across the selected issues and pages. |
| **4. Pure-Forge Inbound Webhook & Alert Router** | `storage:app`<br>`read:confluence-content.all`<br>`write:confluence-content`<br>`read:jira-work`<br>`write:jira-work` | • **`storage:app`**: Stores deterministic JSON dot-path field mappings (`alert.title`, `alert.severity`, `alert.service`), SHA-256 alert-storm deduplication fingerprints, and dead-letter replay journals (`whj-*`).<br>• **`read:jira-work` & `write:jira-work`**: Checks for existing open incident issues matching the coalesced alert fingerprint in the target Jira project and routes deduplicated alert batches into Jira issues.<br>• **`read:confluence-content.all` & `write:confluence-content`**: Allows incident postmortem pages in Confluence to embed and synchronize live webhook routing audit logs via the Confluence macro. |
| **5. Pure-Forge Zero-Egress CSV & JSON Table Studio** | `storage:app`<br>`read:confluence-content.all`<br>`read:jira-work` | • **`storage:app`**: Persists inline CSV/JSON table datasets, sort column preferences, and numeric aggregation configurations per page/issue in Forge app storage.<br>• **`read:confluence-content.all`**: Reads CSV/JSON code blocks or table data embedded in the host Confluence page so datasets can be compiled into sortable, filterable tables with automatic `SUM`/`AVG`/`MIN`/`MAX` footers.<br>• **`read:jira-work`**: Reads attached or inline CSV/JSON blocks when rendered inside a Jira issue panel. |
| **6. Pure-Forge Space Glossary & Acronym Dictionary** | `storage:app`<br>`read:confluence-content.all`<br>`read:jira-work` | • **`storage:app`**: Persists the space's canonical A–Z glossary dictionary, acronym aliases, taxonomy categories, and term ownership metadata inside Forge app storage.<br>• **`read:confluence-content.all`**: Scans the host Confluence page context to highlight matching glossary acronyms and verify zero conflicting term definitions across space pages.<br>• **`read:jira-work`**: Enables engineering teams viewing a Jira issue panel to look up space glossary terms and acronyms referenced in the issue summary or description. |
| **7. Pure-Forge Inactive User & License Seat Optimizer** | `storage:app`<br>`read:confluence-content.all`<br>`read:jira-work` | • **`storage:app`**: Stores anonymized dormant-seat audit journals (`saj-*`), inactivity threshold settings ($\ge 14$-day safety floor), and protected admin/bot exclusion rules in Forge storage.<br>• **`read:jira-work` & `read:confluence-content.all`**: Evaluates anonymized content/issue activity timestamps across Jira and Confluence to identify dormant license seats and compute monthly/annual FinOps reclamation savings without modifying or deactivating user accounts. |

---

## 4. Data Retention & Customer Control
Because all application state resides solely within your Atlassian Cloud instance's Forge storage partition (`storage:app`), your organization retains 100% control over its data at all times. Uninstalling any PureForge-Studio application removes its associated Forge app storage in accordance with Atlassian Cloud's standard platform lifecycle.

## 5. Contact & Privacy Inquiries
For privacy questions, scope audits, or security questionnaires, please contact us via:
- **Public Issue Tracker:** https://github.com/Pureforge-Studio/docs/issues
- **Support & Security Email:** `uo7vhd510@mozmail.com`

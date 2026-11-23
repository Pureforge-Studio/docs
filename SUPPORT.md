# Customer Support & Service Level Agreement (SLA) — PureForge-Studio

Welcome to the official customer support portal for **PureForge-Studio** Atlassian Cloud applications:

1. **[Pure-Forge SVG Mermaid Studio](./MERMAID_STUDIO_GUIDE.md)** (`Confluence` & `Jira`)
2. **[Pure-Forge Markdown Tree Studio](./MARKDOWN_TREE_GUIDE.md)** (`Confluence`)
3. **[Pure-Forge Bulk Label Governance](./LABEL_GOVERNANCE_GUIDE.md)** (`Jira` & `Confluence`)
4. **[Pure-Forge Inbound Webhook & Alert Router](./WEBHOOK_ROUTER_GUIDE.md)** (`Jira` & `Confluence`)
5. **[Pure-Forge Zero-Egress CSV & JSON Table Studio](./CSV_JSON_TABLE_GUIDE.md)** (`Confluence` & `Jira`)
6. **[Pure-Forge Space Glossary & Acronym Dictionary](./GLOSSARY_STUDIO_GUIDE.md)** (`Confluence` & `Jira`)
7. **[Pure-Forge Inactive User & License Seat Optimizer](./INACTIVE_SEAT_AUDITOR_GUIDE.md)** (`Jira` & `Confluence`)

---

## 1. Support Channels & Operating Schedule
- **Primary Support Ticket & Bug Tracker (Instant Automated Triage):** Open an issue on our **[GitHub Support Tracker](https://github.com/Pureforge-Studio/docs/issues)** (automated triage and self-service diagnostics respond immediately 24/7; engineer review follows per the SLA table below).
- **Support & Security Email:** `uo7vhd510@mozmail.com`
- **Support Operating Days & Window:** **Monday – Friday (US Eastern Time / ET, UTC-5 / UTC-4)**, excluding observed US Federal Holidays.

---

## 2. Response Time Targets (Standard Support SLA)

| Severity Level | Definition | Automated Triage (GitHub Issues) | Engineer Response Target | Resolution / Follow-Up Target |
| :--- | :--- | :---: | :---: | :--- |
| **Severity 1 (Critical / Security)** | Application fails to load (`Red Fault Banner`) across all users in production or suspected security vulnerability. | **Immediate (< 5 Minutes)** | **Within 2 Business Days (48 Hours)** | Verified fix deployed via Atlassian Forge production channel as top backlog priority. |
| **Severity 2 (Major Functional)** | A core feature (e.g., SVG export, Markdown import, label batch execution, or CSV export) returns an unexpected error. | **Immediate (< 5 Minutes)** | **Within 2–3 Business Days** | Workaround or patch scheduled in the next maintenance release. |
| **Severity 3 (General / Enhancement)** | General usage questions, documentation clarifications, or feature requests (`Amber Refusal` guidance). | **Immediate (< 5 Minutes)** | **Within 3–5 Business Days** | Triaged into product backlog for upcoming minor releases. |

---

## 3. Information to Include in a Support Request
To help us resolve your question as quickly as possible, please include:
1. Which **PureForge-Studio** application and version you are using.
2. Whether the issue occurs in **Confluence Cloud** or **Jira Cloud**.
3. The status banner message shown at the top of the app (*Amber Refusal Diagnostic* or *Red Fault Code*), if applicable.
   *(Never include sensitive company data, Personal Data, or credentials in a support ticket.)*

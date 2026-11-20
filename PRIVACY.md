# Privacy Policy — PureForge-Studio

**Effective Date:** November 20, 2026  
**Vendor:** PureForge-Studio  

## 1. 100% Zero-Egress Architecture ("Runs on Atlassian")
All Atlassian Cloud applications published by **PureForge-Studio**—including **Pure-Forge SVG Mermaid Studio**, **Pure-Forge Markdown Tree Studio**, and **Pure-Forge Bulk Label Governance**—run exclusively on the native **Atlassian Forge** platform with **zero external network egress** (`permissions.external` is completely omitted from every app manifest).

## 2. Personal Data & PII Declaration
- **No Personal Data Collected, Transmitted, or Stored:** Our applications **do not** collect, copy, cache, transmit, or store any Personal Data or Personally Identifiable Information (PII) such as user names, email addresses, IP addresses, or Atlassian `AccountID` references.
- **No External Servers or Third-Party Processors:** All application compute executes inside Atlassian-managed Forge functions and your web browser. All diagram sources, Markdown tree snapshots, and label rollback journals are stored exclusively inside your own Atlassian Cloud tenant via the native Atlassian Forge Storage API (`storage:app`).
- **No Analytics, Cookies, or External CDNs:** Our applications embed zero third-party tracking scripts, zero external CDN dependencies, and zero telemetry beacons.

## 3. Data Retention & Customer Control
Because all application state resides solely within your Atlassian Cloud instance's Forge storage partition, your organization retains 100% control over its data at all times. Uninstalling the application removes its associated Forge app storage in accordance with Atlassian Cloud's standard platform lifecycle.

## 4. Contact & Privacy Inquiries
For privacy questions or security questionnaires, please contact us via:
- **Public Issue Tracker:** https://github.com/Pureforge-Studio/docs/issues
- **Support Email:** `uo7vhd510@mozmail.com`

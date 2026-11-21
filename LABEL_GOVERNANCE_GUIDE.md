# User Guide: Pure-Forge Bulk Label Governance (Jira & Confluence)

**Marketplace App Key:** `studio.pureforge.bulk-label-governance`  
**Security Architecture:** 100% Zero-Egress Atlassian Forge (**"Runs on Atlassian"**)

---

## 1. What Problem Does This App Solve?

In Jira Cloud, any user can type a new label onto an issue. Over a few sprints, projects accumulate dozens of misspelled, duplicate, or obsolete labels across hundreds of issues:
- `tech-debt`, `tech_debt`, `legacy-debt`, `platform-debt`
- `q1-release`, `Q1_Release`, `q1-rel`

When project admins try to clean up these labels, they hit three major roadblocks:
1. **No Native Bulk Rename or Merge in Jira:** Jira has no built-in button to rename a label or merge two labels into one across 150 tickets.
2. **Legacy Label Plugins Crash or Create Duplicate Tags:** Several older Marketplace label managers either fail with a blank white screen when deleting a label, or add the new label without removing the old label.
3. **200-Label Truncation Limits & Timeouts:** Older label plugins hard-cap their list at 200 labels and try to update hundreds of tickets in a single unpaginated request that times out.

**Pure-Forge Bulk Label Governance gives Jira admins a safe, cursor-paginated dashboard to merge, rename, recolor, and delete labels at scale.**

![Pure-Forge Bulk Label Governance UI](./assets/label_governance_prod_clean.png)

---

## 2. How to Use It (3-Step Quickstart)

### Step 1: Open the Label Governance Panel on Any Jira Issue
1. Open any Jira Cloud issue in your project.
2. Click the **Pure-Forge Bulk Label & Taxonomy Governance Manager** issue panel.

### Step 2: Select Source Labels in the Unlimited Cursor-Paginated Inventory
- The left pane (**Cursor-Paginated Label Inventory**) indexes your project's labels without a 200-label cap and displays the exact issue count for each label (e.g., `tech-debt: 82 Issues`, `legacy-debt: 53 Issues`).
- Select one or more source labels to **Rename**, **Merge**, **Recolor**, or **Delete**.

### Step 3: Preview the Atomic 50-Issue Batch Plan & Execute
Before modifying a single Jira ticket, the right pane displays the exact **Atomic Cursor-Paginated Batch Plan**:
- **50-Issue Cursor Batches:** If your merge affects `135` Jira issues, the planner splits the operation into **3 safe batches** (`Batch #1: Issues 1–50`, `Batch #2: Issues 51–100`, `Batch #3: Issues 101–135`) so large updates never hit Jira REST API rate limits or browser timeouts.
- **Two-Phase Atomic Diff:** Every batch clearly shows `+add: ["platform-debt"]` and `-remove: ["tech-debt", "legacy-debt"]` alongside the assigned **Rollback Journal ID** (e.g. `rbj-9f41c80b2a10`).
- Click **Execute Atomic Batch Plan** to apply the changes cleanly across all batches.

---

## 3. Built-In Safety Guards

- **Accidental Bulk-Delete Guard (Amber Banner):** Bulk-deleting a label across dozens of tickets requires explicit confirmation (`confirm_delete`). If triggered without confirmation, an **Amber Safety Refusal Banner** prevents accidental data loss.
- **Atlassian Label Syntax Validator:** Automatically checks that target labels contain no spaces or invalid characters before starting a batch.
- **Fail-Closed Rollback Journal Guard (Red Banner):** If a storage journal write fails or an invalid script/control character is detected, the operation halts before modifying any Jira issue so your project is never left in a half-updated state.

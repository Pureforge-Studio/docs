# User Guide: Pure-Forge Markdown Tree Studio (Confluence)

**Marketplace App Key:** `studio.pureforge.markdown-tree-studio`  
**Security Architecture:** 100% Zero-Egress Atlassian Forge (**"Runs on Atlassian"**)

---

## 1. What Problem Does This App Solve?

Engineering, DevOps, and product teams frequently write documentation in **Markdown (`.md`)** files organized inside nested directories (such as a Git repository's `docs/` folder).

When teams try to bring those Markdown folders into Confluence—or render Markdown directly on Confluence pages—existing plugins fail in four common ways:
1. **Flattening Nested Folders:** Older Markdown importers take a neatly organized folder tree (`docs/architecture/security/zero-egress.md`) and dump every file into a single flat, unorganized list of pages.
2. **Crashing on Image Links:** Standard Markdown image tags (`![Diagram](./arch.svg)`) cause several legacy Confluence Markdown editors to stop rendering completely.
3. **Broken Dark Mode & Missing PDF Code Blocks:** Older Markdown/Code macros don't adapt to Confluence Dark Mode and disappear when a page is exported to PDF or Word.
4. **No Whole-Space Markdown Export:** Exporting an entire Confluence page tree back out into a clean folder structure of `.md` files often fails on multi-level spaces.

**Pure-Forge Markdown Tree Studio solves all four problems inside a single zero-egress Confluence app.**

---

## 2. How Folder Trees Map to Confluence Pages

When you import a nested folder of Markdown files, **Pure-Forge Markdown Tree Studio** plans your Confluence page creation in **Parent-First Topological Order** (`Depth 0` $\rightarrow$ `Depth 1` $\rightarrow$ `Depth 2`):

```text
Your Markdown Folder Tree                  Created Confluence Page Hierarchy
─────────────────────────                  ─────────────────────────────────
docs/
├── index.md                         ───►  [Depth 0] Engineering Handbook (Space Root)
└── architecture/
    ├── index.md                     ───►    └── [Depth 1] Architecture (Child of Engineering Handbook)
    ├── zero-egress.md               ───►          ├── [Depth 2] Zero Egress Guide (Child of Architecture)
    └── pdf-export.md                ───►          └── [Depth 2] PDF Export Spec (Child of Architecture)
```

- **`index.md` / `README.md` Automatic Root Resolution:** Any `index.md` or `README.md` inside a subfolder becomes the parent Confluence page for that folder, and all sibling `.md` files in that folder are created underneath it as child pages.
- **H1 Heading Title Extraction:** Page titles are automatically extracted from each file's top `# Heading` (or humanized from the filename if no `# Heading` is present).

---

## 3. How to Use It (3-Step Quickstart)

### Step 1: Open the Studio Macro on a Confluence Page
1. Edit a Confluence page where you want to preview or manage Markdown content.
2. Type **`/markdown-tree`** and select **Pure-Forge Bi-Directional Markdown Tree Importer, Exporter & Live Macro**.

### Step 2: Review the Parent-First Page Tree Plan
- Look at the **Hierarchical Folder-to-Page Tree Planner** on the left pane.
- Each planned page shows its **Depth level (`[Depth 0]`, `[Depth 1]`, `[Depth 2]`)**, its resolved parent page, and the count of detected **Code Blocks** and **Image Links**.
- **Pre-Flight Sibling Collision Guard (Amber Banner):** Confluence does not allow two pages under the same parent to have identical titles. Before touching your space, our planner checks for duplicate titles and highlights any collision in a calm **Amber Banner** so you can rename the file before importing.

### Step 3: Preview Dark/Light Code Blocks or Export the Space
- The right pane renders your Markdown content and syntax-highlighted code blocks with automatic **Dark Mode** and **Confluence PDF/Word export** compatibility.
- Click **Export Whole Space (.ZIP Tree)** to export a Confluence page hierarchy back into a clean folder tree of `.md` files with YAML frontmatter (`title`, `page_key`, `parent_key`).

---

## 4. Security & Path-Traversal Protection

- **Fail-Closed Path & Image Guard:** Any Markdown bundle entry attempting relative path traversal (`../`) or containing an executable `javascript:` image/link URI is immediately blocked by the **Red Security Fault Guard** before any Confluence API call is made.

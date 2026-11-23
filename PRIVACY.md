# Privacy Policy — PureForge-Studio

**Effective:** November 23, 2026
**Publisher:** PureForge-Studio

Our apps run entirely on Atlassian's Forge platform. They keep their data in your Atlassian site's app storage and send nothing to us or to anyone else. We cannot see your data.

This policy covers the seven apps PureForge-Studio publishes on the Atlassian Marketplace: Mermaid Studio, Markdown Tree Studio, Label Governance, Webhook Router, JSON/CSV Table Studio, Glossary & Taxonomy Studio, and the License Seat Optimizer (Inactive User Auditor). It does not cover Atlassian's own products, which are governed by [Atlassian's Privacy Policy](https://www.atlassian.com/legal/privacy-policy). It also does not cover outside services you set up to send webhooks to Webhook Router.

## What each app stores

Each app keeps only what it needs, in the Forge app storage of the site where it is installed. Some apps also keep an unsaved draft or preferences in your own browser's local storage; these never leave your device.

| App | Stored in app storage | Kept only in your browser |
| --- | --- | --- |
| Mermaid Studio | The diagram source, its type and the time it was saved, for each macro or Jira issue. | Your unsaved draft and the last diagram you edited. |
| Markdown Tree Studio | The Markdown of each live macro. For imports and exports in progress: the target space and parent page, page titles, file paths and the IDs of pages created or queued. File contents pass through while a page is created or exported, but are not kept. | Your unsaved macro draft. |
| Label Governance | A journal of the 25 most recent label runs: the operation, the labels involved, counts, status, and for each changed issue its ID, key and labels before and after (used for undo). | Your unsent operation draft. |
| Webhook Router | Your settings (project, issue type, field paths, priority mapping, labels); the secret webhook token; the last 50 delivery results (time, outcome, issue key, a short reason); and hashed duplicate-check fingerprints, which expire after your dedupe window (at most 7 days). | Your unsaved settings draft. |
| JSON/CSV Table Studio | The table data and its sort and filter, for each macro or Jira issue. | Your unsaved draft. |
| Glossary & Taxonomy Studio | The glossary terms, acronyms, categories, definitions and owner-team text, for each Confluence space or Jira project. | Your unsaved draft. |
| License Seat Optimizer | Your seat cost, dormancy threshold, and the totals of the last audit (user counts, dormant count, savings). The user list from your CSV is read in your browser and is not stored. | Your "never flag" list and column preferences. |

**Webhook Router:** the app does not store a delivery's content. It does copy the summary, and up to 20,000 characters of the payload, into the Jira issue it creates. That issue then follows your Jira site's own permissions and retention.

## What we do not collect

- No app stores Atlassian account IDs, names or email addresses. The License Seat Optimizer reads them from your CSV in the browser and keeps only totals.
- No analytics, tracking, cookies or advertising identifiers.
- No copies of your Jira issues or Confluence pages beyond what is listed above. The apps read them when you use a feature and keep only the items in the table.
- No data is sent to us or to any third party. The apps declare no outbound network access ("Runs on Atlassian"), so Forge blocks them from contacting any outside server.

## Where data lives and who can see it

- **Storage.** Atlassian hosts all app data in Forge app storage, separately for each site that installs the app. It never sits on servers we run. Forge hosted storage follows your site's Atlassian data residency location and moves with it ([Forge data residency](https://developer.atlassian.com/platform/forge/data-residency/)).
- **Who can see it.** Only people using the app on your site, within the permissions of the page, issue, space or project it sits on. Label Governance, Webhook Router and the License Seat Optimizer appear only on admin pages. Table Studio and Glossary Studio save only for people who can edit the page or issue.
- **Our access.** We have no way to read or export your app data. Forge keeps technical error logs that the developer can view. Our apps write no log entries of their own, so those logs hold only error messages and stack traces.
- **Atlassian APIs.** The apps call Jira and Confluence only for the feature you are using, and with your own permissions. The one exception is Webhook Router, which creates issues as the app because no user is present when a webhook arrives.
- **Sharing.** We do not sell, rent or share data. The only other party involved is Atlassian, as the hosting platform.

## How long data is kept

- Diagrams, macros, tables, glossaries and settings stay until you change them or uninstall the app.
- Label Governance keeps its 25 most recent runs; older runs are deleted automatically.
- Webhook Router keeps its 50 most recent delivery results. Duplicate-check fingerprints expire after your dedupe window.
- The License Seat Optimizer keeps only the totals of its most recent audit.
- Import and export job records stay until the app is uninstalled.
- When you uninstall an app, Atlassian soft-deletes its app storage, then destroys it under Atlassian's data retention policy. If you reinstall within 21 days, Atlassian support can relink the earlier data ([Forge data lifecycle](https://developer.atlassian.com/platform/forge/storage-reference/hosted-storage-data-lifecycle/)). To clear browser drafts, clear your browser's site data.

## Permissions each app requests

| App | Scopes |
| --- | --- |
| Mermaid Studio | `storage:app`, `read:page:confluence`, `read:jira-work` |
| Markdown Tree Studio | `storage:app`, `read:page:confluence`, `write:page:confluence`, `read:space:confluence` |
| Label Governance | `storage:app`, `read:jira-work`, `write:jira-work` |
| Webhook Router | `storage:app`, `read:jira-work`, `write:jira-work` |
| JSON/CSV Table Studio | `storage:app`, `read:page:confluence`, `read:jira-work` |
| Glossary & Taxonomy Studio | `storage:app`, `read:page:confluence`, `read:jira-work` |
| License Seat Optimizer | `storage:app` |

Each app's user guide explains why it needs each scope.

## Your rights, security and changes

- **Your rights.** You control your data through the apps and your Atlassian site. Edit or delete it in the app, or uninstall the app to remove all of it. We hold no copy, so you or your site admin handle any request to see or delete data; email us if you'd like help.
- **Security.** See our [Security Policy](./SECURITY.md).
- **Children.** The apps are business tools and are not meant for children.
- **Changes.** If we change this policy we will update the effective date. Before any change to what the apps store, we will post a notice here at least 30 days in advance.

## Contact

PureForge-Studio, North Charleston, SC 29405, United States. Email: `uo7vhd510@mozmail.com`. Issues: https://github.com/Pureforge-Studio/docs/issues

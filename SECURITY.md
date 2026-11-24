# Security Policy — PureForge-Studio

**Security contact:** `security@pureforgestudio.com` (put `[SECURITY]` in the subject line)
**Privacy:** [PRIVACY.md](./PRIVACY.md)

## How the apps are built

- **Hosted on Atlassian Forge.** All seven apps run on Atlassian Forge (`nodejs24.x`). They declare no outbound network access, so Forge blocks any call to an outside server.
- **Data stays in your site.** App data lives only in Forge hosted storage on the site where the app is installed. We run no servers or databases of our own.
- **No outside scripts.** Every script, style and library, including the bundled Mermaid renderer, ships inside the app. Nothing is loaded from a CDN.
- **Least privilege.** Each app requests only the scopes listed in the [Privacy Policy](./PRIVACY.md), and acts with the current user's permissions wherever a user is present.
- **Safe rendering.** User text is escaped before display. Diagrams render with Mermaid's strict security level. CSV exports block spreadsheet formulas.

## How we test

Every change to the app code is checked before release:

- Static analysis: Ruff with the Bandit security rules, strict type checking, and checks that ban `eval`, `new Function`, `XMLHttpRequest` and outbound `fetch` calls.
- Secret scanning with detect-secrets on every change, plus a full scan every week.
- A weekly dependency audit with pip-audit and Bandit.
- Mutation tests that deliberately break key safety checks — zero-egress manifests, licence enforcement, output escaping, formula blocking and delete confirmations — to prove the tests catch them.

## Reporting a vulnerability

1. Email `security@pureforgestudio.com` with `[SECURITY]` in the subject. Include the app, the steps to reproduce and the impact. Please don't open a public issue with exploit details.
2. We acknowledge reports within 2 business days.
3. We fix confirmed issues following the [Atlassian Marketplace Security Bug Fix Policy](https://developer.atlassian.com/platform/marketplace/security-bugfix-policy/), and tell you when the fix is released.

Please test only on your own Atlassian site, and don't access or change other people's data.

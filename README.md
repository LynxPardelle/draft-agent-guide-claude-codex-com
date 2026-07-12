# Agent Guide Claude/Codex

<!-- zoolanding-hub-routing:start -->
## Zoolanding Knowledge Router

Shared procedures are routed through the Zoolandingpage hub. Start with [AGENTS.md](AGENTS.md) and open only the document needed for the current task.

| Task | Read |
| --- | --- |
| Edit draft content or routes | Local `site-config.json`, page JSON, and task-specific local docs |
| Create or bootstrap a draft | [ai-notes/how-to/create-secure-draft-repo.md](https://github.com/LynxPardelle/zoolandingpage/blob/main/ai-notes/how-to/create-secure-draft-repo.md) |
| Promote, deploy, or configure branches | [Hub lifecycle guide and local `.github/workflows/`](https://github.com/LynxPardelle/zoolandingpage/blob/main/docs/11-draft-lifecycle.md) |
| Upload public assets | [docs/12-public-assets-and-file-uploads.md](https://github.com/LynxPardelle/zoolandingpage/blob/main/docs/12-public-assets-and-file-uploads.md) |
| Configure domains or aliases | [docs/13-managed-alias-front-door.md](https://github.com/LynxPardelle/zoolandingpage/blob/main/docs/13-managed-alias-front-door.md) |
| Work across repositories | [docs/repository-map.md](https://github.com/LynxPardelle/zoolandingpage/blob/main/docs/repository-map.md) |

Critical repository-specific safety, deployment, and rollback rules remain local.
<!-- zoolanding-hub-routing:end -->

Public draft source for `agent-guide-claude-codex.com`.

## Start Here

| Task | Source |
| --- | --- |
| Agent safety and closeout | [AGENTS.md](AGENTS.md) |
| Domain, environments, and required GitHub variables | [draft-repo.config.json](draft-repo.config.json) |
| Routes and page IDs | [site-config.json](site-config.json) |
| Page content | `{pageId}/page-config.json`, `{pageId}/components.json`, `{pageId}/variables.json`, and `{pageId}/i18n/` |
| Deployment implementation | [tools/deploy-draft.mjs](tools/deploy-draft.mjs) and [.github/workflows/](.github/workflows/) |
| Local-only investigation context | `ai_notes/README.md`, then only the relevant ignored note or evidence |

Shared cross-repository guidance lives in the [Zoolandingpage documentation hub](https://github.com/LynxPardelle/zoolandingpage/blob/main/docs/README.md). The hub owns shared authoring, safety, and alias contracts; this repository owns this draft's content, release configuration, and deployment workflows.

## Release Flow

- Work lands on `dev`; it does not deploy.
- A merged pull request `dev -> test` deploys the test environment.
- A separate merged pull request `test -> main` deploys production.
- GitHub Actions use OIDC. Do not add long-lived AWS credentials.

Before PR, merge, visibility changes, or publication, run from a current Zoolandingpage hub checkout:

```powershell
node tools/draft-repo-preflight.mjs --pull=true
node tools/draft-public-safety-audit.mjs --repo=drafts/agent-guide-claude-codex.com --history=true
```

Validate every JSON payload and run `node --check tools/deploy-draft.mjs`. Changes to payloads or rendered behavior also require desktop and mobile browser QA on every affected route. Documentation-only changes require links, workflow syntax, JSON parsing, and public-safety checks; they do not require visual QA.

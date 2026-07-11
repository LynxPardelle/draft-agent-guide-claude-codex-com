# Zoolanding Draft Workflow

Use this file as the mandatory local entrypoint. Start with [README.md](README.md) and [draft-repo.config.json](draft-repo.config.json). Open local `ai_notes/README.md` only when it exists and the task needs that context.

## Git And Publication

- Work on `dev`; promote with separate pull requests `dev -> test -> main`.
- `dev` does not deploy. `test` deploys only the test environment after merge. `main` deploys production only after merge.
- Pull with `--ff-only` only when the worktree is clean. Report dirty, detached, or unexpected branch state before changing files.
- Treat this as an independent Git repository. Stage, commit, and push from this root.
- Do not bypass release guards, weaken OIDC, add long-lived cloud keys, or infer aliases or domains from another draft.

## Public Safety

- Treat this repository as public unless current GitHub metadata proves otherwise.
- Never commit secrets, tokens, upload grants, API keys, signed URLs, raw environment values, private customer data, PII, `.zlp/`, `.env*`, local logs, private source documents, credential files, local databases, or agent state.
- Keep `ai_notes/`, `findings/`, and `errors-reports/` local and ignored. Promote only a sanitized reusable lesson to the hub.
- Public contact details are allowed only when intentionally client-facing. Source CVs, identity documents, private photos, raw research, and unapproved domains or aliases stay local.
- Before PR, merge, visibility changes, or publication, run the hub public-safety audit and resolve every blocking finding.

## Shared Guidance

- Draft lifecycle: https://github.com/LynxPardelle/zoolandingpage/blob/main/docs/11-draft-lifecycle.md
- Public assets/uploads: https://github.com/LynxPardelle/zoolandingpage/blob/main/docs/12-public-assets-and-file-uploads.md
- Managed aliases: https://github.com/LynxPardelle/zoolandingpage/blob/main/docs/13-managed-alias-front-door.md
- Fleet ownership: https://github.com/LynxPardelle/zoolandingpage/blob/main/docs/repository-map.md

Keep critical draft-specific safety and release rules here; link extended shared procedures instead of copying hub history.

## Closeout

- Run repository guard/deploy checks and the hub preflight/public-safety checks relevant to the change.
- Audit, fix, and rerun at least three times.
- Payload, route, style, script, or rendered-behavior changes require desktop and mobile browser QA on every affected route. Documentation-only changes require link, workflow, JSON, and public-safety validation.
- Keep chronology in GitHub pull requests and the owning hub draft changelog, not in this file or `Codex.md`.

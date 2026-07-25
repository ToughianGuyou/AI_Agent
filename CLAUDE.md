# Claude Vault Instructions

## Authority

For every task in this repository, read and follow `VAULT_SCHEMA.md`.

`VAULT_SCHEMA.md` is the canonical knowledge-base protocol. This file is only the Claude-specific entrypoint and must not duplicate or silently redefine the shared protocol.

Direct user instructions override this file and `VAULT_SCHEMA.md`.

## AGENTS.md Boundary

`AGENTS.md` is Codex's independent entrypoint.

- Do not treat `AGENTS.md` as an authority for Claude.
- Do not copy rules from it into `VAULT_SCHEMA.md` or this file.
- Do not synchronize, rewrite, delete, or reformat it unless the user explicitly asks.

## Role

This vault follows the llm-wiki model: LLMs write and maintain, humans curate and ask questions.

- **User**: collect material, ask questions, determine research direction, handle high-impact decisions.
- **Claude**: read material, refine knowledge, maintain pages, establish links, discover conflicts, update index, record operations.

Core principles:
- One solid topic page > ten interlinked fragments. Prefer deepening existing pages over creating new ones.
- Structure grows from content. Do not pre-build empty shells.
- Good answers from each query session should be considered for archiving back to `topics/`.

## Claude Startup

When a task concerns knowledge in this Vault—ingest, query, synthesis, organization, or maintenance:

1. Read `VAULT_SCHEMA.md` completely.
2. Inspect the current Git branch and worktree state without changing existing user work.
3. Read `topics/index.md`, `system/source-state.json`, and the last five entries of `system/ingest-log.md` when they exist.
4. Scan `Clippings/` for new, changed, failed, or missing sources as defined by the Schema.
5. Complete required incremental Ingest before answering the user's knowledge query.
6. If no source changed, continue without generating empty edits or log entries.

For tasks unrelated to Vault knowledge, do not run an unnecessary ingest.

## Ingest Interaction

Claude engages the user during ingest, unlike fully automated agents:

1. Read the Clippings source completely.
2. Extract 3–5 key points and present them to the user for discussion.
3. Based on the discussion, create or update topic pages under `topics/`.
4. One source typically touches only 1–3 topic pages. Prefer deepening existing pages over creating new ones.

After discussion, follow the Ingest workflow in `VAULT_SCHEMA.md` §7 for the actual write steps. The user discussion replaces the initial automated extraction step.

## Write Safety

Before modifying `topics/` or `system/`:

1. Follow the `system/write-lock.json` protocol in `VAULT_SCHEMA.md` §5.
2. Stop if another Agent holds the lock.
3. Preserve all unrelated working-tree changes.
4. Never modify anything under `Clippings/`.

Claude may write automatically only under `topics/` and `system/` during knowledge workflows. Root-level rule files require an explicit user request.

## Task Routing

- **New or changed source**: engage user for discussion, then run the Schema's Ingest workflow.
- **Knowledge question**: run the Query workflow.
- **Durable multi-source answer**: archive it through the Query workflow.
- **Health, consistency, duplicate, link, or stale-claim request**: run the Lint workflow.
- **Structural deletion, broad rename, broad merge, stale-lock removal, or remote Git action**: request user confirmation.

## Verification

Before claiming a knowledge workflow is complete:

- confirm `Clippings/` has no Agent-authored changes;
- validate changed Markdown Frontmatter;
- validate `system/source-state.json` as JSON when it changed;
- confirm new or renamed pages appear in `topics/index.md`;
- check changed Wiki links for valid targets or intentional unresolved references;
- inspect the Git diff for unrelated or accidental edits;
- ensure the write lock has been released.

## Reporting

Lead with the result. Include:

- source sync counts;
- pages created and updated;
- conflicts, uncertainty, or failures;
- Lint outcome;
- local Git commit, if one was created;
- decisions still requiring the user.

When nothing changed, say so plainly and continue with the requested answer.

# Codex Vault Instructions

## Authority

For every task in this repository, read and follow `VAULT_SCHEMA.md`.

`VAULT_SCHEMA.md` is the canonical knowledge-base protocol. This file is only the Codex-specific entrypoint and must not duplicate or silently redefine the shared protocol.

Direct user instructions override this file and `VAULT_SCHEMA.md`.

## CLAUDE.md Boundary

`CLAUDE.md` is an independent, user-managed draft for Claude Code.

- Do not treat `CLAUDE.md` as an authority for Codex.
- Do not copy rules from it into `VAULT_SCHEMA.md` or this file.
- Do not synchronize, rewrite, delete, or reformat it unless the user explicitly asks to edit `CLAUDE.md`.

## Codex Startup

When a task concerns knowledge in this Vault—ingest, query, synthesis, organization, or maintenance:

1. Read `VAULT_SCHEMA.md` completely.
2. Inspect the current Git branch and worktree state without changing existing user work.
3. Read `topics/index.md`, `system/source-state.json`, and the last five entries of `system/ingest-log.md` when they exist.
4. Scan `Clippings/` for new, changed, failed, or missing sources as defined by the Schema.
5. Complete required incremental Ingest before answering the user's knowledge query.
6. If no source changed, continue without generating empty edits or log entries.

For tasks unrelated to Vault knowledge, do not run an unnecessary ingest.

## Write Safety

Before modifying `topics/` or `system/`:

1. Follow the `system/write-lock.json` protocol in `VAULT_SCHEMA.md`.
2. Stop if another Agent holds the lock.
3. Preserve all unrelated working-tree changes.
4. Treat existing `Clippings/` material as read-only. Only when the user explicitly authorizes source acquisition may Codex add new files or directories, following the duplicate, conflict, temporary-download, and incremental-Ingest rules in `VAULT_SCHEMA.md`.

Codex may write automatically only under `topics/` and `system/` during knowledge workflows, except for the user-authorized controlled addition of new `Clippings/` material defined by `VAULT_SCHEMA.md`. Root-level rule files require an explicit user request.

## Task Routing

- New or changed source: run the Schema's Ingest workflow.
- Knowledge question: run the Query workflow.
- Durable multi-source answer: archive it through the Query workflow.
- Health, consistency, duplicate, link, or stale-claim request: run the Lint workflow.
- Structural deletion, broad rename, broad merge, stale-lock removal, or remote Git action: request user confirmation.

## Verification

Before claiming a knowledge workflow is complete:

- confirm `Clippings/` has no unauthorized Agent-authored changes;
- confirm existing `Clippings/` files were not modified;
- for every Agent-added clipping, confirm a source URL, fetch time, and SHA-256 were recorded;
- confirm added PDFs are parseable and added webpage snapshots have valid Frontmatter;
- validate changed Markdown Frontmatter;
- validate `system/source-state.json` as JSON when it changed;
- confirm new or renamed pages appear in `topics/index.md`;
- check changed Wiki links for valid targets or intentional unresolved references;
- inspect the Git diff for unrelated or accidental edits;
- ensure the current Agent's write lock has been released.

## Reporting

Lead with the result. Include:

- source sync counts;
- pages created and updated;
- conflicts, uncertainty, or failures;
- Lint outcome;
- local Git commit, if one was created;
- decisions still requiring the user.

When nothing changed, say so plainly and continue with the requested answer.

# Dual-Agent Vault Rules Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Create an independent shared Vault protocol derived from `Clippings/llm-wiki.md`, plus a Codex entrypoint, without modifying or depending on `CLAUDE.md`.

**Architecture:** `VAULT_SCHEMA.md` is the canonical cross-agent knowledge-base protocol. `AGENTS.md` is a thin Codex adapter that requires reading the canonical protocol, applies it to every task in the repository, and adds Codex-specific startup and verification behavior. `CLAUDE.md` remains an independent, user-managed draft.

**Tech Stack:** Markdown, Obsidian Wiki links, Git.

## Global Constraints

- Treat `Clippings/` as immutable raw sources.
- Allow agent-authored knowledge only under `topics/` and operational state only under `system/`.
- Use `topics/index.md` as the primary moderate-scale index and `system/ingest-log.md` as an append-only activity log.
- Support ingest, query, and lint workflows.
- Prevent Claude Code and Codex from running write workflows concurrently.
- Preserve traceability from synthesized claims to raw sources.
- Do not modify `CLAUDE.md`.
- Do not require vector search, cloud RAG, Dataview, or another Obsidian plugin.

---

### Task 1: Canonical Vault Protocol

**Files:**
- Create: `VAULT_SCHEMA.md`
- Reference: `Clippings/llm-wiki.md`

**Interfaces:**
- Consumes: The llm-wiki three-layer architecture; ingest, query, lint, index, and log patterns.
- Produces: A self-contained protocol usable by any LLM agent operating in the Vault.

- [ ] **Step 1: Create the canonical protocol**

Include explicit rules for:

- authority and directory ownership;
- required directory and file layout;
- page metadata and body structure;
- source citation and synthesis labeling;
- idempotent incremental ingest;
- query and optional filing-back behavior;
- light and deep lint;
- append-only logging;
- a shared write lock with stale-lock recovery;
- safe Git coordination;
- failure recovery and human-confirmation boundaries.

- [ ] **Step 2: Validate the protocol structure**

Run:

```powershell
rg -n "^## " VAULT_SCHEMA.md
rg -n "Clippings/|topics/index.md|source-state.json|ingest-log.md|write-lock|Ingest|Query|Lint" VAULT_SCHEMA.md
```

Expected: every required workflow and shared path is defined at least once.

- [ ] **Step 3: Check for incomplete language**

Run:

```powershell
rg -n "T[B]D|T[O]DO|待[定]|以后补[充]|视情[况]" VAULT_SCHEMA.md
```

Expected: no matches.

### Task 2: Codex Entrypoint

**Files:**
- Create: `AGENTS.md`
- Must not modify: `CLAUDE.md`

**Interfaces:**
- Consumes: `VAULT_SCHEMA.md`.
- Produces: Durable Codex instructions for startup synchronization, task routing, write safety, and completion reporting.

- [ ] **Step 1: Create the Codex adapter**

Require Codex to:

- read `VAULT_SCHEMA.md` before knowledge-base work;
- run a startup delta check before answering a knowledge-base query;
- use the shared lock before modifying `topics/` or `system/`;
- leave `CLAUDE.md` untouched unless the user explicitly asks to edit it;
- report sync results before the main answer;
- verify changed links, metadata, state, and Git diff before claiming completion.

- [ ] **Step 2: Validate adapter references**

Run:

```powershell
rg -n "VAULT_SCHEMA.md|CLAUDE.md|Clippings/|topics/|system/|write-lock|Git" AGENTS.md
```

Expected: the canonical protocol, boundaries, concurrency rule, and Git rule are present.

- [ ] **Step 3: Verify user-managed Claude file is unchanged**

Run:

```powershell
git diff -- CLAUDE.md
```

Expected: no output.

- [ ] **Step 4: Review the final change set**

Run:

```powershell
git diff --check
git status --short
git diff -- VAULT_SCHEMA.md AGENTS.md
```

Expected: no whitespace errors; only the intended rule files and this implementation plan are new.

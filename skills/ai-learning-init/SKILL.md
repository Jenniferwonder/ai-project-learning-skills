---
name: ai-learning-init
description: >-
  Initialize first-person, learning-in-public study artifacts (my-learning/)
  for an AI-related open-source fork: sync repo, scaffold LEARNING_PLAN and
  dual-direction notes, resume via PROGRESS. Use when the user invokes
  ai-init, ai init, ai-learning-init, or asks to start learning an AI project
  from a fork. Requires a user-specified fork repository URL before any sync
  or note generation (except ai-init continue with existing PROGRESS).
---

# AI Learning Init

Initialize `my-learning/` for studying an AI-related open-source **fork**: sync code, scaffold a learning plan and dual-direction notes, continue via `PROGRESS.md`.

## Hard gate — fork URL first

**Before any clone/pull, any create/edit under `my-learning/`, or any learning note body:**

1. Require a user-specified fork URL (HTTPS or SSH), **or** `fork:` already set in `my-learning/PROGRESS.md` (resume / `ai-init continue`).
2. If missing: ask only for the fork URL. Do not guess upstream. Do not pick a repo. Do not start S1–S5.
3. Standard reply when triggered without URL: this skill binds to a specified fork — please provide the repository URL.

## Invocation

Treat as explicit invoke when the message starts with or is:

| Kind | Phrase |
|------|--------|
| Name | `ai-learning-init` |
| Command | `ai-init` (preferred) |
| Speech | `ai init`, AI 项目学习初始化, 初始化 my-learning, learning in public 学某 fork |

```text
ai-init <fork-url> [local-path] [branch]
ai-init continue
ai-init
```

- `ai-init <fork-url> …` → gate pass → S0/S1
- `ai-init` with no URL → ask for fork URL only
- `ai-init continue` → read `my-learning/PROGRESS.md`; use its `fork:`; if no PROGRESS, say init is required first

## Required inputs

| Field | Required | Notes |
|-------|----------|--------|
| `fork` | Yes | Fork git URL |
| `local_path` | Yes before clone | Where to clone or existing checkout |
| `branch` | Default `main`/`master` | Detect from remote if omitted |
| `learner` | Yes before writing plan voice | One-line「我是谁」profile for first-person docs |

Write these into `PROGRESS.md` header before scaffolding.

## Workflow

```text
Gate → S0 inputs → S1 sync → S2 scout → S3 skeleton → stop
User: continue / ai-init continue → S4 one batch → S5 when all batches done
```

### S0 — Collect inputs

After fork URL exists: collect `local_path`, `branch`, `learner` if missing. Do not invent the learner profile.

### S1 — Sync fork

- If `local_path` is not a git repo: `git clone <fork> <local_path>`, checkout branch.
- If it is: `git fetch` + `git pull` (or ff-only) on the target branch. Prefer the specified fork remote.
- On success, check `[x] S1` in PROGRESS.
- If the agent workspace is not the target repo, move/open that root before writing notes (tool-specific).

### S2 — Scout codebase

From real files only, record in PROGRESS under `## Scout`:

- Stack (language, framework, AI libs)
- Business modules (packages/dirs)
- Core tech themes for tech-qa
- Persistence: yes/no; if yes, where schema lives
- How to run locally (compose / README)

Do not invent modules or tables. Check `[x] S2`.

### S3 — Skeleton only (default first stop)

Create layout from [templates/](templates/). Fill indexes and `LEARNING_PLAN.md` **outlines** from scout (module/tech lists, stage map). Note bodies stay placeholders (`<!-- TODO: batch -->` or short stub).

```text
my-learning/
  PROGRESS.md
  README.md
  LEARNING_PLAN.md
  code-changes/README.md
  notes/
    01-env-setup.md
    02-project-features-overview.md
    03-db-schema-design.md   # or SKIP stub if no DB
    modules/README.md + one stub per module
    tech-qa/README.md + one stub per tech theme
```

**LEARNING_PLAN section order (fixed):**

1. Opening (我是谁 / 载体 / learning in public)
2. Capability map
3. **Staged route (mermaid + stage table) — before L/G**
4. L series (numbers continuous by stage: stage1 = L1–Ln, …)
5. G series (gaps to fill)
6. Execution principles
7. Note index

After S3: check `[x] S3`, stop, report next PROGRESS item. Do not write all note bodies in the same turn.

If `my-learning/` already exists with completed items: **resume mode** — do not rebuild; jump to next unchecked item.

### S4 — Batched writing

One batch per turn by default:

- One overview note, **or**
- One `modules/*` note, **or**
- One `tech-qa/*` note, **or**
- One LEARNING_PLAN section deepen (not whole rewrite)

User may say: `继续` / `只写 modules` / `跳过库表` / `重写 tech-qa/03`.

### S5 — Quality + cross-links

When all PROGRESS content items are done: fix README/index links, run checklist below, check `[x] S5`.

## Resume protocol

1. Read `my-learning/PROGRESS.md` first.
2. Confirm `fork:` (or ask once).
3. Do the **first unchecked** item only (unless user scoped the batch).
4. Mark done; update related README links; report 「已完成 / 下一项」.
5. Never overwrite a checked-complete file unless user says `重写 <path>`.

## Templates

Copy and adapt:

| File | Use |
|------|-----|
| [templates/PROGRESS.md](templates/PROGRESS.md) | Header + checklist |
| [templates/LEARNING_PLAN.md](templates/LEARNING_PLAN.md) | Plan skeleton (stage mermaid before L/G) |
| [templates/README.md](templates/README.md) | my-learning index |
| [templates/project-features-overview.md](templates/project-features-overview.md) | Features overview |
| [templates/db-schema-design.md](templates/db-schema-design.md) | DB notes (or SKIP) |
| [templates/env-setup.md](templates/env-setup.md) | Local boot notes |
| [templates/module-note.md](templates/module-note.md) | Direction 1 |
| [templates/modules-README.md](templates/modules-README.md) | modules index |
| [templates/tech-qa-note.md](templates/tech-qa-note.md) | Direction 2 (`##` domain / `###` question) |
| [templates/tech-qa-README.md](templates/tech-qa-README.md) | tech-qa index |
| [templates/code-changes-README.md](templates/code-changes-README.md) | practice output slot |

## Voice and formatting

- First person（我）everywhere in README, LEARNING_PLAN, notes.
- Learning in public + altruism: reproducible steps, real file paths, tradeoffs and pitfalls.
- **Ban**: 建议、推荐、可以考虑、应当、最好 and similar lecture tone. Use 我的做法是 / 我验证了 / 我踩过.
- tech-qa: domain = `##`, question = `###`; each Q has **答** + **本仓库落点**.
- modules: flow + tech used + data landing; link tech-qa; not a second generic tutorial.
- No fake code anchors — mark gaps as 项目未覆盖 / G items.
- Avoid job-hunting framing in public notes; keep project path/class names as in repo.

## Quality checklist

- [ ] First person; no banned lecture words
- [ ] LEARNING_PLAN: mermaid stages **before** L/G; L ids continuous by stage
- [ ] tech-qa: `##` / `###` structure
- [ ] Every claim that cites code has a real path
- [ ] modules ↔ tech-qa cross-links
- [ ] PROGRESS matches files on disk
- [ ] Skeleton-first: no dumping all bodies in one turn unless user insists

## Never

- Run without fork URL (except valid `ai-init continue` with PROGRESS `fork:`)
- Rebuild an existing completed `my-learning/` tree
- Invent modules, tables, or「本仓库落点」
- Put L/G sections before the staged mermaid route in LEARNING_PLAN
- Write second-person tutorial voice or 「建议你…」

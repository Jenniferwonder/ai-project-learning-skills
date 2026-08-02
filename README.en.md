# AI Project Learning Skills

[中文](README.md) | English

Agent skills for **learning-in-public** study of AI-related open-source projects: sync a fork, scaffold `my-learning/`, and resume via `PROGRESS.md`.

Compatible with the [Agent Skills](https://agentskills.io/) format and the [skills CLI](https://github.com/vercel-labs/skills) (`npx skills`).

## Install (one command)

```bash
npx skills add Jenniferwonder/ai-project-learning-skills
```

Or with the full URL:

```bash
npx skills add https://github.com/Jenniferwonder/ai-project-learning-skills
```

Useful flags:

```bash
# List skills in this repo without installing
npx skills add Jenniferwonder/ai-project-learning-skills -l

# Install only ai-learning-init
npx skills add Jenniferwonder/ai-project-learning-skills -s ai-learning-init

# Global install for Cursor
npx skills add Jenniferwonder/ai-project-learning-skills -g -a cursor -y

# Cursor + Claude Code + Copilot (project scope)
npx skills add Jenniferwonder/ai-project-learning-skills -a cursor -a claude-code -a github-copilot -y
```

After install, start a new agent session so the skill is picked up.

## Available skills

### `ai-learning-init` (command: `ai-init`)

Initialize first-person study artifacts for an AI open-source **fork**:

1. Hard gate: requires a specified fork URL (or `ai-init continue` with existing `PROGRESS.md`)
2. Sync fork → scout codebase → scaffold `my-learning/` skeleton
3. Batched writing of LEARNING_PLAN, feature overview, DB notes, module notes, tech-qa notes
4. Resume any time via `PROGRESS.md` / `ai-init continue`

**Invoke in chat:**

```text
ai-init https://github.com/<you>/<fork>.git
ai init
ai-learning-init
ai-init continue
```

**Outputs under the target repo:**

```text
my-learning/
  PROGRESS.md
  README.md
  LEARNING_PLAN.md          # staged mermaid route before L/G series
  code-changes/
  notes/
    01-env-setup.md
    02-project-features-overview.md
    03-db-schema-design.md
    modules/                # direction 1: by business module
    tech-qa/                # direction 2: ## domain / ### question
```

See [`skills/ai-learning-init/SKILL.md`](skills/ai-learning-init/SKILL.md) and [`skills/ai-learning-init/INSTALL.md`](skills/ai-learning-init/INSTALL.md).

## Example repositories

Repos where this skill was used for learning-in-public study artifacts:

| Repository | Notes |
|------------|--------|
| [ai-interview-platform](https://github.com/Jenniferwonder/ai-interview-platform) | AI full-stack Q&A platform learning artifacts |
| [hot-monitor](https://github.com/Jenniferwonder/hot-monitor) | Hot-topic monitoring project learning artifacts |

## Repository layout

```text
skills/
  ai-learning-init/
    SKILL.md
    INSTALL.md
    templates/
```

The skills CLI discovers each folder that contains a `SKILL.md`.

## License

[MIT](LICENSE) © Jenniferwonder

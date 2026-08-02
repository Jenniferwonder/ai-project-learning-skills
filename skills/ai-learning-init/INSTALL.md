# Install `ai-learning-init`

## Recommended: skills CLI

From any directory:

```bash
npx skills add Jenniferwonder/ai-project-learning-skills
```

Only this skill:

```bash
npx skills add Jenniferwonder/ai-project-learning-skills -s ai-learning-init
```

Global (user-level) for Cursor:

```bash
npx skills add Jenniferwonder/ai-project-learning-skills -g -a cursor -y
```

List without installing:

```bash
npx skills add Jenniferwonder/ai-project-learning-skills -l
```

Then open a new agent chat and run:

```text
ai-init <fork-url>
ai-init continue
```

## Manual install (symlink / copy)

Canonical source in this repo: `skills/ai-learning-init/`.

| Tool | Project | Global |
|------|---------|--------|
| Cursor | `.cursor/skills/ai-learning-init/` or `.agents/skills/` | `~/.cursor/skills/ai-learning-init/` |
| Claude Code | `.claude/skills/ai-learning-init/` | `~/.claude/skills/ai-learning-init/` |
| GitHub Copilot | paste SKILL body into agent instructions, or `.agents/skills/` | `~/.copilot/skills/` (if supported) |

Windows junction example (Cursor global):

```powershell
cmd /c mklink /J "%USERPROFILE%\.cursor\skills\ai-learning-init" "<path-to-repo>\skills\ai-learning-init"
```

macOS / Linux:

```bash
mkdir -p ~/.cursor/skills
ln -s /path/to/ai-project-learning-skills/skills/ai-learning-init ~/.cursor/skills/ai-learning-init
```

## Verify

- [ ] Skill appears in `npx skills ls` (or agent skills list)
- [ ] `ai-init` without URL only asks for the fork URL
- [ ] `ai-init continue` resumes from `my-learning/PROGRESS.md` when present

## Dry-run on an existing `my-learning/`

Do not delete or regenerate a filled tree. Ensure `PROGRESS.md` has `fork:`, mark finished files `[x]`, continue the next unchecked batch.

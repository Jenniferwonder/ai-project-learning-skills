# AI 项目学习 Skills

中文 | [English](README.en.md)

面向 **AI 相关开源项目** 的 Agent Skills：以 learning in public 方式同步 fork、搭建 `my-learning/` 学习骨架，并通过 `PROGRESS.md` 支持中断续写。

兼容 [Agent Skills](https://agentskills.io/) 规范与 [skills CLI](https://github.com/vercel-labs/skills)（`npx skills`）。

## 一键安装

```bash
npx skills add Jenniferwonder/ai-project-learning-skills
```

或使用完整 URL：

```bash
npx skills add https://github.com/Jenniferwonder/ai-project-learning-skills
```

常用参数：

```bash
# 只列出仓库里的 skill，不安装
npx skills add Jenniferwonder/ai-project-learning-skills -l

# 只安装 ai-learning-init
npx skills add Jenniferwonder/ai-project-learning-skills -s ai-learning-init

# 全局安装到 Cursor
npx skills add Jenniferwonder/ai-project-learning-skills -g -a cursor -y

# 同时装到 Cursor / Claude Code / Copilot（项目级）
npx skills add Jenniferwonder/ai-project-learning-skills -a cursor -a claude-code -a github-copilot -y
```

安装后请新开一轮 Agent 对话，以便加载 skill。

## 包含的 Skills

### `ai-learning-init`（命令：`ai-init`）

为指定 AI 开源 **fork** 初始化第一人称学习产出：

1. **硬门禁**：必须先给出 fork 仓库地址（或 `ai-init continue` 且已有 `PROGRESS.md`）
2. 同步 fork → 侦察代码库 → 搭建 `my-learning/` 骨架
3. 分批撰写 LEARNING_PLAN、功能全景、库表、模块笔记、技术高频问答
4. 随时用 `PROGRESS.md` / `ai-init continue` 续写

**对话中唤起：**

```text
ai-init https://github.com/<you>/<fork>.git
ai init
ai-learning-init
ai-init continue
```

**在目标仓库中的产出结构：**

```text
my-learning/
  PROGRESS.md
  README.md
  LEARNING_PLAN.md          # 分阶段 mermaid 路线在 L/G 系列之前
  code-changes/
  notes/
    01-env-setup.md
    02-project-features-overview.md
    03-db-schema-design.md
    modules/                # 方向一：按业务模块
    tech-qa/                # 方向二：## 领域 / ### 问题
```

详见 [`skills/ai-learning-init/SKILL.md`](skills/ai-learning-init/SKILL.md) 与 [`skills/ai-learning-init/INSTALL.md`](skills/ai-learning-init/INSTALL.md)。

## 仓库结构

```text
skills/
  ai-learning-init/
    SKILL.md
    INSTALL.md
    templates/
```

skills CLI 会发现每个包含 `SKILL.md` 的目录。

## License

[MIT](LICENSE) © Jenniferwonder

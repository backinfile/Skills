# 日常 Skills

用于 Codex 的日常技能，涵盖方案梳理、长谈反思、小说写作和 Git 任务管理。

| Skill | 用途 |
| --- | --- |
| [grill](skills/grill/SKILL.md) | 通过逐轮提问，明确计划、取舍和验收标准 |
| [deeper-question](skills/deeper-question/SKILL.md) | 在多轮长对话、上下文足够长之后，提出未问出口的深层问题，只给问题 |
| [novel-writing](skills/novel-writing/SKILL.md) | 生成小说初稿，审查后完整重写，保留各版本 |
| [set-global-rules](skills/set-global-rules/SKILL.md) | 仅由用户主动调用，将表达方式、最小改动、设计文案和测试约定写入全局 AGENTS.md |
| [worktree-task](skills/worktree-task/SKILL.md) | 在独立 Git worktree 中完成任务，确认后合并回原分支 |

## 安装

将 `skills/` 中需要的整个 skill 文件夹复制到 `~/.codex/skills/`（Windows：`%USERPROFILE%\.codex\skills\`）。如设置了 `CODEX_HOME`，则复制到其下的 `skills/` 目录。

## 使用

在对话中用 `$技能名` 调用，例如：

- `$grill 帮我梳理这个方案。`
- `$deeper-question`
- `$novel-writing 根据这份大纲写一篇短篇小说。`
- `$set-global-rules`
- `$worktree-task 实现这个功能。`

`novel-writing` 仅在明确调用时启用；`worktree-task` 需要 Git 仓库。

`set-global-rules` 仅由用户主动调用；安装或创建 skill 时不会改写全局 `AGENTS.md`。调用后保留原有内容并合并四条协作约定，重复调用不会重复添加。

`deeper-question` 仅在对话持续很多轮次、上下文足够长之后触发，只给问题，不用分析。

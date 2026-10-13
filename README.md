# Skills Backup

> Synced by [Skills Manager](https://github.com/cchao123/skills-managers) — a desktop app for managing AI coding agent skills.

## Use as a Claude Code marketplace

This repository is auto-generated as a [Claude Code plugin marketplace](https://docs.claude.com/en/docs/claude-code/plugin-marketplaces). Each skill below is exposed as an individually installable plugin.

In Claude Code, add this marketplace:

```bash
/plugin marketplace add zhankundela/skill
```

Then install any skill you want:

```bash
/plugin install academic-writing@skill
```

Browse all available skills with `/plugin` after adding the marketplace, or see the full list in [`.claude-plugin/marketplace.json`](./.claude-plugin/marketplace.json).

## Skills (5)

| # | Skill | Description |
|---|-------|-------------|
| 1 | **academic-writing** | Scholarly writing and research compliance. Use for CRediT, preregistration, Plan S, Nelson Memo, preprints, ORCID, LLM disclosure. |
| 2 | **coding-specification** | 将科研或工程问题、现有代码、算法背景和预期目标转化为可交给 Codex 执行的 Coding Specification。用于编写代码任务规格、约束和验收计划；本技能的交付物是规格文档，不是完整实现代码。 |
| 3 | **find-skills** | Helps users discover and install agent skills when they ask questions like "how do I do X", "find a skill for X", "is there a skill that can...", or express interest in extending capabilities. This skill should be used when the user is looking for functionality that might exist as an installable skill. |
| 4 | **github-issues** | Create, update, and manage GitHub issues using MCP tools. Use this skill when users want to create bug reports, feature requests, or task issues, update existing issues, add labels/assignees/milestones, manage repository labels, set issue fields (dates, priority, custom fields), set issue types, manage issue workflows, link issues, add dependencies, or track blocked-by/blocking relationships. Triggers on requests like "create an issue", "file a bug", "request a feature", "update issue X", "set the priority", "set the start date", "create a label", "rename a label", "list repo labels", "link issues", "add dependency", "blocked by", "blocking", or any GitHub issue management task. |
| 5 | **matlab** | Builds, reviews, migrates, and plans MATLAB or GNU Octave numerical workflows. Use for arrays, tabular/time data, tests, projects, graphics, MAT files, and explicit Python interoperability. |


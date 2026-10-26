# skills

This repository is the source of truth for my AI agent customizations: Claude Code
skills, agents and commands, tracked under [claude/](claude) (synced to
`~/.claude` via a directory junction). It contains:

- [claude/skills/](claude/skills) — Agent Skills (`SKILL.md` + supporting
  references/scripts/examples) that extend what Claude Code can do.
- [claude/agents/](claude/agents) — Subagent definitions used for delegated
  tasks such as code review.
- [claude/commands/](claude/commands) — Slash commands.

## Skill sources

Most skills here were not written from scratch — they were pulled in from
public skill collections and adapted. Where a skill's origin could be
identified, it's listed below; skills not listed were authored directly in
this repo.

| Skill | Source |
| --- | --- |
| [appinsights-instrumentation](claude/skills/appinsights-instrumentation/SKILL.md) | [github/awesome-copilot](https://github.com/github/awesome-copilot/blob/main/skills/appinsights-instrumentation/SKILL.md) |
| [csharp-async](claude/skills/csharp-async/SKILL.md) | [github/awesome-copilot](https://github.com/github/awesome-copilot/blob/main/skills/csharp-async/SKILL.md) |
| [editorconfig](claude/skills/editorconfig/SKILL.md) | [github/awesome-copilot](https://github.com/github/awesome-copilot/blob/main/skills/editorconfig/SKILL.md) |
| [create-implementation-plan](claude/skills/create-implementation-plan/SKILL.md) | [github/awesome-copilot](https://github.com/github/awesome-copilot/blob/main/skills/create-implementation-plan/SKILL.md) |
| [create-readme](claude/skills/create-readme/SKILL.md) | [github/awesome-copilot](https://github.com/github/awesome-copilot/blob/main/skills/create-readme/SKILL.md) |
| [git-commit](claude/skills/git-commit/SKILL.md) | [github/awesome-copilot](https://github.com/github/awesome-copilot/blob/main/skills/git-commit/SKILL.md) |
| [brainstorming](claude/skills/brainstorming/SKILL.md) | [obra/superpowers](https://github.com/obra/superpowers/blob/main/skills/brainstorming/SKILL.md) |
| [code-simplification](claude/skills/code-simplification/SKILL.md) | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills/blob/main/skills/code-simplification/SKILL.md) |
| [common-skill-creator](claude/skills/common-skill-creator/SKILL.md) | [HoangNguyen0403/agent-skills-standard](https://github.com/HoangNguyen0403/agent-skills-standard/blob/main/skills/common/common-skill-creator/SKILL.md) |
| [find-skills](claude/skills/find-skills/SKILL.md) | Bundled with the [Skills CLI](https://skills.sh/) (`npx skills`) ecosystem |

The [code-reviewer](claude/agents/code-reviewer.md) subagent also comes from
[obra/superpowers](https://github.com/obra/superpowers/blob/main/agents/code-reviewer.md).

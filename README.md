# Agent Evolution Advisor

**A read-only review skill for long-lived OpenClaw agents.**

Agent Evolution Advisor helps you inspect a deployed OpenClaw agent without letting it automatically modify itself.

It focuses on **controlled evolution**:

- review recent runtime behavior
- detect drift across `AGENTS.md`, `SOUL.md`, `USER.md`, and `MEMORY.md`
- assess memory hygiene and interaction quality
- identify tooling reliability and workflow improvement opportunities
- recommend safe next steps without changing production state by default

> **Review first, improve second.**

## Why it exists

Long-lived agents drift.

Rules diverge, memory gets noisy, answers become less actionable, and repeated manual work never becomes workflow. This skill makes those problems visible early in a structured, low-risk way.

## What it does

In strict read-only mode, it helps you:

- audit recent agent behavior
- review rule drift
- check memory hygiene
- evaluate answer quality
- find tooling and workflow inefficiencies
- produce concise, structured review reports

## What it does not do

By default, it does **not**:

- modify code
- rewrite rule files
- patch config
- apply production changes
- start unattended self-improvement loops

This is a deliberately conservative skill for **human-approved improvement**.

## Example prompts

- `复盘最近 2 天 Agent 表现`
- `看一下最近回答质量`
- `审一下规则漂移`
- `检查 MEMORY 和 daily memory 分层`
- `看一下最近工具和 workflow 有没有优化点`

## Included files

- `SKILL.md` — workflow, scope, and boundaries
- `references/finding-examples.md` — finding classification guidance
- `references/report-format.md` — review output structure
- `references/usage-examples.md` — trigger phrases and templates

## Scope

This is a **V1** skill focused on read-only review.

The limitation is intentional: it makes the skill safe enough to use in real deployments before adding more automation.

## Core principle

**No autonomous production changes by default.**

---

## Release Notes / Publishing Notes

Use the following fields when publishing this skill to GitHub, ClawHub, or similar registries.

### GitHub repo description

```text
A read-only OpenClaw review skill for auditing runtime behavior, rule drift, memory hygiene, interaction quality, and workflow design.
```

### GitHub topics

```text
openclaw
agent
ai-agent
agent-skill
runtime-review
workflow
memory
automation
quality-review
```

### ClawHub short description

```text
A read-only OpenClaw review skill for auditing runtime behavior, rule drift, memory hygiene, interaction quality, and workflow design without automatically changing code or production state.
```

### ClawHub tagline

```text
Review first, improve second.
```

### Detailed publishing description

```text
Agent Evolution Advisor is a read-only review skill for long-lived OpenClaw agents.

It helps inspect a deployed agent without letting it automatically modify itself. Instead of autonomous self-editing, it focuses on controlled evolution through review, diagnosis, and structured recommendations.

This skill can help you:
- review recent runtime behavior
- detect drift across AGENTS.md, SOUL.md, USER.md, and MEMORY.md
- assess memory hygiene and interaction quality
- identify tooling reliability issues
- surface workflow improvement opportunities
- produce concise, structured review reports

By default, it does not modify code, config, or production behavior.
```

### Example prompts

```text
复盘最近 2 天 Agent 表现
看一下最近回答质量
审一下规则漂移
检查 MEMORY 和 daily memory 分层
看一下最近工具和 workflow 有没有优化点
```

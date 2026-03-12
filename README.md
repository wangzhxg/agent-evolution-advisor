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

## Installation / How to use

### Option 1: Install from a release asset
If you want the easiest path, download one of the release assets:

- `agent-evolution-advisor.skill`
- `agent-evolution-advisor.skill.zip`

Recommended:
- use `.skill` if you want the native skill package
- use `.skill.zip` if you prefer a more generic download format

Then import the skill into your OpenClaw environment using your normal local skill installation flow.

### Option 2: Use from source
You can also clone or download this repository and use the extracted skill directory directly:

```text
agent-evolution-advisor/
```

Place that directory into your local OpenClaw skills area, or use it as a base for your own modified version.

### How to trigger it
After installation, invoke the skill with review-style prompts such as:

- `复盘最近 2 天 Agent 表现`
- `看一下最近回答质量`
- `审一下规则漂移`
- `看一下最近工具和 workflow 有没有优化点`

### What to expect
This is a read-only review skill.

By default, it will:
- inspect recent runtime behavior
- review rule drift, memory hygiene, interaction quality, tooling reliability, and workflow design
- produce structured recommendations

By default, it will not:
- modify code
- patch config
- rewrite rule files
- change production behavior automatically

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


---
name: agent-evolution-advisor
description: Review a deployed OpenClaw agent in a strictly read-only way. Use to audit runtime behavior, detect drift across AGENTS.md, SOUL.md, USER.md, and MEMORY.md, assess memory hygiene and interaction quality, evaluate tooling reliability and workflow design, and generate structured recommendations for safe long-term improvement without automatically changing code, config, or production behavior.
---

# Agent Evolution Advisor

A read-only review skill for long-lived OpenClaw agents.

Default goal:
1. Observe recent behavior
2. Diagnose repeated problems
3. Recommend practical improvements
4. Separate low-risk suggestions from higher-risk changes
5. Leave execution to a later explicit step

Allowed:
- Read rules and memory files
- Inspect recent session history
- Inspect current status and recent behavior
- Produce findings, priorities, and recommendations

Not allowed by default:
- Write files
- Patch rules
- Change gateway config
- Install or update skills
- Trigger destructive shell actions
- Start self-modification loops

## Review Workflow

Follow this sequence.

### 1. Define scope
Keep the review window small and recent.

Default scope:
- `AGENTS.md`
- `SOUL.md`
- `USER.md`
- `MEMORY.md`
- recent `memory/YYYY-MM-DD.md` files for the last 1-3 days
- recent session history relevant to the request

Prefer recent, high-signal context over exhaustive history.

### 2. Load context
Read only the context needed to answer:
- How is the agent supposed to behave?
- How has it behaved recently?
- Where are the gaps, drifts, or repeated issues?

Do not load large logs unless the review specifically requires them.

### 3. Extract signals
Convert raw context into structured signals in these groups:
- rule signals
- user preference signals
- interaction quality signals
- tooling reliability signals
- workflow signals

Examples:
- default language is Chinese
- responses should be conclusion-first
- risk should be stated before action
- some answers were too long
- a tool repeatedly failed on certain pages
- a recurring manual step should become a workflow

### 4. Analyze findings
Classify findings into:
- `rule_drift`
- `memory_hygiene`
- `interaction_quality`
- `tooling_reliability`
- `workflow_design`

For each finding, determine:
- symptom
- likely root cause
- confidence
- impact
- recommendation

Prefer repeated, meaningful patterns over one-off noise.

### 5. Plan actions
Convert findings into practical next actions.

Use these priorities:
- `P0`: safety issue or major rule conflict
- `P1`: repeated quality or workflow problem
- `P2`: useful but non-urgent improvement

Use these risk levels:
- `low`
- `medium`
- `high`

Default action types:
- `doc_update_suggestion`
- `memory_update_suggestion`
- `workflow_change_suggestion`
- `tool_fallback_suggestion`
- `no_action`

### 6. Render report
Produce a concise engineering-style review with:
1. Summary
2. Key findings
3. Priority actions
4. Safe next steps
5. Items to leave unchanged for now

Map every recommendation to a concrete target or workflow.

## Review Heuristics

- Report only issues that are repeated, meaningful, actionable, and aligned with the user's actual working style.
- Treat drift as a systems problem: check rules, memory capture, prompt load, tool mismatch, workflow misuse, and preference encoding.
- Prefer the smallest useful recommendation first: tighten one rule, promote one preference, add one workflow step, or define one fallback path.
- Review and recommend only; do not apply production changes by default.

## File Review Guidance

### `AGENTS.md`
Review for:
- operational rules
- execution boundaries
- session startup behavior
- messaging and channel behavior
- risk handling
- output structure defaults

Flag:
- duplicated rules
- conflicting rules
- vague rules that should be more executable

### `SOUL.md`
Review for:
- stable persona
- tone and boundaries
- decision posture
- trust and restraint model

Flag:
- tension between stated persona and observed behavior
- vague identity language that does not improve execution quality

### `USER.md`
Review for:
- stable user profile
- work background
- style preferences
- recurring topics
- collaboration expectations

Flag:
- stale assumptions
- repeated preferences missing from profile
- missing negative preferences

### `MEMORY.md`
Review for:
- stable long-term preferences
- durable collaboration context
- important decisions
- interaction defaults

Flag:
- short-term clutter
- missing durable preferences
- content that belongs in daily memory instead

### `memory/YYYY-MM-DD.md`
Review for:
- recent continuity
- significant events captured
- proper separation between temporary notes and long-term memory

Flag:
- important updates not recorded
- stable patterns not promoted when appropriate

## Session Review Guidance

When reviewing recent sessions, look for:
- repeated user corrections
- repeated requests for shorter or clearer answers
- tool choices that were suboptimal
- cases where risk should have been surfaced earlier
- missing memory capture after important decisions
- repeated work that should become a workflow

Do not overfit to one odd conversation. Require repeated evidence or strong signal before escalating.

## Tooling Reliability Guidance

If a tool appears unreliable, distinguish between:
- tool limitation
- environment limitation
- website structure change
- operator misuse
- missing fallback strategy

Example:
If `web_fetch` extracts little or no useful content, recommend a browser-based fallback instead of calling the tool broken.

## Workflow Design Guidance

Look for repeated work that should become a defined pattern, such as:
- recurring post-change memory logging
- repeated rules reconciliation across files
- repeated report formatting requests
- repeated use of one tool where another is better
- tasks that should move to cron or heartbeat

Recommend workflow change only when it reduces future manual effort.

## Output Format

Unless the user requests otherwise, use this structure:

### 1. 结论
State the overall assessment in 2-5 bullets.

### 2. 重点发现
Group findings by category. For each item, include:
- 现象
- 原因判断
- 影响
- 建议

### 3. 优先动作
List actions as `P0 / P1 / P2`.

### 4. 可安全推进项
Call out low-risk follow-ups suitable for a later approval step.

### 5. 暂不建议动作
Explicitly name changes that should not be made yet.

Keep the report compact, structured, and useful to an engineering lead.

## Internal Schemas

Use these structures internally for consistency.

### Finding
```json
{
  "id": "finding-001",
  "category": "interaction_quality",
  "severity": "medium",
  "confidence": 0.82,
  "symptom": "Some technical answers were too long before giving the conclusion.",
  "rootCause": "Analysis expansion happened before conclusion delivery.",
  "impact": "Increases reading cost and weakens executive usability.",
  "recommendation": "Default to conclusion-first structure in technical diagnosis responses."
}
```

### Action
```json
{
  "actionId": "action-001",
  "priority": "P1",
  "riskLevel": "low",
  "type": "doc_update_suggestion",
  "target": "AGENTS.md",
  "summary": "Reinforce conclusion-first technical response structure.",
  "why": "Repeatedly confirmed user preference and improves response usability.",
  "approvalRequired": true
}
```

Do not dump raw JSON to the user unless requested.

## Boundaries

V1 should not:
- edit files automatically
- rewrite rules automatically
- patch system config
- start unattended self-improvement loops
- claim autonomous self-evolution

V1 should:
- make the system easier to understand
- make improvement opportunities visible
- create clean handoff points for explicit follow-up approval

## Recommended Follow-up

After producing the report, recommend one of:
- no action
- prepare a patch draft
- update memory only
- refine a workflow
- schedule a periodic review

Do not execute follow-up changes unless explicitly asked.

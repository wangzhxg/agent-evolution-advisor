# Usage Examples

Use this file when you need a minimal, repeatable pattern for actually invoking the skill.

Keep usage read-only unless the user explicitly asks for follow-up execution.

---

## Standard Trigger Phrases

Use these short trigger phrases as default entry points.

### 1. General runtime review
User asks:
- 复盘最近 2 天 Agent 表现
- 复盘最近 7 天 Agent 表现
- 做一次 Agent 周复盘

Default scope:
- core rule files
- recent daily memory
- recent sessions
- overall runtime behavior

Default output:
- summary
- key findings
- priority actions
- safe next steps

### 2. Interaction quality review
User asks:
- 看一下最近回答质量
- 复盘最近回答风格
- 看看最近是不是又变啰嗦了

Focus on:
- conclusion-first behavior
- verbosity
- structure
- risk framing
- relay-friendly explanations

### 3. Rules drift review
User asks:
- 审一下规则漂移
- 检查一下规则文件有没有冲突
- 看看 AGENTS / SOUL / USER / MEMORY 有没有打架

Focus on:
- duplicated preferences
- conflicting instructions
- missing stable preferences
- stale wording
- unclear file ownership

### 4. Memory hygiene review
User asks:
- 看一下最近记忆维护质量
- 检查 MEMORY 和 daily memory 分层
- 看看哪些该进长期记忆

Focus on:
- long-term vs short-term separation
- missing durable preferences
- stale or noisy memory content
- promotion opportunities from daily memory

### 5. Tooling and workflow review
User asks:
- 看一下最近工具使用有没有低效点
- 复盘一下最近 workflow 设计
- 看看哪些动作该固化成流程
- 看一下最近工具和 workflow 有没有优化点

Focus on:
- repeated failed tool paths
- expensive tool choices
- missing fallback strategies
- repeated manual steps
- cron / heartbeat / workflow opportunities

---

## Default Review Windows

If the user says:
- “最近” → default to the last 2 days
- “周复盘” → default to the last 7 days

If evidence is missing for part of the requested window, say so briefly and continue with available context.

---

## Standard Review Template

Use this full template unless the user asks for a shorter format.

```md
## 结论
- 当前整体状态：
- 最主要的问题：
- 最值得优先处理的事项：

## 重点发现

### Rule Drift
- 现象：
- 原因判断：
- 影响：
- 建议：

### Memory Hygiene
- 现象：
- 原因判断：
- 影响：
- 建议：

### Interaction Quality
- 现象：
- 原因判断：
- 影响：
- 建议：

### Tooling Reliability
- 现象：
- 原因判断：
- 影响：
- 建议：

### Workflow Design
- 现象：
- 原因判断：
- 影响：
- 建议：

## 优先动作
- P0：
- P1：
- P2：

## 可安全推进项
- 低风险项 1
- 低风险项 2

## 暂不建议动作
- 暂不建议项 1
- 暂不建议项 2
```

---

## Short Review Template

Use this when the user wants a shorter answer or when the review scope is narrow.

```md
## 结论
- ...
- ...
- ...

## 重点发现
- 规则：
- 记忆：
- 回答质量：
- 工具 / 流程：

## 优先动作
- P1：
- P2：

## 暂不建议动作
- ...
- ...
```

---

## Safe Follow-up Phrasing

After the review, good follow-up suggestions include:
- 如果你愿意，我可以继续把这些建议整理成 patch 草案。
- 如果你愿意，我可以把低风险项先收敛成文档修改建议。
- 如果你愿意，我可以继续把其中一项展开成可执行的下一步方案。

Avoid follow-up phrasing that implies autonomous execution.

---

## Good Invocation Examples

### Example A
User:
- 复盘最近 2 天 Agent 表现

Expected behavior:
- run a general runtime review
- use the standard review template
- keep output concise and management-readable

### Example B
User:
- 看一下最近回答质量

Expected behavior:
- focus on interaction quality
- still mention major rule or workflow issues if they strongly affect answer quality
- prefer the short review template unless detail is clearly needed

### Example C
User:
- 审一下规则漂移

Expected behavior:
- focus on `AGENTS.md`, `SOUL.md`, `USER.md`, `MEMORY.md`
- prioritize conflict, duplication, missing stable preferences, and role boundaries
- avoid broad runtime commentary unless it directly supports the drift finding

### Example D
User:
- 看一下最近工具和 workflow 有没有优化点

Expected behavior:
- focus on tool choice, fallback paths, repeated manual steps, and process formalization opportunities
- avoid drifting into general style commentary unless it affects workflow efficiency

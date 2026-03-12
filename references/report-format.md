# Report Format

Use this file to keep review output stable, concise, and useful.

Default audience:
- engineering lead
- system operator
- long-term OpenClaw user

Default tone:
- calm
- direct
- practical
- low-noise
- risk-aware

Default language:
- Chinese first, unless the user explicitly requests English

---

## Core Output Rule

Default structure:

1. 结论
2. 重点发现
3. 优先动作
4. 可安全推进项
5. 暂不建议动作

Use this structure unless the user requests another format.

---

## Style Rules

Always:
- lead with the conclusion
- use short, explicit bullets
- tie each finding to an impact
- tie each recommendation to a concrete target
- distinguish fact, judgment, and suggestion
- keep management-readable structure

Avoid:
- long preambles
- generic advice
- overstating certainty
- repeating the same point in multiple sections
- dumping raw internal schema unless requested

---

## Short Review Format

Use for:
- quick audit
- daily review
- lightweight follow-up
- narrow-scope checks

### Template

```md
## 结论
- ...
- ...

## 重点发现
### [类别]
- 现象：
- 原因判断：
- 影响：
- 建议：

## 优先动作
- P1: ...
- P2: ...

## 可安全推进项
- ...

## 暂不建议动作
- ...
```

### Target length
- 5-15 bullets total
- compact enough to scan quickly

---

## Full Review Format

Use for:
- weekly review
- multi-file drift analysis
- runtime pattern diagnosis
- broader system improvement planning

### Template

```md
## 结论
- 总体状态：
- 主要风险：
- 最值得处理的事项：

## 重点发现

### 1. Rule Drift
- 现象：
- 原因判断：
- 影响：
- 建议：

### 2. Memory Hygiene
- 现象：
- 原因判断：
- 影响：
- 建议：

### 3. Interaction Quality
- 现象：
- 原因判断：
- 影响：
- 建议：

### 4. Tooling Reliability
- 现象：
- 原因判断：
- 影响：
- 建议：

### 5. Workflow Design
- 现象：
- 原因判断：
- 影响：
- 建议：

## 优先动作
- P0:
- P1:
- P2:

## 可安全推进项
- 低风险项 1
- 低风险项 2

## 暂不建议动作
- ...
- ...
```

### Target length
- concise but complete
- enough detail to act on
- avoid turning the review into a long essay

---

## Section Guidance

### 1. 结论
This section should answer:
- Is the system broadly healthy or drifting?
- What matters most right now?
- Does the user need to act?

Good examples:
- “当前整体规则已基本对齐，主要问题不在规则冲突，而在后续复盘流程尚未固化。”
- “近期交互质量总体稳定，但仍存在少量结论前置不够彻底的问题。”
- “工具层没有明显系统性故障，主要优化机会在 workflow 设计。”

Avoid:
- vague summaries
- rhetorical flourish
- repeating every detail here

---

### 2. 重点发现
For each finding, use:
- 现象
- 原因判断
- 影响
- 建议

This keeps the review operational.

Good pattern:
- 现象：用户近期多次要求结果更短、更像汇报
- 原因判断：输出模式仍偶尔偏分析展开
- 影响：增加阅读成本，降低管理场景可用性
- 建议：汇报类请求默认优先给分类版和精简版

---

### 3. 优先动作
Use explicit priority labels:
- `P0`
- `P1`
- `P2`

Only include real actions.

Good examples:
- `P1：将“重要规则变更后写 daily memory”固化为标准收尾动作`
- `P1：为内容抓取失败站点建立 web_fetch → browser fallback`
- `P2：进一步统一汇报类输出模板`

Avoid:
- vague aspirations
- items with no clear owner or target

---

### 4. 可安全推进项
This section should list low-risk follow-ups that are suitable for a later approval step.

Typical items:
- update `MEMORY.md`
- refine `AGENTS.md` wording
- add a reporting convention
- log a stable workflow into daily memory

Keep this section practical and bounded.

---

### 5. 暂不建议动作
This section is important.

Use it to prevent overreach:
- do not change config yet
- do not automate a process yet
- do not formalize a workflow with weak evidence
- do not treat a one-off anomaly as a system issue

This section shows restraint and improves trust.

---

## Reporting by Category

When possible, organize findings under these fixed categories:
- Rule Drift
- Memory Hygiene
- Interaction Quality
- Tooling Reliability
- Workflow Design

Use fewer categories only when the scope is narrow.

---

## Language Guidance

Default to Chinese output with concise engineering phrasing.

Prefer:
- “结论”
- “原因判断”
- “影响”
- “建议”
- “优先动作”
- “可安全推进项”
- “暂不建议动作”

Use English only for:
- file names
- technical terms
- explicit labels such as `P0 / P1 / P2`
- category names when useful

---

## Risk Wording Guidance

When a recommendation carries risk, state risk before action.

Good patterns:
- “风险较低，可作为下一步草案处理。”
- “该动作涉及规则层收敛，建议先审阅后再写入。”
- “当前证据不足，暂不建议固化为长期规则。”

Avoid:
- silent risk omission
- false certainty
- dramatic language

---

## Good Output Example

```md
## 结论
- 当前核心规则文件已基本对齐，没有明显冲突。
- 主要优化空间在交互风格稳定性和复盘流程固化。
- 暂无需要立即处理的高风险问题。

## 重点发现
### Interaction Quality
- 现象：部分长回答在结论前铺垫偏多。
- 原因判断：分析展开先于管理视角输出。
- 影响：增加阅读成本，削弱汇报场景可用性。
- 建议：技术与汇报类问题统一默认先给结论，再展开原因和建议动作。

### Workflow Design
- 现象：重要规则调整后的 daily memory 记录依赖人工提醒。
- 原因判断：缺少标准收尾动作。
- 影响：未来 session 上下文延续不稳定。
- 建议：将“规则变更后写入 daily memory”固化为标准流程。

## 优先动作
- P1：固化规则调整后的 memory 记录流程。
- P1：继续收紧结论优先的输出模板。
- P2：整理一版固定的 review 报告模板。

## 可安全推进项
- 为 `MEMORY.md` 补充更明确的长期偏好表达。
- 为规则变更建立固定收尾清单。

## 暂不建议动作
- 暂不引入自动写回或自动修复。
- 暂不根据单次异常调整长期规则。
```

---

## Bad Output Patterns

Avoid outputs like:
- “There are many areas for improvement...”
- “The system is somewhat inconsistent in some places...”
- “Maybe consider improving memory and workflow...”

These are too vague to be useful.

Also avoid:
- writing a long essay before the conclusion
- repeating the same issue in three sections
- proposing config or automation changes without evidence

---

## Recommendation Density

In most reviews:
- 1-3 key findings are enough
- 1-3 priority actions are enough
- more than 5 major actions usually means the review is under-prioritized

Prefer a short ranked list over a long unsorted list.

---

## Final Check Before Output

Before finalizing the report, verify:
- Is the conclusion clear within the first few lines?
- Are findings grouped and actionable?
- Are priorities explicit?
- Is risk stated where needed?
- Is anything overfit from weak evidence?
- Is the report short enough for fast scanning?

If not, tighten it.

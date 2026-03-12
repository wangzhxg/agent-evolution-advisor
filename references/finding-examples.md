# Finding Examples

Use this file when the review needs concrete examples of what counts as a valid finding.

The goal is to improve consistency:
- classify issues correctly
- avoid over-reporting noise
- connect symptoms to likely root causes
- recommend the smallest useful next action

Prefer repeated patterns over one-off anomalies.

---

## 1. `rule_drift`

Use this category when rules across core files are duplicated, inconsistent, stale, or insufficiently executable.

### Common signals
- The same preference appears in multiple files with different wording or different force
- A rule exists in one core file but is missing from another file that should reinforce it
- A recently established workflow has not been reflected in the rule system
- A rule is too vague to guide actual behavior
- Old wording still implies a behavior that no longer matches current expectations

### Good examples

#### Example A
**Symptom**  
`AGENTS.md` says responses should be conclusion-first, but recent updates in other files emphasize detailed explanation without reinforcing conclusion-first output.

**Likely root cause**  
Rules evolved in stages and were not reconciled across files.

**Recommendation direction**  
Tighten wording so conclusion-first structure is consistently encoded in the right files.

#### Example B
**Symptom**  
A stable preference such as “default to Chinese” appears in `USER.md` and recent daily memory, but is not reinforced in long-term memory or rule guidance.

**Likely root cause**  
Preference was learned in practice but not fully promoted into the stable rule layer.

**Recommendation direction**  
Promote the stable preference into the appropriate long-term file.

#### Example C
**Symptom**  
A rule says “be concise,” but another file encourages detailed explanations without clarifying when detail is appropriate.

**Likely root cause**  
Missing context-dependent guidance.

**Recommendation direction**  
Rewrite rules to express concise-by-default, detailed-when-needed behavior.

### What does NOT count
- Minor wording differences with the same practical meaning
- Stylistic variation that does not change behavior
- One-off phrasing choices in conversation that are not backed by rule changes

---

## 2. `memory_hygiene`

Use this category when memory capture is missing, noisy, misplaced, or poorly maintained.

### Common signals
- Stable preferences are missing from `MEMORY.md`
- Temporary details are polluting long-term memory
- Important events were discussed but never recorded
- Daily notes contain repeated long-term patterns that should be promoted
- Long-term memory contains stale or low-value fragments

### Good examples

#### Example A
**Symptom**  
The user repeatedly asks for shorter, structured responses, but the preference is only visible in recent sessions and not in `MEMORY.md`.

**Likely root cause**  
Stable collaboration preference has not been formalized in long-term memory.

**Recommendation direction**  
Promote this preference to `MEMORY.md`.

#### Example B
**Symptom**  
`MEMORY.md` contains task-specific or same-day details that are unlikely to matter next week.

**Likely root cause**  
Short-term notes were written into long-term memory.

**Recommendation direction**  
Move temporary items into `memory/YYYY-MM-DD.md` and keep long-term memory clean.

#### Example C
**Symptom**  
A major rule refactor happened, but the daily memory does not record it.

**Likely root cause**  
End-of-task memory logging was skipped.

**Recommendation direction**  
Record the change in the current daily memory file.

### What does NOT count
- Small omissions that do not affect future continuity
- One-off missing details that are already obvious from current context
- Temporary notes staying temporary in daily memory

---

## 3. `interaction_quality`

Use this category when recent responses do not match the desired communication style, structure, clarity, or usefulness.

### Common signals
- The answer delays the conclusion too long
- The answer is too verbose for the task
- The answer is too abstract and lacks actionable steps
- Risk was not surfaced early enough
- The answer is technically correct but hard to relay to another person
- The structure is inconsistent with known user preferences

### Good examples

#### Example A
**Symptom**  
Technical answers spend several paragraphs on context before stating the conclusion.

**Likely root cause**  
Reasoning was presented before executive summary.

**Recommendation direction**  
Default to: conclusion → cause → suggested action.

#### Example B
**Symptom**  
A report-style request receives a broad narrative answer instead of a concise management-readable structure.

**Likely root cause**  
Output mode was not adapted to the user’s reporting context.

**Recommendation direction**  
Use categorized bullets and short impact-oriented phrasing.

#### Example C
**Symptom**  
A potentially risky operation is described without clearly stating the risk first.

**Likely root cause**  
Action guidance outran safety framing.

**Recommendation direction**  
Surface risk before execution advice in high-risk scenarios.

### What does NOT count
- Small stylistic variation with no user impact
- Slightly longer answers when the user explicitly asked for detail
- Rich explanation when complexity genuinely requires it

---

## 4. `tooling_reliability`

Use this category when tools, fetch paths, or execution choices are repeatedly suboptimal or fragile.

### Common signals
- The same tool fails repeatedly in a similar context
- A better fallback exists but is not used
- The agent uses a heavy tool when a lighter one would do
- The agent retries a weak path instead of switching approach
- Page extraction repeatedly fails on a known site pattern

### Good examples

#### Example A
**Symptom**  
`web_fetch` returns little useful content on a dynamic site, and the agent has to re-do the task in a browser.

**Likely root cause**  
The site structure is not compatible with readability-based extraction.

**Recommendation direction**  
Define a fetch-to-browser fallback rule for similar pages.

#### Example B
**Symptom**  
A multi-step manual read/edit workflow is repeated for the same kind of simple file change.

**Likely root cause**  
No reusable workflow or script pattern has been established yet.

**Recommendation direction**  
Document a preferred editing path or later consider script support.

#### Example C
**Symptom**  
A task repeatedly uses an interactive browser path when plain text fetch would have been enough.

**Likely root cause**  
Tool selection defaults are not optimized for cost and speed.

**Recommendation direction**  
Prefer lightweight fetch for content extraction, use browser only when interaction or structure requires it.

### What does NOT count
- One-off tool failures caused by transient network or page issues
- Cases where fallback was quickly and correctly applied
- Situations where the chosen tool was slower but still appropriate

---

## 5. `workflow_design`

Use this category when repeated work should be formalized into a workflow, or when tasks are being routed through the wrong operational mechanism.

### Common signals
- The same cleanup or logging step is manually repeated
- A reminder-like task is handled conversationally instead of by cron
- A recurring audit has no scheduled process
- Repeated document updates have no approval flow
- The agent repeatedly solves the same coordination problem from scratch

### Good examples

#### Example A
**Symptom**  
After important rule changes, the system often forgets to record the update in daily memory unless the user explicitly asks.

**Likely root cause**  
No standard post-change workflow exists.

**Recommendation direction**  
Define a standard “change completed → log to daily memory” step.

#### Example B
**Symptom**  
Time-based reminders are handled ad hoc in conversation.

**Likely root cause**  
Cron is underused for reminder-style tasks.

**Recommendation direction**  
Move exact-time reminders to cron.

#### Example C
**Symptom**  
The same kind of deployment review is repeatedly requested manually with similar framing.

**Likely root cause**  
A reusable audit workflow exists conceptually but is not formalized.

**Recommendation direction**  
Create a standard review pattern or skill.

### What does NOT count
- Rare tasks that do not justify formalization
- Personal preferences that should stay flexible
- One-off coordination friction without repeat evidence

---

## Severity Calibration

Use severity conservatively.

### `low`
- Cosmetic or mild friction
- Limited impact
- Easy to defer

### `medium`
- Repeated quality or workflow issue
- Noticeable productivity cost
- Worth acting on soon

### `high`
- Safety, privacy, or strong usability degradation
- Major rule conflict
- Repeated failure with broad impact

Do not use `high` for ordinary style tuning.

---

## Confidence Calibration

Use confidence to reflect evidence quality.

### High confidence
Use when:
- the pattern repeats
- evidence is explicit
- the issue clearly maps to a known preference or rule

### Medium confidence
Use when:
- the pattern is plausible but limited
- there is some ambiguity in root cause

### Low confidence
Use when:
- evidence is thin
- the issue may be situational
- the observed behavior may have been intentional

If confidence is low, recommend observation or light follow-up instead of strong action.

---

## Recommendation Rules

For each finding, prefer the smallest useful recommendation.

Good recommendations:
- tighten one rule
- promote one stable preference into memory
- add one workflow step
- define one fallback path
- leave the system unchanged but monitor

Avoid oversized recommendations unless the problem is clearly systemic.

---

## Non-Findings

Do not report a finding when:
- the issue is one-off and low impact
- the evidence is too weak
- the variance is harmless
- the user explicitly asked for a different response mode
- the proposed “problem” is actually intentional behavior

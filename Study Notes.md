# Claude Certified Architect – Foundations: Study Notes

> A condensed review of what each task statement expects you to know. Unofficial; written from the exam guide's task statements. Always check the current official exam guide before your sitting.

---

## How the Exam Thinks

Most questions give four options that all sound reasonable. The correct one usually follows one of these patterns:

| If the question is about... | The exam prefers... | Over... |
|---|---|---|
| A rule that must never be broken (money, identity, compliance) | Programmatic enforcement: hooks, prerequisite gates | Stronger prompt wording, few-shot examples |
| Wrong tool being selected | Better tool descriptions, renaming, splitting | Routing classifiers, system prompt lists |
| Inconsistent or noisy output | Explicit criteria and concrete examples | "Be careful", "be conservative", "only high confidence" |
| Inconsistent format | 2-4 few-shot examples | Longer prose instructions |
| Guaranteed structure | Tool use with a JSON schema | "Return valid JSON" instructions, regex repair |
| Deciding when to stop or escalate | Explicit signals (`stop_reason`, explicit criteria) | Text parsing, sentiment, self-reported confidence |
| A subagent that lacks information | Pass it explicitly in the subagent's prompt | Assuming inherited context or shared memory |
| Errors | Structured error context so the caller can decide | Silent empty success, generic "failed", aborting everything |
| Quality problems in a long single pass | Focused passes plus an integration pass | Bigger model, bigger context window |
| Reviewing generated work | An independent instance | The same session reviewing itself |
| A fix proportional to the problem | The smallest change that addresses the root cause | Re-architecting, new infrastructure, a separate model |

Wrong options tend to be: over-engineered, probabilistic where a guarantee is needed, aimed at a different problem than the one described, or based on a feature that does not exist.

---

## Domain 1: Agentic Architecture & Orchestration (27%)

**1.1 Agentic loops**
- Loop control is driven by `stop_reason`: continue on `"tool_use"`, stop on `"end_turn"`.
- Tool results are appended to the conversation history so the model can reason about them on the next iteration.
- Anti-patterns: parsing natural-language text for completion, treating the presence of assistant text as "done", using an arbitrary iteration cap as the primary stopping mechanism. A cap is acceptable as a safety net.

**1.2 Coordinator-subagent orchestration**
- Hub-and-spoke: the coordinator handles all inter-subagent communication, error handling, and routing.
- Subagents have isolated context. They do not inherit the coordinator's history.
- The coordinator selects which subagents a query needs instead of always running the full pipeline.
- Overly narrow decomposition by the coordinator causes coverage gaps even when every subagent succeeds.
- Iterative refinement: evaluate synthesis output for gaps, re-delegate targeted work, re-invoke synthesis.

**1.3 Subagent invocation and context passing**
- Subagents are spawned with the `Task` tool; the coordinator's `allowedTools` must include `"Task"`.
- `AgentDefinition` configures each subagent's description, system prompt, and tool restrictions.
- Everything a subagent needs goes in its prompt, in structured form that keeps content attached to metadata (source URLs, dates, page numbers).
- Parallel subagents: emit multiple `Task` calls in a single coordinator response.
- Coordinator prompts specify goals and quality criteria, not step-by-step procedures.

**1.4 Workflow enforcement and handoff**
- When a tool sequence is critical (verify identity before refunding), enforce it programmatically. Prompts have a non-zero failure rate.
- Multi-concern requests: decompose into distinct items, investigate in parallel with shared context, give one unified response.
- Escalation handoff: a structured summary (customer ID, root cause, amounts, recommended action) because the human may not have the transcript.

**1.5 Hooks**
- `PostToolUse` hooks intercept tool results to normalize heterogeneous formats (timestamps, status codes) or trim them before the model sees them.
- Tool call interception hooks block policy-violating actions (for example refunds above a threshold) and redirect to an alternative workflow.
- Hooks give deterministic guarantees; prompts give probabilistic compliance. Choose hooks when the rule must always hold.

**1.6 Task decomposition**
- Prompt chaining (fixed sequential steps) for predictable, multi-aspect work, such as per-file analysis followed by a cross-file integration pass.
- Dynamic adaptive decomposition for open-ended investigation where scope is unknown: map structure, identify high-impact areas, build a prioritized plan that adapts.

**1.7 Sessions**
- `--resume <session-name>` continues a named session. Tell the agent which files changed so it re-analyzes them.
- `fork_session` creates independent branches from a shared baseline to explore divergent approaches.
- If prior tool results are broadly stale, a new session with an injected structured summary is more reliable than resuming.

---

## Domain 2: Tool Design & MCP Integration (18%)

**2.1 Tool interfaces**
- Tool descriptions are the primary mechanism for tool selection. Include input formats, example queries, edge cases, and boundaries versus similar tools.
- Fix overlap by renaming and rewriting descriptions; split generic tools into purpose-specific tools with defined contracts.
- Keywords in the system prompt can create unintended tool associations that override descriptions.

**2.2 Structured errors**
- MCP tools signal failure with the `isError` flag.
- Return structured metadata: `errorCategory` (transient, validation, business, permission), `isRetryable`, and a human-readable explanation.
- Distinguish an access failure (retry may help) from a valid empty result (a successful query with no matches).
- Business rule violations are non-retryable and need a customer-appropriate explanation.
- Subagents recover from transient failures locally and propagate only what they cannot resolve, with partial results and what was attempted.

**2.3 Tool distribution and `tool_choice`**
- Too many tools (for example 18 instead of 4-5) degrades selection; out-of-role tools get misused.
- Scope tools to each agent's role; add a narrowly scoped tool for a high-frequency need and route the rest through the coordinator.
- Replace generic tools with constrained alternatives (`fetch_url` becomes `load_document` with validation).
- `tool_choice`: `"auto"` may return text; `"any"` must call some tool; `{"type": "tool", "name": "..."}` forces a specific tool.
- To guarantee an order, force the first tool on the first request and handle later steps in follow-up turns.

**2.4 MCP servers**
- Project scope: `.mcp.json` (shared, committed). User scope: `~/.claude.json` (personal, experimental).
- Use environment variable expansion such as `${GITHUB_TOKEN}` in `.mcp.json`; never commit secrets.
- Tools from all configured servers are discovered at connection time and available together.
- MCP resources expose content catalogs (issue summaries, documentation hierarchies, schemas) to reduce exploratory tool calls.
- Write rich MCP tool descriptions, or the agent will prefer familiar built-ins like `Grep`.
- Prefer existing community servers for standard integrations (Jira); build custom servers for team-specific workflows.

**2.5 Built-in tools**
- `Grep` searches file contents. `Glob` matches file paths by pattern (`**/*.test.tsx`).
- `Read` and `Write` for whole files; `Edit` for targeted changes using unique text matching.
- When `Edit` fails because the match is not unique, fall back to `Read` plus `Write`.
- Explore incrementally: `Grep` for entry points, then `Read` and follow imports. Do not read everything upfront.

---

## Domain 3: Claude Code Configuration & Workflows (20%)

**3.1 CLAUDE.md hierarchy**
- User level: `~/.claude/CLAUDE.md` (not shared). Project level: `CLAUDE.md` or `.claude/CLAUDE.md` (committed). Directory level: `CLAUDE.md` in a subdirectory.
- A teammate or CI runner not following conventions usually means the instructions live at user level.
- `@` import syntax keeps files modular; `.claude/rules/` holds topic-specific rule files.
- `/memory` shows which memory files are loaded; use it to diagnose inconsistent behavior.

**3.2 Commands and skills**
- Project commands: `.claude/commands/` (shared via version control). Personal commands: `~/.claude/commands/`.
- Skills: `.claude/skills/` with a `SKILL.md`. Frontmatter includes `context: fork` (run in an isolated sub-agent context so verbose output stays out of the main session), `allowed-tools` (restrict tool access), and `argument-hint` (prompt for required parameters).
- Personal variants go in `~/.claude/skills/` under a different name.
- Skills are on-demand, task-specific workflows. `CLAUDE.md` is always-loaded universal standards.

**3.3 Path-specific rules**
- `.claude/rules/*.md` files with YAML frontmatter `paths:` glob patterns load only when Claude works on matching files.
- Best for conventions that follow a file type across many directories (test files). Directory-level `CLAUDE.md` cannot do that.

**3.4 Plan mode vs direct execution**
- Plan mode: large-scale changes, multiple valid approaches, architectural decisions, multi-file modifications.
- Direct execution: simple, well-scoped changes with a clear fix.
- The Explore subagent isolates verbose discovery and returns a summary, preserving main-session context.
- Combining is normal: plan mode to investigate, direct execution to implement.

**3.5 Iterative refinement**
- Concrete input/output examples when prose instructions are interpreted inconsistently.
- Test-driven iteration: write tests first, then share failures to guide improvement.
- Interview pattern: have Claude ask questions to surface considerations before implementing in an unfamiliar domain.
- Interacting issues go in one message; independent issues are fixed sequentially.

**3.6 CI/CD**
- `-p` / `--print` runs Claude Code non-interactively. Without it, a pipeline job hangs waiting for input.
- `--output-format json` with `--json-schema` produces machine-parseable structured findings.
- `CLAUDE.md` gives CI-invoked Claude its project context: testing standards, fixtures, review criteria.
- Review generated code with an independent instance, not the session that wrote it.
- On re-runs, include prior findings and ask for only new or unaddressed issues. Provide existing tests to avoid duplicate test suggestions.

---

## Domain 4: Prompt Engineering & Structured Output (20%)

**4.1 Explicit criteria**
- Specific, categorical criteria (what to flag, what to skip) beat vague instructions like "be conservative".
- High false-positive rates in one category erode trust in all categories. Temporarily disable the noisy category while you fix its criteria.
- Define severity levels with concrete code examples for each level.

**4.2 Few-shot prompting**
- The most effective technique for consistent format when instructions alone are not enough.
- Use 2-4 targeted examples for ambiguous cases, showing the reasoning for the choice.
- Examples help the model generalize to novel patterns, handle varied document structures, and reduce fabrication in extraction.

**4.3 Structured output**
- Tool use with a JSON schema is the most reliable route to schema-compliant output. It eliminates syntax errors.
- It does not prevent semantic errors: wrong field, totals that do not sum.
- Make fields nullable or optional when the source may not contain the value; required fields invite fabrication.
- Enums: add `"other"` with a detail string for extensibility, and `"unclear"` for ambiguous cases.
- `tool_choice: "any"` when the document type is unknown and several extraction tools exist.

**4.4 Validation and retry**
- Retry with feedback: resend the document, the failed extraction, and the specific validation error.
- Retries do not help when the information is absent from the source. Check before retrying again.
- Self-correction fields: `calculated_total` next to `stated_total`, `conflict_detected` flags.
- A `detected_pattern` field on findings supports systematic analysis of false positives.

**4.5 Batch processing**
- Message Batches API: 50% cost savings, up to 24-hour processing window, no latency SLA.
- Use it for non-blocking, latency-tolerant work (overnight reports, audits). Keep blocking workflows (pre-merge checks) synchronous.
- No multi-turn tool calling inside a single batch request.
- `custom_id` correlates requests with responses. Resubmit only failures, with a fix (for example chunking oversized documents).
- Derive submission frequency from the SLA: maximum wait before submission plus 24 hours must fit the deadline.
- Refine the prompt on a sample set before submitting at volume.

**4.6 Multi-instance and multi-pass review**
- A model that keeps its generation reasoning is less likely to question its own decisions.
- Independent review instances catch more than self-review instructions or extended thinking.
- Large reviews: per-file local passes plus a cross-file integration pass, to avoid attention dilution and contradictory findings.
- Verification passes can report confidence per finding to support calibrated review routing.

---

## Domain 5: Context Management & Reliability (15%)

**5.1 Preserving context**
- Progressive summarization loses numbers, dates, percentages, and customer-stated expectations.
- Keep transactional facts in a persistent "case facts" block outside the summarized history.
- "Lost in the middle": put key findings at the start of long inputs and use explicit section headers.
- Trim verbose tool results to relevant fields before they accumulate in context.

**5.2 Escalation and ambiguity**
- Escalate when: the customer explicitly asks for a human, policy is silent or an exception is needed, or the agent cannot make progress.
- Honor an explicit request for a human immediately, without investigating first.
- Frustration without a request: acknowledge it and offer resolution; escalate if the customer reiterates.
- Sentiment and self-reported confidence are unreliable proxies for complexity.
- Multiple customer matches: ask for another identifier; do not pick by heuristic.

**5.3 Error propagation**
- Return structured error context: failure type, what was attempted, partial results, possible alternatives.
- Anti-patterns: silently returning an empty success, generic "search unavailable", terminating the whole workflow on one failure.
- Synthesis output should annotate coverage gaps so readers know which findings are well supported.

**5.4 Large codebase exploration**
- Context degradation shows up as inconsistent answers and references to "typical patterns" instead of specific classes found earlier.
- Scratchpad files persist key findings across context boundaries.
- Delegate verbose exploration to subagents; the coordinator keeps the high-level picture.
- Crash recovery: agents export state to a known location; the coordinator loads a manifest on resume.
- `/compact` reduces context usage during long sessions but can lose detail.

**5.5 Human review and confidence**
- Aggregate accuracy (for example 97%) can hide poor performance on specific document types or fields. Validate by segment before reducing human review.
- Stratified random sampling of high-confidence extractions measures ongoing error rates and catches new error patterns.
- Field-level confidence, calibrated on a labeled validation set, routes reviewer attention.

**5.6 Provenance and uncertainty**
- Source attribution is lost when findings are summarized without claim-source mappings. Require structured mappings and preserve them through synthesis.
- Conflicting statistics from credible sources: report both with attribution; do not pick one arbitrarily.
- Include publication or collection dates so differences over time are not read as contradictions.
- Reports should separate well-established findings from contested ones.

---

## Topics the Exam Guide Treats as Out of Scope

Fine-tuning, API authentication and billing, deploying or hosting MCP servers, Claude's internal architecture or training, constitutional AI and safety training, embeddings and vector databases, computer use, vision, streaming, rate limits and quotas, OAuth and key rotation, cloud provider configuration, performance benchmarking, prompt caching implementation details, and token-counting algorithms. Confirm this list against the current official guide.

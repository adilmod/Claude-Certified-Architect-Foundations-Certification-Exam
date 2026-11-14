# Claude Certified Architect – Foundations: Practice Exam

> 124 scenario-based questions | 6 scenarios | 5 domains | Unofficial community resource

---

## Exam Format

- **Format:** Multiple choice, 4 options per question (1 correct, 3 distractors)
- **Structure:** Questions are framed by production scenarios. A real sitting is reported to draw 4 of the 6 scenarios below, for about 60 questions.
- **Unanswered questions:** Scored as incorrect. No penalty for guessing.
- **Scoring:** Scaled score 100-1,000. Minimum passing score: **720**. The raw-to-scaled conversion is not published.

## How to Use This File

- Questions are grouped by scenario and mixed across domains within each scenario, as in the exam. The task statement a question tests is shown only after its answer.
- Correct answers are evenly distributed across A-D. If you find yourself picking by position or option length, you are not testing knowledge.
- **Readiness target:** aim for 85%+ on questions you have not seen before, with no domain under 75%. A bare 70% here is not evidence you will pass.
- For every question you miss, re-read the explanation for all four options. The exam rewards knowing why the distractors are wrong.
- Answers follow the official exam guide. Where the current product has changed since the guide was written, the guide's terminology is used.

---

## Content Domains

| Domain | Topic | Exam Weight | Questions in This Bank |
|--------|-------|-------------|------------------------|
| 1 | Agentic Architecture & Orchestration | 27% | 31 (25%) |
| 2 | Tool Design & MCP Integration | 18% | 22 (18%) |
| 3 | Claude Code Configuration & Workflows | 20% | 24 (19%) |
| 4 | Prompt Engineering & Structured Output | 20% | 27 (22%) |
| 5 | Context Management & Reliability | 15% | 20 (16%) |

---

## Scenario Index

| Scenario | Title | Questions |
|----------|-------|-----------|
| 1 | Customer Support Resolution Agent | Q1-Q21 (21) |
| 2 | Code Generation with Claude Code | Q22-Q41 (20) |
| 3 | Multi-Agent Research System | Q42-Q63 (22) |
| 4 | Developer Productivity with Claude | Q64-Q83 (20) |
| 5 | Claude Code for Continuous Integration | Q84-Q103 (20) |
| 6 | Structured Data Extraction | Q104-Q124 (21) |

---

## Domain-Task Index

### Domain 1: Agentic Architecture & Orchestration (27%)

| Task | Description | Questions |
|------|-------------|-----------|
| 1.1 | Design and implement agentic loops for autonomous task execution | Q4, Q7, Q53, Q70, Q77 |
| 1.2 | Orchestrate multi-agent systems with coordinator-subagent patterns | Q47, Q50, Q51, Q55, Q58, Q63 |
| 1.3 | Configure subagent invocation, context passing, and spawning | Q44, Q46, Q48, Q61, Q84 |
| 1.4 | Implement multi-step workflows with enforcement and handoff patterns | Q5, Q20, Q21 |
| 1.5 | Apply Agent SDK hooks for tool call interception and data normalization | Q9, Q15, Q19, Q73, Q76 |
| 1.6 | Design task decomposition strategies for complex workflows | Q64, Q68, Q96, Q106 |
| 1.7 | Manage session state, resumption, and forking | Q27, Q29, Q81 |

### Domain 2: Tool Design & MCP Integration (18%)

| Task | Description | Questions |
|------|-------------|-----------|
| 2.1 | Design effective tool interfaces with clear descriptions and boundaries | Q2, Q8, Q13, Q109 |
| 2.2 | Implement structured error responses for MCP tools | Q1, Q6, Q54, Q62 |
| 2.3 | Distribute tools appropriately across agents and configure tool_choice | Q11, Q42, Q45, Q59, Q116 |
| 2.4 | Integrate MCP servers into Claude Code and agent workflows | Q66, Q67, Q69, Q80, Q82 |
| 2.5 | Select and apply built-in tools (Read, Write, Edit, Bash, Grep, Glob) effectively | Q71, Q72, Q74, Q75 |

### Domain 3: Claude Code Configuration & Workflows (20%)

| Task | Description | Questions |
|------|-------------|-----------|
| 3.1 | Configure CLAUDE.md files with appropriate hierarchy, scoping, and modular organization | Q24, Q26, Q28, Q38, Q93 |
| 3.2 | Create and configure custom slash commands and skills | Q30, Q34, Q35, Q83 |
| 3.3 | Apply path-specific rules for conditional convention loading | Q33, Q37 |
| 3.4 | Determine when to use plan mode vs direct execution | Q23, Q25, Q41 |
| 3.5 | Apply iterative refinement techniques for progressive improvement | Q22, Q32, Q36, Q39, Q40 |
| 3.6 | Integrate Claude Code into CI/CD pipelines | Q86, Q91, Q92, Q95, Q98 |

### Domain 4: Prompt Engineering & Structured Output (20%)

| Task | Description | Questions |
|------|-------------|-----------|
| 4.1 | Design prompts with explicit criteria to improve precision and reduce false positives | Q89, Q90, Q99, Q103 |
| 4.2 | Apply few-shot prompting to improve output consistency and quality | Q97, Q101, Q105, Q110, Q124 |
| 4.3 | Enforce structured output using tool use and JSON schemas | Q111, Q112, Q113, Q120, Q121 |
| 4.4 | Implement validation, retry, and feedback loops for extraction quality | Q88, Q107, Q115, Q117 |
| 4.5 | Design efficient batch processing strategies | Q87, Q94, Q100, Q108, Q118, Q122 |
| 4.6 | Design multi-instance and multi-pass review architectures | Q31, Q85, Q102 |

### Domain 5: Context Management & Reliability (15%)

| Task | Description | Questions |
|------|-------------|-----------|
| 5.1 | Manage conversation context to preserve critical information across long interactions | Q3, Q10, Q56 |
| 5.2 | Design effective escalation and ambiguity resolution patterns | Q12, Q14, Q16, Q17, Q18 |
| 5.3 | Implement error propagation strategies across multi-agent systems | Q49, Q52 |
| 5.4 | Manage context effectively in large codebase exploration | Q65, Q78, Q79 |
| 5.5 | Design human review workflows and confidence calibration | Q104, Q114, Q119, Q123 |
| 5.6 | Preserve information provenance and handle uncertainty in multi-source synthesis | Q43, Q57, Q60 |

---

## Scenario 1: Customer Support Resolution Agent

You are building a customer support resolution agent using the Claude Agent SDK. The agent handles high-ambiguity requests like returns, billing disputes, and account issues. It has access to your backend systems through custom MCP tools (`get_customer`, `lookup_order`, `process_refund`, `escalate_to_human`). Target: 80%+ first-contact resolution while knowing when to escalate.

**Primary domains:** Domain 1, Domain 2, Domain 5

---

**Q1.** Your MCP tool `check_fraud_risk` returns `{"isError": true, "message": "Refund blocked"}` when a refund is flagged by fraud detection. The agent interprets this as a transient failure and retries the refund three times before giving up. Each retry generates a separate fraud alert in your compliance system.

What is the missing element in the error response design?

A) The tool should suppress the `isError` flag for fraud blocks and instead return the result as a successful response with a `blocked: true` field.
B) The response should include `isRetryable: false` and a customer-appropriate explanation distinguishing this business rule block from a transient system error.
C) The response should include the fraud risk score so the agent can decide whether the score is high enough to justify blocking.
D) The response should include a `retry_after` timestamp so the agent knows when to retry.

**Correct Answer: B**
*Task 2.2: Implement structured error responses for MCP tools*

A business rule block from fraud detection is a non-retryable error. Including `isRetryable: false` signals to the agent that retrying will not resolve the situation, preventing redundant attempts that trigger compliance alerts. A customer-appropriate explanation helps the agent communicate the block appropriately. Option D implies the block is temporary and retriable, which is the opposite of the intended behavior. Option A hides the error nature of the response and makes recovery logic less clear. Option C provides fraud risk data to the agent that it may not be authorized to act on directly.

---

**Q2.** Production logs show the agent frequently calls `get_customer` when users ask about orders, instead of calling `lookup_order`. Both tools have minimal descriptions and accept similar identifier formats. What's the most effective first step to improve tool selection reliability?

A) Consolidate both tools into a single `lookup_entity` tool that accepts any identifier and internally determines which backend to query.
B) Expand each tool's description to include input formats it handles, example queries, edge cases, and boundaries explaining when to use it versus similar tools.
C) Implement a routing layer that parses user input before each turn and pre-selects the appropriate tool based on detected keywords.
D) Add few-shot examples to the system prompt demonstrating correct tool selection patterns, with 5-8 examples.

**Correct Answer: B**
*Task 2.1: Design effective tool interfaces with clear descriptions and boundaries*

Tool descriptions are the primary mechanism LLMs use for tool selection. Option B directly addresses the root cause. Few-shot examples (D) add token overhead without fixing the underlying issue. A routing layer (C) is over-engineered. Consolidating tools (A) requires more effort than a "first step" warrants.

---

**Q3.** A customer support agent is handling a complex billing dispute that spans 20+ turns. A customer mentioned early in the conversation that they were charged $847.50 on March 3rd for a service they cancelled on February 28th. Midway through the conversation, the agent references the charge as "the overcharge from last month" without the specific amount. The customer disputes the agent's understanding of the case. What context management technique would prevent this?

A) Extract transactional facts (amounts, dates, order numbers) into a persistent case-facts block included in every prompt.
B) Instruct the agent to re-read the full conversation history before each response.
C) Increase the model's context window by switching to a larger tier to retain the full conversation without summarization.
D) Use `/compact` at the start of each conversation to summarize prior turns into a shorter representation.

**Correct Answer: A**
*Task 5.1: Manage conversation context to preserve critical information across long interactions*

Extracting precise transactional facts into a persistent "case facts" block ensures that specific numerical values, dates, and customer-stated details are explicitly available in every prompt turn rather than buried in growing conversation history. Progressive summarization risks condensing these details into vague references like "overcharge from last month." Option D's compaction is useful for context length management but can lose precision on transactional facts. Option C does not prevent progressive summarization and is not a reliable solution. Option B is not practical for long conversations and still does not prevent facts from being lost as context grows.

---

**Q4.** You are building a customer support agent using the Claude Agent SDK. The agent processes billing disputes by calling tools like `lookup_order`, `get_invoice`, and `process_refund`. A code review notes that after each tool call, your loop checks whether Claude's response text contains the phrase "I have completed" to decide whether to stop.

What is the primary problem with this loop termination approach?

A) Phrase matching is too strict; the loop should instead stop whenever a response contains any text block, since text means Claude is done.
B) Natural-language signals are unreliable for termination; the loop should continue on `stop_reason` `"tool_use"` and stop on `"end_turn"`.
C) The loop should terminate as soon as any tool call fails, since continuing after a failure will corrupt the conversation history.
D) The check runs only after tool execution, so the loop always makes one extra API call before it can detect completion.

**Correct Answer: B**
*Task 1.1: Design and implement agentic loops for autonomous task execution*

Inspecting `stop_reason` is the canonical method for agentic loop control: continue while it is `"tool_use"`, stop when it is `"end_turn"`. Claude's phrasing varies across responses and prompt updates, so text matching is not a reliable signal. Option D misdiagnoses the problem as an efficiency issue. Option C would abort recoverable workflows; failed tool calls should be returned to the model as results so it can adapt. Option A swaps one anti-pattern for another: responses often contain text alongside `tool_use` blocks.

---

**Q5.** A customer contacts your support agent about three issues in a single message: a billing charge dispute, a missing order, and a request to update their email address. The agent processes these sequentially, taking 3-4 minutes per request. A senior architect suggests you redesign the handling approach.

What design change would most improve efficiency while maintaining accuracy?

A) Instruct the agent to address only the highest-priority issue per conversation turn and ask the customer to submit separate tickets for the remaining issues.
B) Decompose the three concerns into distinct investigation items and process each in parallel using shared customer context, then compile a unified response.
C) Process the three issues sequentially but cache intermediate results so subsequent issues benefit from data already retrieved.
D) Delegate all three issues to a single specialized "multi-issue" subagent that handles complex requests with multiple concerns.

**Correct Answer: B**
*Task 1.4: Implement multi-step workflows with enforcement and handoff patterns*

When a customer presents multiple independent concerns, decomposing them into parallel investigation items dramatically reduces latency. Each concern can be investigated simultaneously using the shared customer context already retrieved. Option A creates a poor customer experience and extra work for the customer. Option C improves caching but does not eliminate the serial bottleneck. Option D creates an undifferentiated subagent that doesn't reflect the coordinator-subagent specialization pattern.

---

**Q6.** Your customer support MCP tool `process_refund` returns the same error response for all failures: `{"status": "error", "message": "Operation failed"}`. The agent currently handles all errors by apologizing to the customer and ending the conversation. Logs show this response is triggered by: network timeouts, invalid refund amounts, refunds blocked by fraud detection, and expired order IDs.

What structured error response design would most improve the agent's ability to recover appropriately?

A) Return structured metadata: an `errorCategory` (transient/validation/permission/business), an `isRetryable` flag, and a specific explanation.
B) Return a numeric error code and have the system prompt map each code to a recovery action.
C) Return a different HTTP status code for each failure type and have the agent interpret the status code to determine the right recovery action.
D) Return a verbose error log with the full stack trace and system state so the agent has maximum information to reason from.

**Correct Answer: A**
*Task 2.2: Implement structured error responses for MCP tools*

Structured error metadata gives the agent the information it needs to choose the correct recovery path: retry a transient failure, ask the customer for corrected input on a validation failure, or explain a policy block on a business rule violation. Option C relies on HTTP semantics that may not map cleanly to all failure categories and are not as expressive as structured fields. Option D provides excessive detail that consumes context without improving decision quality. Option B encodes recovery logic in the system prompt rather than in a principled error structure, making it harder to maintain.

---

**Q7.** Your agent loop sends tool results back to Claude and stops as soon as a response contains a text block. In testing, the agent often says "Let me look up that order for you" and the session ends without the lookup ever running. What is the cause?

A) The response carried both text and a `tool_use` block; the loop must continue whenever `stop_reason` is `"tool_use"`.
B) The tool definitions lack detailed descriptions, so Claude announces the lookup but cannot work out which tool to call.
C) The `max_tokens` value is too low, so each response is cut off before Claude can emit the tool call it announced.
D) The system prompt lets Claude narrate its actions; it should be told to emit tool calls without any accompanying text.

**Correct Answer: A**
*Task 1.1: Design and implement agentic loops for autonomous task execution*

Treating the presence of assistant text as a completion signal is an anti-pattern: Claude frequently emits text alongside tool calls. The loop should be driven by `stop_reason`, executing tools and continuing on `"tool_use"` and stopping on `"end_turn"`. Option D suppresses a symptom and leaves the loop logic wrong. Option C would surface as a `"max_tokens"` stop reason, not as a normal response with text. Option B would cause wrong tool selection, not a session that ends early.

---

**Q8.** Your customer support agent has a `lookup_order` tool that is called at the right times, but frequently returns errors. Logs show the agent passes free-text descriptions like "order from last Tuesday" instead of the required ISO-8601 timestamp format. The tool description reads: "Retrieves order details given a date or identifier." No examples or format constraints are provided.

What change to the tool definition would most directly reduce these input format errors?

A) Add a system prompt instruction: "Always use ISO-8601 format when calling lookup_order."
B) Add format constraints and example inputs to the tool description so the model knows how to format the date argument.
C) Add input schema validation that rejects malformed inputs and returns an error to the agent.
D) Split `lookup_order` into two tools: `lookup_order_by_id` and `lookup_order_by_date` to reduce ambiguity.

**Correct Answer: B**
*Task 2.1: Design effective tool interfaces with clear descriptions and boundaries*

Tool descriptions are the primary mechanism the model uses to understand how to call a tool. Adding format constraints and examples directly to the description gives the model the information it needs at decision time. Option A adds token overhead in the system prompt but is more fragile than a tool-specific description. Option C adds validation but does not prevent the model from sending malformed inputs in the first place, creating unnecessary error cycles. Option D addresses a different problem (disambiguation) rather than the format guidance issue.

---

**Q9.** You are deciding how to implement four behaviors for the support agent. Which one most clearly warrants a hook rather than prompt instructions?

A) Preferring to check the order status before asking the customer clarifying questions.
B) Never passing full payment card numbers to the external shipping-partner tool.
C) Responding to customers in a friendly and concise tone throughout the conversation.
D) Closing each conversation with a short summary of how the issue was resolved.

**Correct Answer: B**
*Task 1.5: Apply Agent SDK hooks for tool call interception and data normalization*

Hooks provide deterministic guarantees; prompt instructions provide probabilistic compliance. A compliance rule that must never be violated belongs in a hook that intercepts the outgoing tool call. Options A, C, and D are stylistic or preferential behaviors where occasional deviation is tolerable, which makes prompt guidance appropriate.

---

**Q10.** Each `lookup_order` call returns more than 40 fields (warehouse codes, internal audit data, carrier metadata), but the agent uses only five of them for return decisions. In long conversations with several lookups, the agent starts losing track of details from earlier in the conversation. What is the most effective fix?

A) Trim each tool result down to the return-relevant fields before it is added to the conversation context.
B) Limit the agent to two order lookups per conversation so that tool output cannot accumulate as quickly.
C) Summarize the earlier conversation turns more aggressively so the complete tool results continue to fit.
D) Instruct the agent in the system prompt to ignore any fields that are irrelevant to processing a return.

**Correct Answer: A**
*Task 5.1: Manage conversation context to preserve critical information across long interactions*

Tool results accumulate in context and consume tokens out of proportion to their relevance. Trimming verbose results to the relevant fields before they enter context removes the waste at the source. Option C sacrifices conversation detail, including precise customer-stated facts, to make room for noise. Option D does not help: ignored fields still occupy context. Option B limits capability rather than fixing context usage.

---

**Q11.** Your customer support system requires that every response from the `draft_response` agent includes a structured JSON summary before the agent returns its output. You want to guarantee the agent calls the `generate_summary` tool on every invocation, not optionally.

Which `tool_choice` configuration achieves this?

A) Remove all other tools from the agent's tool list so `generate_summary` is the only option available.
B) Set `tool_choice: {"type": "tool", "name": "generate_summary"}` to force the model to call `generate_summary` specifically.
C) Set `tool_choice: "any"` so the model must call at least one tool, though it may still choose a different tool instead.
D) Set `tool_choice: "auto"` so the model decides when the summary tool is needed.

**Correct Answer: B**
*Task 2.3: Distribute tools appropriately across agents and configure tool_choice*

Forced tool selection via `tool_choice: {"type": "tool", "name": "generate_summary"}` guarantees the model calls that specific tool on every invocation. Option D (`"auto"`) allows the model to return text without calling any tool. Option C (`"any"`) guarantees a tool call but does not guarantee which tool, so the model might choose a different one. Option A achieves the same result indirectly but removes legitimate tools the agent may need for its other tasks.

---

**Q12.** A customer writes, "This is Maria Garcia, I need to return my blender." The `get_customer` tool returns three accounts with that name. What should the agent do next?

A) Check each account's order history for a blender and proceed with whichever account turns out to contain one.
B) Select the account with the most recent order activity, since it is the most likely to belong to this customer.
C) Ask the customer for an additional identifier, such as an email address or order number, before proceeding.
D) Escalate to a human agent, because resolving identity ambiguity is outside what the agent should attempt.

**Correct Answer: C**
*Task 5.2: Design effective escalation and ambiguity resolution patterns*

When a lookup returns multiple matches, the agent should ask for additional identifiers rather than choose by heuristic. Options A and B are both heuristic selection and risk acting on, or exposing details of, the wrong person's account. Option D is unnecessary: this is a routine clarification the agent can resolve with one question.

---

**Q13.** Your customer support agent has three tools with overlapping names and descriptions: `get_account_info` ("Get information about the account"), `fetch_account_details` ("Fetch account details"), and `retrieve_customer_record` ("Retrieve customer information"). All three call different backend systems with different data. The agent frequently picks the wrong tool.

Which approach most effectively resolves the misrouting?

A) Rename the tools after their distinct data sources and rewrite each description to state what it returns and when to use it.
B) Add six to eight few-shot examples to the system prompt, each showing the correct tool being selected for a representative request.
C) Consolidate all three tools into one tool with a `source` parameter that specifies which backend to query.
D) Add a system prompt instruction listing all three tools and specifying exactly when each should be used based on the request type.

**Correct Answer: A**
*Task 2.1: Design effective tool interfaces with clear descriptions and boundaries*

Ambiguous or overlapping tool names and descriptions cause misrouting, because descriptions are the primary input the model uses to select tools. Renaming the tools and writing differentiated descriptions fixes the root cause. Option D may reduce misrouting but leaves the indistinguishable descriptions in place. Option C collapses three specialized tools into one generic tool, shifting the same routing decision into a parameter. Option B adds token overhead without fixing the descriptions themselves.

---

**Q14.** A customer writes: "This is the second time my discount wasn't applied. I'm really annoyed." The fix is a standard adjustment the agent is able to make, and the customer has not asked for a human. What is the best response?

A) Score the sentiment of each incoming message and escalate once it crosses a defined negative threshold.
B) Apply the adjustment without comment and close the conversation quickly in order to minimize further friction.
C) Escalate to a human agent immediately, because expressed frustration signals that the case is too sensitive to automate.
D) Acknowledge the frustration and offer to fix the problem now, escalating if the customer then asks for a human.

**Correct Answer: D**
*Task 5.2: Design effective escalation and ambiguity resolution patterns*

Sentiment is an unreliable proxy for case complexity. When the issue is within the agent's capability and the customer has not requested a human, the agent should acknowledge the frustration and offer resolution, escalating if the customer reiterates a preference for a human. Options A and C both escalate on sentiment rather than on real triggers (explicit request, policy gap, inability to progress). Option B ignores the customer's stated experience.

---

**Q15.** Your customer support agent has a policy: refunds above $500 require manager approval and must not be processed autonomously. Your system prompt states "Do not process refunds above $500 without manager approval." Production logs show this rule is violated in approximately 3% of cases.

What is the most effective way to guarantee compliance?

A) Add 10 few-shot examples in the system prompt, all demonstrating the agent requesting manager approval for high-value refunds.
B) Implement a validation step that runs after `process_refund` completes and reverses any refunds that exceeded the threshold.
C) Strengthen the system prompt language: "You are strictly forbidden from processing refunds above $500 without explicit manager approval under any circumstances."
D) Implement a hook that intercepts outgoing `process_refund` tool calls, checks the refund amount, and blocks execution or redirects to the manager approval workflow when the amount exceeds $500.

**Correct Answer: D**
*Task 1.5: Apply Agent SDK hooks for tool call interception and data normalization*

Business rules that require guaranteed compliance must be enforced programmatically, not through prompt instructions alone. A hook that intercepts `process_refund` calls before execution provides deterministic enforcement regardless of how the model interprets the system prompt. Options A and C both improve adherence probabilistically but cannot guarantee zero violations. Option B runs after the action has already been taken, which means the policy violation has already occurred.

---

**Q16.** Your agent achieves 55% first-contact resolution, well below the 80% target. Logs show it escalates straightforward cases while attempting to autonomously handle complex situations requiring policy exceptions. What's the most effective way to improve escalation calibration?

A) Add explicit escalation criteria to your system prompt with few-shot examples demonstrating when to escalate versus resolve autonomously.
B) Implement sentiment analysis to detect customer frustration levels and automatically escalate when negative sentiment exceeds a threshold.
C) Have the agent self-report a confidence score (1-10) before each response and automatically route requests to humans when confidence falls below a threshold.
D) Deploy a separate classifier model trained on historical tickets to predict which requests need escalation before the main agent begins processing.

**Correct Answer: A**
*Task 5.2: Design effective escalation and ambiguity resolution patterns*

Adding explicit escalation criteria with few-shot examples directly addresses the root cause: unclear decision boundaries. Option C fails because LLM self-reported confidence is poorly calibrated. Option D is over-engineered. Option B solves a different problem entirely.

---

**Q17.** A customer asks the agent to match a competitor's lower price. Your policy documents cover price adjustments only for price drops on your own site and say nothing about competitor prices. How should the agent handle the request?

A) Apply the own-site price adjustment policy, since the customer's situation is closely analogous to the cases that it covers.
B) Decline the request, since anything that the policy does not explicitly allow should be treated as prohibited.
C) Ask the customer for proof of the competitor's price, then issue the adjustment if the evidence checks out.
D) Escalate to a human agent, since the policy is silent on this situation and it calls for a judgment the agent cannot make.

**Correct Answer: D**
*Task 5.2: Design effective escalation and ambiguity resolution patterns*

Policy gaps and exceptions are a core escalation trigger: when policy is ambiguous or silent on the customer's specific request, the agent should escalate rather than improvise. Options A and C invent policy by extending a rule to a case it does not cover. Option B also invents policy, in the opposite direction, and may wrongly deny something the business would allow.

---

**Q18.** A customer opens a support chat saying "I'd like to speak to a human please. I've been dealing with this billing issue for three weeks and I'm frustrated." The agent has already identified this as a standard billing adjustment that it can resolve in 2 steps using its available tools. Your agent responds by saying "I can help with that right away, let me pull up your account." and proceeds to investigate. The customer repeats their request for a human. What is wrong with this behavior and what should be corrected?

A) The agent should honor an explicit customer request for a human agent immediately on first request, without attempting investigation first.
B) The agent should detect negative sentiment and escalate once the frustration score exceeds a defined threshold.
C) The agent should apologize for the wait, then proceed with automated resolution since the case is within its capability.
D) The agent should complete its investigation, present the proposed solution, and escalate only if the customer still insists on a human afterward.

**Correct Answer: A**
*Task 5.2: Design effective escalation and ambiguity resolution patterns*

When a customer explicitly requests a human agent, that request must be honored immediately regardless of whether the agent believes it can resolve the issue. Proceeding with investigation after a clear escalation request violates the design principle documented in Task 5.2. Option B introduces sentiment scoring as a proxy, but the customer has already expressed an explicit preference. Sentiment analysis is irrelevant here. Option D delays honoring the request while investigation proceeds, which further frustrates the customer. Option C is the agent's current incorrect behavior: capability is not the deciding factor when a customer has made an explicit request.

---

**Q19.** Your customer support agent integrates with three backend MCP tools: a legacy billing system returning Unix timestamps, an order management system returning ISO 8601 dates, and a subscription service returning numeric status codes (1=active, 2=paused, 3=cancelled). The agent frequently misinterprets these heterogeneous formats when reasoning about customer records.

What is the most appropriate architectural fix?

A) Add a post-processing step after the agent produces its final response to re-format any dates and status values that appear in the output.
B) Update each backend system to return a uniform date and status format before the agent calls them.
C) Add format conversion instructions to the system prompt explaining how to interpret each tool's output conventions.
D) Add `PostToolUse` hooks that normalize timestamps, dates, and status codes into one consistent format before the model sees each result.

**Correct Answer: D**
*Task 1.5: Apply Agent SDK hooks for tool call interception and data normalization*

`PostToolUse` hooks are the correct mechanism for intercepting and transforming tool results before the model processes them. This ensures the model always sees normalized data regardless of backend heterogeneity. Option B requires backend changes that may not be feasible and introduces coupling. Option C relies on probabilistic compliance and adds token overhead. Option A applies normalization after the model has already reasoned on inconsistent data, which cannot repair any incorrect conclusions already made.

---

**Q20.** Production data shows that in 12% of cases, your agent skips `get_customer` entirely and calls `lookup_order` using only the customer's stated name, occasionally leading to misidentified accounts and incorrect refunds. What change would most effectively address this reliability issue?

A) Implement a routing classifier that analyzes each request and enables only the subset of tools appropriate for that request type.
B) Enhance the system prompt to state that customer verification via `get_customer` is mandatory before any order operations.
C) Add a programmatic prerequisite that blocks `lookup_order` and `process_refund` calls until `get_customer` has returned a verified customer ID.
D) Add few-shot examples showing the agent always calling `get_customer` first, even when customers volunteer order details.

**Correct Answer: C**
*Task 1.4: Implement multi-step workflows with enforcement and handoff patterns*

When a specific tool sequence is required for critical business logic, programmatic enforcement provides deterministic guarantees that prompt-based approaches cannot. Options B and D rely on probabilistic LLM compliance. Option A addresses tool availability rather than tool ordering.

---

**Q21.** When your support agent escalates a billing dispute, the human agent receives a ticket reading only "Customer needs help with a refund." Human agents work in a separate ticketing system with no access to the conversation transcript, and they spend several minutes re-asking questions the customer has already answered. What should the agent do when it escalates?

A) Paste the complete conversation transcript into the ticket so the human agent can read everything that was discussed.
B) Raise the escalation threshold so that fewer cases reach human agents and handoff quality matters less often.
C) Stay in the conversation after escalating so that it can answer the human agent's questions about the case as they come up.
D) Compile a structured handoff summary containing the customer ID, root cause analysis, refund amount, and recommended action.

**Correct Answer: D**
*Task 1.4: Implement multi-step workflows with enforcement and handoff patterns*

Human agents who lack transcript access need a structured handoff summary with the facts required to act: customer ID, root cause, amounts, and the recommended action. Option A forces the human to reconstruct the case from raw dialogue, which is slow and error-prone. Option C keeps the human dependent on the agent rather than giving them a self-contained case. Option B avoids the problem instead of fixing the handoff.

---

## Scenario 2: Code Generation with Claude Code

You are using Claude Code to accelerate software development for code generation, refactoring, debugging, and documentation. You need to integrate it with custom slash commands, CLAUDE.md configurations, and understand when to use plan mode vs direct execution.

**Primary domains:** Domain 3, Domain 5

---

**Q22.** A development team is using Claude Code to implement a new authentication module. Before any implementation begins, the team lead wants to ensure Claude surfaces potential security considerations, edge cases, and design tradeoffs that the team may not have anticipated. Which iterative refinement technique is most appropriate here?

A) Start with a minimal implementation, then iterate by describing the issues found during the team's code review.
B) Write a detailed specification covering the known requirements and pass it to Claude for direct implementation.
C) Use the interview pattern: have Claude ask the team about requirements, constraints, and assumptions before proposing a design.
D) Provide a complete test suite first and have Claude iterate on the code until every one of the tests passes.

**Correct Answer: C**
*Task 3.5: Apply iterative refinement techniques for progressive improvement*

The interview pattern is designed to surface design considerations and uncover assumptions the developer may not have anticipated before any implementation begins. It is particularly valuable in domains like security where overlooked edge cases carry high risk. Option B bypasses the opportunity to surface gaps before implementation is locked in. Option A defers the discovery of design issues until after implementation, when the cost of changes is higher. Option D (test-driven iteration) is effective for well-defined behavior but cannot surface considerations the team has not yet thought of.

---

**Q23.** A developer is using plan mode to explore a large codebase before deciding how to approach a library migration. During exploration, Claude generates dozens of tool results including full file reads, search outputs, and dependency traces. The developer notices the main conversation context is filling up rapidly and fears context exhaustion before the plan is complete. What is the most appropriate technique to preserve main session context during verbose exploration?

A) Switch to direct execution partway through so Claude spends fewer tool calls on exploration before it starts editing files.
B) Limit Claude to reading entry point files during plan mode so exploration generates far fewer tool results overall.
C) Run `/compact` after every few tool calls so earlier results are continuously summarized as the context window grows.
D) Delegate the verbose discovery to the Explore subagent, which returns a summary instead of raw results to the main session.

**Correct Answer: D**
*Task 3.4: Determine when to use plan mode vs direct execution*

The Explore subagent isolates verbose discovery work from the main conversation context: it explores and returns a summary, so raw tool results never consume the main session's budget. Option A abandons the exploration the migration needs. Option C is cumbersome and repeatedly discards detail that may still be needed. Option B artificially limits exploration and would produce an incomplete analysis.

---

**Q24.** A developer says Claude Code follows the team's conventions in some sessions but not in others, and suspects that some instruction files are not being loaded. What is the most direct way to diagnose this?

A) Ask Claude to list the conventions it is following and compare its answer against the files.
B) Move every instruction file into `~/.claude/CLAUDE.md` so that it is loaded in every session.
C) Run the `/memory` command to check which memory files are actually loaded in the current session.
D) Run the `/compact` command to make Claude reload all of its instruction files from disk in the current session.

**Correct Answer: C**
*Task 3.1: Configure CLAUDE.md files with appropriate hierarchy, scoping, and modular organization*

The `/memory` command shows which memory files are loaded, which makes it the direct tool for diagnosing inconsistent behavior across sessions. Option D summarizes conversation history; it is not a diagnostic. Option A yields the model's impression rather than ground truth about what was loaded. Option B makes team conventions personal and unshared, creating a different problem.

---

**Q25.** You've been assigned to restructure a monolithic application into microservices. This will involve changes across dozens of files and requires decisions about service boundaries and module dependencies. Which approach should you take?

A) Enter plan mode to explore the codebase, understand dependencies, and design an implementation approach before making changes.
B) Begin in direct execution mode and only switch to plan mode if you encounter unexpected complexity during implementation.
C) Start with direct execution and make changes incrementally, letting the implementation reveal the natural service boundaries.
D) Use direct execution with comprehensive upfront instructions detailing exactly how each service should be structured.

**Correct Answer: A**
*Task 3.4: Determine when to use plan mode vs direct execution*

Plan mode is designed for complex tasks involving large-scale changes, multiple valid approaches, and architectural decisions. Option C risks costly rework when dependencies are discovered late. Option D assumes you already know the right structure without exploring the code. Option B ignores that the complexity is already stated.

---

**Q26.** A senior engineer adds detailed coding standards and security guidelines to their `~/.claude/CLAUDE.md` file. When a new team member joins and clones the repository, they report that Claude Code behaves differently and does not appear to follow the team's documented standards. What is the most likely cause?

A) The `~/.claude/CLAUDE.md` file is user-scoped and not version-controlled, so teammates do not receive it when they clone the repository.
B) The configuration hierarchy requires the project-level file to explicitly import from user-level files using `@import`.
C) CLAUDE.md files must be placed in the `.claude/` subdirectory to be recognized; a root-level `CLAUDE.md` is ignored.
D) The new team member's Claude Code version is outdated and does not support shared configuration files.

**Correct Answer: A**
*Task 3.1: Configure CLAUDE.md files with appropriate hierarchy, scoping, and modular organization*

User-level configuration in `~/.claude/CLAUDE.md` applies only to the individual developer and is never shared through version control. To share standards across the team, the instructions must live in the project-level `CLAUDE.md` or `.claude/CLAUDE.md`, which are committed to the repository. Option D is not a real limitation. Option C is incorrect because a root-level `CLAUDE.md` is a valid project-level location. Option B misstates how imports work: they are optional, and they cannot pull in a file that exists only on another developer's machine.

---

**Q27.** You are leading a research investigation using Claude Code. You have completed an initial analysis of a competitor's public API documentation and want to explore two divergent architectural approaches for your response strategy: one focused on feature parity, one focused on differentiation. You want both explorations to start from the same analysis baseline.

Which session management approach best fits this scenario?

A) Use `--resume` to resume the current session twice in parallel, once for each exploration direction.
B) Use `fork_session` to create two independent branches from the current session, then explore each approach in its respective branch.
C) Run two separate new sessions, each with a copy of the analysis findings injected as context in the initial prompt.
D) Continue in the same session, exploring one approach first, then using `/compact` to clear context before exploring the second approach.

**Correct Answer: B**
*Task 1.7: Manage session state, resumption, and forking*

`fork_session` is designed precisely for this scenario: creating independent branches from a shared analysis baseline to explore divergent approaches. Each branch inherits the common findings and can be explored independently without contaminating the other. Option C requires duplicating context and does not preserve the live session state. Option A describes a mechanism that does not work this way: `--resume` continues a single session sequentially, not in parallel branches. Option D uses `/compact` destructively, losing the baseline context needed for the second exploration.

---

**Q28.** Your monorepo has a root `CLAUDE.md` that has grown to over 400 lines, covering Python conventions, TypeScript conventions, infrastructure rules, and testing standards. Developers report that Claude sometimes applies the wrong conventions to the wrong files, and the file is difficult to maintain. What is the best approach to reorganize this configuration?

A) Create a separate `CLAUDE.md` in each top-level package directory and delete the root file entirely.
B) Break the root `CLAUDE.md` into topic files and use `@import` directives in the root file to pull them all in unconditionally.
C) Add inline section headers to the monolithic file and use the `/memory` command to tell Claude which section to prioritize for each task.
D) Split it into focused files under `.claude/rules/`, each with `paths` frontmatter so its rules load only for matching files.

**Correct Answer: D**
*Task 3.1: Configure CLAUDE.md files with appropriate hierarchy, scoping, and modular organization*

The `.claude/rules/` directory is designed for exactly this scenario: topic-specific rule files with YAML frontmatter path scoping, so each rule set activates only when editing matching files. This reduces irrelevant context and token usage. Option A would require duplicating shared rules across package directories. Option C relies on manual intervention each session; `/memory` shows which memory files are loaded, it does not prioritize sections. Option B addresses the maintenance concern but not the wrong-conventions problem, since unconditional imports still load every rule.

---

**Q29.** A developer has been using Claude Code to investigate a legacy authentication service. After several hours, they have built up a detailed session with findings about the service's token validation logic. They need to step away and return tomorrow. Three core files in the authentication module will be modified overnight by another team.

What is the most reliable approach for resuming the investigation productively the next day?

A) Resume the named session without any notification about file changes; the agent will detect modifications automatically when it next reads those files.
B) Resume with `--resume <session-name>` and tell the agent which files changed so it can re-analyze them against its prior findings.
C) Start a completely new session each time, since stale tool results from the previous session make resumption unreliable for any scenario.
D) Use `fork_session` to create a branch of the current session before stepping away, then resume from the fork the next day.

**Correct Answer: B**
*Task 1.7: Manage session state, resumption, and forking*

When resuming a session after code modifications, the correct approach is to use `--resume <session-name>` to continue the named session and explicitly inform the agent about which files changed so it can target re-analysis appropriately. Option C is overly conservative: starting fresh is appropriate when prior tool results are broadly stale, but when only a few known files changed, resumption with targeted context about those changes is more efficient. Option A is incorrect because the agent does not automatically detect file changes on resume. Option D misuses `fork_session`, which is designed for exploring divergent approaches from a shared baseline, not for session continuity across time gaps.

---

**Q30.** Your team shares a `/review` skill in the project's `.claude/skills/` directory. One developer wants a stricter variant for personal use without changing behavior for teammates. What should they do?

A) Create the variant inside the project's `.claude/skills/` directory and add its path to `.gitignore`.
B) Edit the shared skill and add an argument that switches on the stricter behavior only when they pass it.
C) Add their stricter review rules to the project `CLAUDE.md` under a section that is labeled with their name.
D) Create a differently named variant in `~/.claude/skills/`, which is personal and is not shared through the repository.

**Correct Answer: D**
*Task 3.2: Create and configure custom slash commands and skills*

Personal customizations belong in user scope: a variant in `~/.claude/skills/` with a different name is available to that developer and leaves teammates unaffected. Option B modifies the shared skill for everyone. Option C loads one person's preferences into every teammate's sessions. Option A can work locally but puts personal configuration in the project directory and changes a shared file to hide it.

---

**Q31.** A developer generates a 300-line module using Claude Code in one session, then asks the same session to review the code for bugs. The review returns "looks good" with minor style suggestions but misses two logic errors that a colleague catches in manual review. What is the most likely cause, and what architectural change addresses it?

A) The session retains its generation reasoning and rarely questions its own decisions; review with an independent instance instead.
B) The review prompt was too vague; adding more explicit review criteria to the same session would catch the missed errors.
C) The model tier used for generation is more capable than the one used for review; switching both to the same tier resolves the quality gap.
D) The context window was too large; the fix is to limit code generation to smaller chunks so the review has less to process.

**Correct Answer: A**
*Task 4.6: Design multi-instance and multi-pass review architectures*

Self-review limitation is a known pattern: when a model retains the reasoning context from code generation, it is less likely to identify errors in its own output. An independent review instance without the generator's context approaches the code without prior assumptions and catches issues the generating instance would overlook. Option D addresses context length, not reasoning context bias. Option B might improve detection of certain categories of issues but does not address the fundamental self-review limitation. Option C addresses model selection, not the structural problem of reviewing one's own output.

---

**Q32.** A developer asks Claude Code to reformat date strings in a data pipeline. After the first attempt, the output format is partially correct but inconsistent: some dates are formatted as `YYYY-MM-DD`, others as `MM/DD/YYYY`. Prose instructions like "always use ISO 8601" have been tried twice without improvement. What technique is most likely to resolve the inconsistency?

A) Ask Claude to generate a formatting function first, then apply it in a second pass.
B) Provide 2-3 concrete input/output examples of the expected transformation, including ambiguous formats.
C) Switch to plan mode so Claude can explore the codebase before formatting dates.
D) Rewrite the instruction to be more emphatic, using capitalization and repetition to signal how important it is.

**Correct Answer: B**
*Task 3.5: Apply iterative refinement techniques for progressive improvement*

Concrete input/output examples are the most effective way to communicate expected transformations when prose instructions are interpreted inconsistently. Showing `"3/15/2024" -> "2024-03-15"` is unambiguous in a way that "use ISO 8601" is not. Option D is unlikely to improve results; emphasis does not resolve ambiguity. Option C is for architectural decisions, not formatting refinement. Option A adds complexity and still does not clarify what the correct transformation looks like.

---

**Q33.** Your codebase has distinct areas with different conventions. Test files are spread throughout the codebase alongside the code they test. You want all tests to follow the same conventions regardless of location. What's the most maintainable way to ensure Claude automatically applies the correct conventions when generating code?

A) Consolidate all conventions in the root `CLAUDE.md` file under headers for each area, relying on Claude to infer which section applies.
B) Create skills in `.claude/skills/` for each code type that include the relevant conventions in their `SKILL.md` files.
C) Create rule files in `.claude/rules/` with YAML frontmatter specifying glob patterns to conditionally apply conventions based on file paths.
D) Place a separate `CLAUDE.md` file in each subdirectory containing that area's specific conventions.

**Correct Answer: C**
*Task 3.3: Apply path-specific rules for conditional convention loading*

`.claude/rules/` with glob patterns (e.g., `**/*.test.tsx`) allows conventions to be automatically applied based on file paths regardless of directory location. Option A relies on inference rather than explicit matching. Option B requires manual invocation. Option D can't easily handle files spread across many directories.

---

**Q34.** You want to create a custom `/review` slash command that runs your team's standard code review checklist and should be available to every developer when they clone or pull the repository. Where should you create this command file?

A) In the `.claude/commands/` directory in the project repository
B) In the `CLAUDE.md` file at the project root
C) In a `.claude/config.json` file with a `commands` array
D) In `~/.claude/commands/` in each developer's home directory

**Correct Answer: A**
*Task 3.2: Create and configure custom slash commands and skills*

Project-scoped custom slash commands are stored in `.claude/commands/` within the repository, version-controlled and automatically available to all developers. Option D is for personal, non-shared commands. Option B is for project instructions, not command definitions. Option C describes a mechanism that doesn't exist.

---

**Q35.** A developer wants a `/scaffold` skill that generates boilerplate for a new microservice. The skill runs many exploratory file reads and Bash commands to understand existing patterns before generating output, producing hundreds of lines of intermediate output. Teammates complain this pollutes their main conversation context. Which frontmatter setting resolves this?

A) Set `allowed-tools: []` in the skill's frontmatter to prevent tool use during execution.
B) Set `context: fork` in the skill's frontmatter to run the skill in an isolated sub-agent context that does not affect the main session.
C) Move the skill file from `.claude/skills/` to `.claude/commands/` so it runs as a command rather than a skill.
D) Add `argument-hint: "service-name"` to the frontmatter so the skill receives a clean input without inheriting any of the session context.

**Correct Answer: B**
*Task 3.2: Create and configure custom slash commands and skills*

The `context: fork` frontmatter option runs the skill in an isolated sub-agent context. All exploratory output, intermediate tool calls, and reasoning happen in the fork and do not accumulate in the main conversation context. Only the final output is returned to the parent session. Option A would disable the tool use the skill depends on. Option C does not change execution isolation behavior. Option D is for prompting the user for input parameters, unrelated to output isolation.

---

**Q36.** Claude Code generated a data transformation function that has three separate issues: an off-by-one error in a loop, a missing null check for an optional field, and an incorrect sort order. Each issue is in a completely different part of the function and none of them interact. What is the recommended approach for addressing these issues?

A) Ask Claude to regenerate the entire function from scratch rather than patching the existing code.
B) Report all three issues in a single detailed message so Claude has full context for all fixes at once.
C) Fix them sequentially: address each issue in a separate message and verify the fix before moving to the next.
D) Address the off-by-one error and null check together since they are in loops, then fix the sort order separately.

**Correct Answer: C**
*Task 3.5: Apply iterative refinement techniques for progressive improvement*

When issues are independent, sequential iteration is appropriate: fixing each one separately and verifying the fix before moving on reduces the chance of fixes interfering with each other and makes each change easier to review. The guidance for sending all issues in a single message applies when the issues interact and Claude needs full context to resolve them together. Option B is suited to interacting problems, not independent ones. Option A discards working code unnecessarily. Option D creates an arbitrary grouping not based on actual interaction.

---

**Q37.** Your team uses Terraform for infrastructure but only in the `infra/` directory. You want Claude to automatically apply Terraform naming conventions and module structure rules only when editing `.tf` files, without those rules appearing in unrelated Python or TypeScript sessions. What is the correct approach?

A) Create a `CLAUDE.md` file inside `infra/` that contains the Terraform rules so they apply only within that subdirectory.
B) Add the Terraform rules to the root `CLAUDE.md` under a clearly marked section, and instruct Claude in the system prompt to apply them only to `.tf` files.
C) Create a skill at `.claude/skills/terraform/SKILL.md` with `allowed-tools` restricted to file operations on the `infra/` directory.
D) Create `.claude/rules/terraform.md` with YAML frontmatter `paths: ["infra/**/*.tf"]` followed by the Terraform conventions.

**Correct Answer: D**
*Task 3.3: Apply path-specific rules for conditional convention loading*

The `.claude/rules/` directory with YAML frontmatter path scoping is the mechanism for conditionally loading conventions. A glob such as `infra/**/*.tf` loads the Terraform rules only when Claude works on matching files. Option A scopes by directory but cannot filter by file type. Option B relies on Claude's inference rather than explicit path matching, and the rules would still load in every session. Option C requires the skill to be invoked and does not load automatically by file path.

---

**Q38.** You maintain a monorepo with five packages: a Python backend, a TypeScript frontend, a Go service, shared infrastructure Terraform, and a documentation site. Each package has different linting standards, testing conventions, and framework-specific rules. The root `CLAUDE.md` has grown to 600 lines and developers report that rules intended for one package often bleed into sessions working on another. What is the most modular and maintainable solution using CLAUDE.md configuration?

A) Keep the 600-line root file but add explicit section headers and instruct developers to tell Claude which section applies at the start of each session.
B) Move all rules into `.claude/rules/` files and tag each with a `projects:` key in their frontmatter specifying which subdirectory the rule applies to.
C) Create a `CLAUDE.md` in each package directory with that package's rules, and use `@import` in the root `CLAUDE.md` to include shared conventions that apply to all packages.
D) Delete the root `CLAUDE.md` and rely entirely on package-level files, accepting that shared conventions must be duplicated across packages.

**Correct Answer: C**
*Task 3.1: Configure CLAUDE.md files with appropriate hierarchy, scoping, and modular organization*

The `@import` syntax in CLAUDE.md is designed for exactly this modular pattern: shared conventions in the root file, package-specific rules in each package's own `CLAUDE.md`, with the root file importing common standards that apply globally. This keeps each file focused and maintainable while eliminating rule bleed between packages. Option A relies on developer discipline to manually scope rules each session, which is error-prone and does not scale. Option D eliminates the shared baseline and requires duplicating common conventions across five files, creating maintenance drift. Option B is a valid approach for path-scoped rules within a single project but does not address the need for package-level CLAUDE.md isolation.

---

**Q39.** A developer has identified three issues in a data processing module: two logic bugs that interact because they both affect the same intermediate result, and a set of five inconsistent variable names scattered across multiple files. The logic bugs produce incorrect output only when both are present; the naming violations are independent style issues. How should these issues be addressed using iterative refinement?

A) Fix all naming violations first since they are simpler, then tackle the two logic bugs in a single message.
B) Report all eight issues in a single message so Claude can resolve them together with full context.
C) Fix each of the eight issues in eight separate sequential messages, verifying each before proceeding.
D) Report the two interacting bugs together in one message, then fix the naming issues sequentially afterward.

**Correct Answer: D**
*Task 3.5: Apply iterative refinement techniques for progressive improvement*

The guidance for batching issues is based on whether they interact. The two logic bugs interact and Claude needs full context on both to resolve them correctly, so they should be reported together. The naming violations are independent and do not affect correctness, so sequential iteration is appropriate: fix each one and verify before moving to the next. Option B lumps all issues together, which adds noise when Claude is resolving the interacting bugs. Option A addresses ordering by complexity rather than by interaction. Option C applies sequential iteration to interacting bugs, which risks an incomplete fix.

---

**Q40.** A developer asks Claude Code to implement a currency-rounding utility. The expected results are fully specified in a requirements table, yet three rounds of prose feedback ("it still mishandles some edge cases") have each fixed one case and broken another. Which technique is most likely to make the iteration converge?

A) Describe every remaining edge case together in a single longer and more detailed prose message.
B) Switch to plan mode so that Claude can redesign the rounding approach before it attempts another implementation.
C) Write tests covering the expected behavior and edge cases first, then iterate by sharing the failing test output with Claude.
D) Have Claude interview the developer about the rounding requirements before writing a fresh implementation.

**Correct Answer: C**
*Task 3.5: Apply iterative refinement techniques for progressive improvement*

Test-driven iteration gives Claude an objective, repeatable signal: write the test suite first, then share concrete failures to guide each improvement, so a fix cannot silently break an earlier case. Option B is for architectural uncertainty, which is not the problem here. Option D suits situations where requirements are unknown; here they are already fully specified. Option A is still prose feedback, which has already proven too ambiguous.

---

**Q41.** A developer asks Claude Code to add a single null-check to one function in a utility module. The function signature, expected behavior, and fix are all clear. Should they use plan mode or direct execution?

A) Use direct execution first, but run a quick plan mode scan afterward to catch any side effects before committing.
B) Plan mode, because any code change could have unexpected side effects that need exploration before committing.
C) Direct execution, because the task is well-scoped with a clear fix that does not require architectural decisions or multi-file analysis.
D) Plan mode, because exploring the codebase first prevents Claude from making assumptions about dependencies.

**Correct Answer: C**
*Task 3.4: Determine when to use plan mode vs direct execution*

Direct execution is appropriate for simple, well-understood, single-location changes with clear scope. Plan mode is designed for tasks involving large-scale changes, multiple valid approaches, architectural decisions, or multi-file modifications. A null-check to one function meets none of the criteria for plan mode. Options B and D describe an over-cautious heuristic that does not reflect the intended use of plan mode. Option A inverts the correct workflow: plan mode is used before execution to explore and decide, not after as a post-execution check.

---

## Scenario 3: Multi-Agent Research System

You are building a multi-agent research system using the Claude Agent SDK. A coordinator agent delegates to specialized subagents: web search, document analysis, synthesis, and report generation. The system produces comprehensive cited reports.

**Primary domains:** Domain 1, Domain 2, Domain 5

---

**Q42.** You are building a multi-agent research system with a synthesis agent whose sole job is combining findings from subagents and producing a structured report. You have given the synthesis agent access to all 18 tools in your system: web search, file reading, database queries, email sending, calendar access, and more, reasoning that more tools provide more flexibility.

What problem does this configuration most likely introduce?

A) The model will stop calling tools altogether, because selection reliability collapses once more than a dozen tools are defined.
B) Prompt caching is disabled when more than 16 tools are defined, so every synthesis request is billed at the full input rate.
C) The additional tools will slow down the synthesis agent, because the model must read all of the tool descriptions before producing output.
D) The agent becomes more likely to misuse out-of-role tools, such as running new web searches instead of synthesizing provided findings.

**Correct Answer: D**
*Task 2.3: Distribute tools appropriately across agents and configure tool_choice*

Giving an agent tools outside its specialization degrades tool selection reliability. A synthesis agent with web search tools will sometimes initiate new searches rather than working with the findings already provided. Scoped access (roughly 4-5 role-relevant tools) is the fix. Option A overstates the effect: the agent still calls tools, but may call the wrong ones. Option B invents a limit that does not exist. Option C mischaracterizes how tool descriptions affect latency.

---

**Q43.** A report states that two sources "contradict each other" on electric vehicle adoption (12% versus 18%). A reviewer discovers that one source reports 2021 data and the other 2023 data. What change prevents this misinterpretation?

A) Add a verification subagent that re-searches every statistic that appears in a report.
B) Restrict the web search subagent to sources published within the last twelve months.
C) Require subagents to include publication or data-collection dates in their structured outputs.
D) Instruct the synthesis agent to prefer the higher of the two figures whenever two sources disagree.

**Correct Answer: C**
*Task 5.6: Preserve information provenance and handle uncertainty in multi-source synthesis*

Temporal metadata lets the synthesis agent interpret differing figures correctly, as change over time rather than contradiction. Option D is an arbitrary rule that would still misrepresent the data. Option A adds cost without supplying the missing dates. Option B discards valid historical context and does not help when recent sources cover different periods.

---

**Q44.** You are building a coordinator that delegates research tasks to subagents using the `Task` tool. When you test the system, the coordinator cannot invoke any subagents. Reviewing the coordinator's `AgentDefinition`, you notice the `allowedTools` field is set to `["web_search", "read_document"]`.

What is the most likely cause of the failure?

A) The coordinator's system prompt does not include instructions to use the `Task` tool, so the model never attempts to call it.
B) The `Task` tool requires an explicit `subagent_endpoint` configuration before it can be invoked.
C) Subagent invocation requires the coordinator to be running in plan mode rather than direct execution mode.
D) `"Task"` is not included in the coordinator's `allowedTools`, so it cannot spawn subagents.

**Correct Answer: D**
*Task 1.3: Configure subagent invocation, context passing, and spawning*

The `Task` tool is the mechanism for spawning subagents in the Claude Agent SDK. For a coordinator to invoke subagents, `"Task"` must be explicitly included in its `allowedTools`. Simply having other tools available does not grant subagent spawning capability. Option B describes a configuration parameter that does not exist. Option A conflates prompt instructions with capability gating: even a well-prompted coordinator cannot call a tool that is not in its allowed set. Option C conflates plan mode with subagent spawning.

---

**Q45.** The synthesis agent frequently needs to verify specific claims while combining findings. Currently, this creates 2-3 round trips per task, increasing latency by 40%. 85% of verifications are simple fact-checks; 15% require deeper investigation. What's the most effective approach to reduce overhead while maintaining reliability?

A) Have the web search agent proactively cache extra context around each source during initial research, anticipating what the synthesis agent might need to verify.
B) Give the synthesis agent a scoped `verify_fact` tool for simple lookups, while complex verifications continue delegating to the web search agent through the coordinator.
C) Give the synthesis agent access to all web search tools so it can handle any verification need directly without round-trips.
D) Have the synthesis agent accumulate all verification needs and return them as a batch to the coordinator at the end of its pass.

**Correct Answer: B**
*Task 2.3: Distribute tools appropriately across agents and configure tool_choice*

Option B applies the principle of least privilege by giving the synthesis agent only what it needs for the 85% common case while preserving the existing coordination pattern for complex cases. Option D creates blocking dependencies. Option C over-provisions the synthesis agent. Option A relies on speculative caching.

---

**Q46.** The coordinator's prompt gives the web search subagent rigid procedural instructions: "Run exactly three searches using these keywords and open the top two results of each." Results are shallow whenever a topic does not fit the template. How should the delegation be redesigned?

A) Increase the required counts to six searches and five opened results each to deepen the coverage.
B) Add further procedural branches to the instructions so that they cover each additional type of topic that comes up.
C) Give the subagent access to the coordinator's conversation history so it can infer what is needed.
D) Specify the research goal and the quality criteria for results, and let the subagent decide how to search.

**Correct Answer: D**
*Task 1.3: Configure subagent invocation, context passing, and spawning*

Coordinator prompts should specify research goals and quality criteria rather than step-by-step procedures, which preserves the subagent's ability to adapt its approach to the topic. Options A and B keep the rigid template and merely make it bigger. Option C is not how subagent context works, and it would not supply clear goals even if it were.

---

**Q47.** A coordinator agent in your research system has delegated document analysis to a subagent. After the subagent finishes, the coordinator notices the findings are incomplete: the subagent covered only three of the five specified sources. The coordinator needs to get the remaining two sources analyzed.

What is the correct approach for re-delegating this work?

A) Invoke the synthesis agent with the partial findings and instruct it to infer what the missing sources likely contain based on patterns from the three completed analyses.
B) Send all five sources again to a new document analysis subagent instance, which will re-analyze the three already-completed sources along with the two missing ones.
C) The coordinator should re-invoke the document analysis subagent with an explicit prompt specifying only the two missing sources, including the previously completed findings as context.
D) Let the coordinator generate its own analysis of the remaining two sources directly, rather than spawning another subagent delegation.

**Correct Answer: C**
*Task 1.2: Orchestrate multi-agent systems with coordinator-subagent patterns*

The coordinator's role includes evaluating output for gaps and re-delegating targeted work to close those gaps. Re-invoking the subagent with only the unfinished sources and providing the completed findings as context is efficient and correct. Option A asks synthesis to fabricate content, which undermines report accuracy. Option B wastes resources by re-processing already-completed sources. Option D bypasses the coordinator-subagent architecture and ignores the subagent's specialization.

---

**Q48.** A coordinator needs to research three independent subtopics in parallel: market trends, competitor analysis, and regulatory environment. Each requires a separate web search subagent. How should the coordinator spawn these subagents to maximize throughput?

A) Emit all three `Task` tool calls in a single coordinator response, which allows the subagents to run in parallel.
B) Spawn the subtopics sequentially: start the first subagent, wait for its result, then start the second, and so on, to avoid context conflicts.
C) Use a single subagent with three separate prompts in sequence, passing prior results as context for each subsequent prompt.
D) Route all three subtopics through a single subagent sequentially, sharing context between them to reduce total memory usage.

**Correct Answer: A**
*Task 1.3: Configure subagent invocation, context passing, and spawning*

The Claude Agent SDK supports parallel subagent execution by emitting multiple `Task` tool calls in a single coordinator response. This maximizes throughput for independent subtopics that do not depend on each other's results. Option B introduces unnecessary serial latency. Option D assumes a dependency that the question does not establish. Option C collapses three specialists into one sequential process, eliminating parallelism.

---

**Q49.** The document analysis subagent fails on two of eight sources (corrupted PDFs) even after its own retries. The other six were analyzed successfully. What should happen next?

A) The subagent returns the six results without comment so the report is not held up by unreadable sources.
B) The subagent returns an error and the coordinator aborts the report, since partial coverage would mislead readers.
C) The subagent returns partial results plus what failed and what it tried, and the report notes the coverage gap.
D) The coordinator keeps re-invoking the subagent on the two failed sources until both of them succeed.

**Correct Answer: C**
*Task 5.3: Implement error propagation strategies across multi-agent systems*

Subagents should handle transient failures locally and propagate only what they cannot resolve, together with partial results and what was attempted. The coordinator can then decide how to proceed, and the final output should annotate the coverage gap. Option B terminates the whole workflow over a partial failure. Option A silently suppresses the failure. Option D retries a non-transient failure indefinitely.

---

**Q50.** Your multi-agent research system uses a coordinator that always routes every query through all four subagents (web search, document analysis, synthesis, and report generation) regardless of query complexity. For a simple factual question like "What year was the Anthropic API released?", the system takes 45 seconds and incurs unnecessary cost.

What design change most directly addresses this?

A) Replace the coordinator with a static routing table that maps query keywords to specific subagent pipelines.
B) Have the coordinator analyze each query and invoke only the subagents it needs, rather than always running the full pipeline.
C) Reduce the number of subagents from four to two by merging web search and document analysis into one general-purpose "retrieval" agent.
D) Have each subagent evaluate its own relevance to the current query and self-select into or out of the pipeline.

**Correct Answer: B**
*Task 1.2: Orchestrate multi-agent systems with coordinator-subagent patterns*

A coordinator that always runs the full pipeline regardless of query complexity wastes resources and adds latency for simple requests. The correct design is a coordinator that evaluates the query and selects only the subagents needed for that specific task. Option A replaces adaptive intelligence with a brittle keyword table. Option D distributes coordination logic across subagents, breaking the hub-and-spoke pattern and reducing observability. Option C reduces capability unnecessarily instead of improving routing logic.

---

**Q51.** The coordinator gathers findings from the web search and document analysis subagents, then invokes the synthesis subagent with the prompt "Synthesize the research findings into a report." The synthesis subagent returns a generic overview containing none of the gathered findings. What is the cause?

A) Subagents do not inherit the coordinator's context, so the findings have to be included in the subagent's prompt.
B) The synthesis subagent's system prompt is too generic and needs stronger instructions to rely on the findings.
C) The synthesis subagent lacks a tool for reading the shared memory store where subagent findings are kept.
D) The synthesis subagent's context window overflowed, so the earlier findings were truncated before it could use them.

**Correct Answer: A**
*Task 1.2: Orchestrate multi-agent systems with coordinator-subagent patterns*

Subagents operate with isolated context: they do not automatically inherit the coordinator's conversation history or share memory between invocations. Everything a subagent needs must be passed explicitly in its prompt. Option D assumes the findings were delivered, which they were not. Option C describes a shared memory mechanism that does not exist by default. Option B cannot help when the findings are simply absent from the subagent's context.

---

**Q52.** Your web search subagent encounters a timeout while fetching results for a competitor analysis. The engineering team implements a change so the subagent catches the timeout internally and returns an empty result set with `status: "success"` and `results: []`. The coordinator receives this and the synthesis agent produces a report that is missing the competitive section entirely, with no indication anything went wrong. What is the problem with this approach?

A) The timeout threshold should be increased so that the subagent does not time out before returning real results.
B) The coordinator should always validate that each subagent returned non-empty results before proceeding to synthesis.
C) The synthesis agent should be responsible for detecting empty sections and re-triggering the web search subagent directly.
D) Reporting failure as an empty success denies the coordinator any chance to recover and lets incomplete work pass as complete.

**Correct Answer: D**
*Task 5.3: Implement error propagation strategies across multi-agent systems*

Silently suppressing errors by returning empty results as success is an explicitly documented anti-pattern. It removes the coordinator's ability to recover, retry, or annotate output with coverage gaps. Option C incorrectly shifts the recovery responsibility to the synthesis agent, which lacks the tools and context to re-run searches. Option B adds coordinator-level validation as a safeguard, but it does not address the root cause: the subagent is misrepresenting failure as success. Option A addresses the symptom (timeout threshold) rather than the error propagation design flaw.

---

**Q53.** Your multi-agent research system's agentic loop appends each tool result to the conversation history before sending the next request. A teammate suggests instead storing all tool results in a separate database and providing only a summary to the model at each iteration, rather than the full result.

Under what condition would this change most likely degrade agent performance?

A) When tools return small results, because the summarization overhead then exceeds the tokens that it saves.
B) When the model must reason across details from several tool results at once to choose its next action.
C) When the tool results contain binary data such as images or file attachments.
D) When sessions involve many tool calls, since generating each summary adds latency that compounds across iterations.

**Correct Answer: B**
*Task 1.1: Design and implement agentic loops for autonomous task execution*

The agentic loop depends on tool results being present in conversation history so the model can reason about what it has already discovered before deciding its next action. Summaries may omit field values, error codes, or conditional data the model needs. Option C is a valid concern but not the primary risk for text-based research tasks. Options A and D describe cost and latency overheads, not degraded reasoning quality.

---

**Q54.** The web search subagent times out while researching a complex topic. You need to design how this failure information flows back to the coordinator agent. Which error propagation approach best enables intelligent recovery?

A) Return structured error context to the coordinator including the failure type, the attempted query, any partial results, and potential alternative approaches.
B) Implement automatic retry logic with exponential backoff within the subagent, returning a generic "search unavailable" status only after all retries are exhausted.
C) Catch the timeout within the subagent and return an empty result set marked as successful.
D) Propagate the timeout exception directly to a top-level handler that terminates the entire research workflow.

**Correct Answer: A**
*Task 2.2: Implement structured error responses for MCP tools*

Structured error context gives the coordinator the information it needs to make intelligent recovery decisions. Option B's generic status hides valuable context. Option C suppresses the error, preventing any recovery. Option D terminates the entire workflow unnecessarily.

---

**Q55.** After running on "impact of AI on creative industries," each subagent completes successfully but the final reports cover only visual arts, missing music, writing, and film production. The coordinator decomposed the topic into: "AI in digital art creation," "AI in graphic design," and "AI in photography." What is the most likely root cause?

A) The synthesis agent lacks instructions for identifying coverage gaps in the findings it receives from other agents.
B) The document analysis agent is filtering out sources related to non-visual creative industries due to overly restrictive relevance criteria.
C) The coordinator agent's task decomposition is too narrow, resulting in subagent assignments that don't cover all relevant domains.
D) The web search agent's queries are not comprehensive enough and need to be expanded to cover more creative industry sectors.

**Correct Answer: C**
*Task 1.2: Orchestrate multi-agent systems with coordinator-subagent patterns*

The coordinator's logs reveal the root cause directly: it decomposed "creative industries" into only visual arts subtasks. The subagents executed their assigned tasks correctly. The problem is what they were assigned.

---

**Q56.** A multi-agent research pipeline aggregates findings from six subagents, each returning 800-1,200 tokens of raw tool output and reasoning. The synthesis agent receives all results in a single large message. The final report consistently omits or contradicts findings that appeared in the middle sections of the aggregated input. What is the most likely cause and the most effective mitigation?

A) The synthesis agent is hitting its output token limit; increase `max_tokens` to allow a longer response.
B) The synthesis agent's context window is exhausted; route some subagent outputs through a secondary summarization agent before passing to synthesis.
C) A "lost in the middle" effect; put key-findings summaries at the start of the aggregated input and add explicit section headers.
D) The subagents are returning conflicting information; add a deduplication step before synthesis.

**Correct Answer: C**
*Task 5.1: Manage conversation context to preserve critical information across long interactions*

The "lost in the middle" effect is a well-documented limitation where models attend less reliably to content in the middle of long inputs. Placing key findings at the beginning and using explicit section headers to organize the aggregated input significantly mitigates this effect. Option D addresses data consistency but not the positional attention problem. Option A addresses output length, not input attention. Option B adds pipeline complexity and may help with context length, but does not address the positional attention issue on its own.

---

**Q57.** Two credible sources report different figures for the size of the same market: one says $4.2B and the other $6.1B. How should the synthesis agent handle this in the report?

A) Present both figures with their source attribution and explicitly note the discrepancy between them.
B) Average the two figures and present the result as the best available estimate of the market size.
C) Omit the market-size claim from the report entirely, since conflicting data cannot be relied upon.
D) Report only the figure from the more recently published source, since newer data supersedes older data.

**Correct Answer: A**
*Task 5.6: Preserve information provenance and handle uncertainty in multi-source synthesis*

When credible sources conflict, the synthesis should annotate the conflict with source attribution rather than arbitrarily selecting one value. Option D is an arbitrary selection rule; the newer figure may use a different methodology. Option B fabricates a number that no source reported. Option C discards relevant information the reader needs.

---

**Q58.** To cut latency, an engineer lets the web search subagent send its findings directly to the synthesis subagent, bypassing the coordinator. Soon, failed searches go unnoticed and reports include findings nobody evaluated. Which design principle was violated?

A) Subagents should share a single context window so that findings never need to be passed at all.
B) Communication between subagents should route through the coordinator for observability and consistent error handling.
C) Subagents should each run on a different model so that errors are caught through diversity.
D) Subagent outputs should be cached so that any failed searches can simply be replayed later.

**Correct Answer: B**
*Task 1.2: Orchestrate multi-agent systems with coordinator-subagent patterns*

In a hub-and-spoke architecture, the coordinator manages all inter-subagent communication, error handling, and information routing. Bypassing it removes the point where output is evaluated and failures are handled. Option A contradicts the isolation that makes subagents useful. Options C and D do not restore the coordinator's oversight.

---

**Q59.** The document analysis subagent has a general-purpose `fetch_url` tool for loading the documents the coordinator assigns. Logs show that it sometimes follows links inside those documents and browses unrelated websites, duplicating the web search agent's job. What is the best fix?

A) Replace `fetch_url` with a constrained `load_document` tool that validates that the URL points to a document.
B) Remove URL access entirely and have the coordinator paste each document's full text into the subagent prompt.
C) Add a system prompt instruction telling the subagent that it must never follow links found inside documents.
D) Give the web search agent the same tool so that either agent can handle whichever links happen to come up.

**Correct Answer: A**
*Task 2.3: Distribute tools appropriately across agents and configure tool_choice*

Replacing a generic tool with a constrained alternative removes the capability for misuse while preserving the legitimate use. Option C is probabilistic and leaves the general capability in place. Option B over-corrects, bloating the coordinator's context and prompt sizes. Option D blurs role boundaries further instead of restoring them.

---

**Q60.** A research synthesis agent is combining findings from five subagents that searched different sources. The final report states that "AI adoption in healthcare reached 45% in 2024" but does not cite which source this came from. A reviewer cannot verify the claim because the subagents' individual outputs were not preserved. What structural change to the pipeline would prevent this provenance loss?

A) Add a post-synthesis review step where a separate agent checks each claim in the report against the raw subagent outputs.
B) Have subagents emit structured claim-source mappings and require the synthesis agent to preserve them in the final report.
C) Store all raw subagent outputs in a separate log file so they can be consulted if a claim needs verification.
D) Require the synthesis agent to add a generic "Sources consulted" section at the end of the report listing all sources accessed.

**Correct Answer: B**
*Task 5.6: Preserve information provenance and handle uncertainty in multi-source synthesis*

The root cause of provenance loss is that summarization steps compress findings without preserving claim-to-source mappings. Requiring subagents to output structured mappings and instructing the synthesis agent to preserve and merge them ensures that each claim in the final report carries its source attribution through the pipeline. Option D produces a list of sources consulted but does not link individual claims to specific sources. Option C stores raw data as a fallback but does not integrate provenance into the report itself. Option A adds a verification step after the fact but does not prevent the structural provenance loss.

---

**Q61.** Your multi-agent research system has a web search subagent that consistently returns findings without identifying which sources correspond to which claims. When the synthesis agent receives these findings, it cannot produce properly cited reports.

What is the correct fix during context passing from the web search subagent to the synthesis agent?

A) Configure the web search subagent to return only source URLs, and have the synthesis agent re-read each source to reconstruct the findings.
B) Instruct the synthesis agent to run its own web searches to re-locate the original sources.
C) Have the subagent return structured output that keeps each claim attached to its source metadata (URL, date, page), and pass that structure on.
D) Have the coordinator concatenate all subagent outputs into a single text block before forwarding to synthesis, since synthesis will extract citations naturally.

**Correct Answer: C**
*Task 1.3: Configure subagent invocation, context passing, and spawning*

Structured data formats that separate content from metadata ensure that claim-source mappings survive the handoff between agents. When context is passed as unstructured text, citation information is easily lost. Option B introduces redundant work and potentially different search results. Option D risks losing the claim-source associations during concatenation. Option A is extremely inefficient and requires the synthesis agent to redo retrieval work.

---

**Q62.** A web search subagent in your research system calls `search_web` and receives the following response: `{"results": [], "status": "success"}`. The subagent reports to the coordinator: "Web search was successful but no relevant results were found." Later you discover the search API was actually down and returning empty results for all queries.

What change to the MCP tool's error handling would prevent this confusion?

A) Always return a non-empty results array by including fallback content when the actual search returns nothing.
B) Implement automatic retry in the MCP tool itself, so the agent never sees an empty result unless all of the retries were exhausted.
C) Have the tool set `isError` for access failures and reserve empty successful results for searches that genuinely found no matches.
D) Add a `confidence` field to the response so the agent can infer whether the empty result is a real outcome or a failure.

**Correct Answer: C**
*Task 2.2: Implement structured error responses for MCP tools*

Access failures and valid empty results are fundamentally different conditions that require different agent responses. Using the `isError` flag for access failures while returning `{"results": [], "status": "success"}` only for genuine empty-result queries gives the coordinator accurate information to make retry and recovery decisions. Option A masks failures by fabricating content. Option D introduces ambiguity; a confidence score on a genuinely empty result is meaningless. Option B handles retries locally but does not solve the agent's inability to distinguish the two conditions.

---

**Q63.** The synthesis output for a query on "renewable energy policy" is thorough on solar and wind but contains nothing on grid storage, which the original query named explicitly. What should the coordinator do?

A) Restart the entire pipeline from the beginning with a reworded version of the original query.
B) Ask the synthesis agent to write the storage section itself, drawing on its general knowledge.
C) Deliver the report with a disclaimer attached, since every subagent completed the task that it was assigned.
D) Evaluate the output for gaps, re-delegate targeted research on storage, and then re-invoke synthesis.

**Correct Answer: D**
*Task 1.2: Orchestrate multi-agent systems with coordinator-subagent patterns*

The coordinator is responsible for an iterative refinement loop: evaluate synthesis output for gaps, re-delegate targeted work, and re-invoke synthesis until coverage is sufficient. Option C ships a known gap. Option B produces unsourced content in a system whose value is cited research. Option A discards good work and may reproduce the same gap.

---

## Scenario 4: Developer Productivity with Claude

You are building developer productivity tools using the Claude Agent SDK. The agent helps engineers explore unfamiliar codebases, understand legacy systems, generate boilerplate, and automate repetitive tasks. It uses built-in tools (Read, Write, Edit, Bash, Grep, Glob) and MCP servers.

**Primary domains:** Domain 2, Domain 3, Domain 1

---

**Q64.** You ask the agent to "add comprehensive tests to this legacy codebase." It begins writing tests for files in alphabetical order and runs out of context after thirty trivial utility files, leaving the core billing logic untested. What approach works better?

A) Map the structure first, identify high-impact areas, then follow a prioritized plan that adapts.
B) Raise the session's context budget and let the agent continue through the files in order.
C) Split the files evenly across parallel subagents so that each file ends up with a test.
D) Give the agent a fixed sequence to follow: one test file for each source file, in directory order.

**Correct Answer: A**
*Task 1.6: Design task decomposition strategies for complex workflows*

Open-ended tasks call for adaptive decomposition: map the structure, identify high-impact areas, and build a prioritized plan that adapts as dependencies are discovered. Option D formalizes the unprioritized approach that already failed. Option B delays the same failure. Option C parallelizes without prioritizing, so effort is still spread evenly over trivial and critical code.

---

**Q65.** You are running a multi-phase codebase investigation using the Claude Agent SDK. After 45 minutes of exploration (reading files, tracing call chains, building a dependency map) you move into the second phase: identifying security vulnerabilities in the authentication module. You notice the agent is now describing the authentication module as "using standard JWT patterns" when earlier in the session it had found a custom token signing implementation. What technique would most effectively preserve key findings across these phase boundaries?

A) Use `/compact` before starting the second phase to free up context space and allow the agent to re-read files as needed.
B) Increase the `max_tokens` parameter so the model can hold more context without compressing earlier findings.
C) Have the agent write key findings to a scratchpad file after each phase and read it at the start of the next phase.
D) Restart the session with a fresh context at the start of each phase, passing a manual summary of what you found.

**Correct Answer: C**
*Task 5.4: Manage context effectively in large codebase exploration*

Scratchpad files are the recommended technique for persisting key findings across context boundaries when context degradation becomes apparent. The agent can write structured notes during exploration and read them back at phase boundaries, ensuring critical findings, like the custom token signing implementation, are not lost to context compression. Option A uses `/compact` to free up space, but this compresses conversation history and may lose the specific finding about the custom token signing. Option D is a valid but costly approach: restarting sessions loses the accumulated understanding and requires manual intervention. Option B is incorrect because `max_tokens` controls output length, not context window size, and would not prevent the degradation.

---

**Q66.** A developer wants to try an experimental MCP server for a personal workflow. It should be available to them across their projects but must not appear for teammates. Where should it be configured?

A) In `.claude/rules/`, with frontmatter that restricts the server to their username.
B) In the project `CLAUDE.md`, listed under a section for personal tooling.
C) In the project's `.mcp.json` file, with a note that marks the server as experimental for now.
D) In their user-scoped `~/.claude.json`, which is not shared through version control.

**Correct Answer: D**
*Task 2.4: Integrate MCP servers into Claude Code and agent workflows*

MCP servers are scoped by where they are configured: project-level `.mcp.json` for shared team tooling, user-level `~/.claude.json` for personal or experimental servers. Option C shares the server with everyone who clones the repository. Options A and B describe files that hold instructions for Claude, not MCP server configuration.

---

**Q67.** Your team wants the agent to read and update Jira tickets. An engineer proposes building a custom MCP server for this. What should you recommend first?

A) Build the custom server so that every tool description can be tuned to the team's own terminology.
B) Skip MCP entirely and have the agent call the Jira REST API through `Bash` using `curl` commands.
C) Use an existing community Jira MCP server, reserving custom servers for team-specific workflows.
D) Expose Jira tickets only as MCP resources, since an issue tracker does not really need any tools.

**Correct Answer: C**
*Task 2.4: Integrate MCP servers into Claude Code and agent workflows*

For standard integrations, an existing community MCP server is preferable to building and maintaining a custom one; custom servers are for workflows that are specific to the team. Option A spends engineering effort on a solved problem. Option B gives up structured tool interfaces and error handling. Option D cannot update tickets, because resources expose content rather than actions.

---

**Q68.** An engineering team asks you to design a Claude-based system to investigate a production incident. The system must root-cause a bug that was introduced somewhere in the past two weeks across an unknown set of files and services. The scope of the investigation cannot be known in advance.

Which decomposition approach is most appropriate?

A) Split the investigation between two agents: one agent reads logs while the other reads source code, and they report findings independently to a human operator.
B) Prompt chaining: design a fixed sequence of investigation steps (check logs, read configs, trace service calls) that the agent executes in order.
C) Have the agent run a comprehensive search of all changed files in the past two weeks and produce a ranked list of candidates for manual review.
D) Dynamic adaptive decomposition: the agent first maps the affected services and symptom timeline, then generates and prioritizes investigation subtasks based on what is discovered at each step.

**Correct Answer: D**
*Task 1.6: Design task decomposition strategies for complex workflows*

Open-ended investigation tasks with unknown scope require dynamic adaptive decomposition, where the agent builds its investigation plan based on intermediate findings rather than following a fixed sequence. A static prompt chain cannot adapt when the investigation reveals unexpected service dependencies or anomalous patterns. Option B is appropriate for predictable multi-aspect reviews, not exploratory investigations. Option A removes the coordinating intelligence and requires human intervention for synthesis. Option C is a single-pass heuristic that does not apply the model's reasoning capability.

---

**Q69.** Your MCP server exposes `search_symbols`, which queries a pre-built code index and returns definitions with cross-references. The agent almost always uses the built-in `Grep` tool instead and misses the cross-references. The MCP tool's description reads "Searches code." What is the best fix?

A) Add a `PreToolUse` hook that rewrites every `Grep` call into an equivalent `search_symbols` call.
B) Expand the MCP tool's description to explain its capabilities, outputs, and when to prefer it over text search.
C) Remove `Grep` from the agent's allowed tools so that the MCP tool becomes its only search option.
D) Rename the MCP tool to `grep_v2` so the model associates it with the search tool it already prefers.

**Correct Answer: B**
*Task 2.4: Integrate MCP servers into Claude Code and agent workflows*

A minimal description gives the model no reason to choose the more capable MCP tool over a familiar built-in. Enhancing the description to explain capabilities and outputs fixes the selection problem at its source. Option C removes a tool that is still the right choice for plain text search. Option A forces the wrong tool for searches that are not symbol lookups. Option D makes the tool look like a duplicate rather than explaining what is different about it.

---

**Q70.** In a custom agent loop, the agent calls `search_codebase` with the same query again and again until the iteration cap stops it. The loop executes each tool call and then sends a new request containing only the original user message. What is the bug?

A) Tool results are never appended to the conversation history, so the model cannot see them.
B) The tool's description does not say that results are final, so the model keeps checking again.
C) The `tool_choice` setting is `"auto"`, which permits the model to call a tool more than once.
D) The iteration cap is set too high, which leaves the model with room to repeat its tool calls.

**Correct Answer: A**
*Task 1.1: Design and implement agentic loops for autonomous task execution*

Tool results must be appended to the conversation history so the model can reason about them in the next iteration. Without them, every request looks like the first turn and the model makes the same call again. Option B treats a loop bug as a description problem. Option D changes when the loop stops, not why it repeats. Option C describes normal, correct behavior.

---

**Q71.** An engineer asks the agent how request authentication works in an unfamiliar service with 3,000 files. What exploration strategy is most effective?

A) Use `Read` on every file under `src/` first, so the agent has complete context before answering.
B) Use `Glob` to list all source files, then `Read` them in order until the relevant logic turns up.
C) Ask the engineer to paste in the relevant files directly, since exploration tools consume too much context.
D) Use `Grep` to find entry points such as auth middleware, then `Read` those files and follow imports.

**Correct Answer: D**
*Task 2.5: Select and apply built-in tools (Read, Write, Edit, Bash, Grep, Glob) effectively*

Codebase understanding should be built incrementally: start with `Grep` to locate entry points, then `Read` to follow imports and trace the flow. Options A and B read files indiscriminately and exhaust context before the relevant code is understood. Option C pushes the work back to an engineer who, by the premise, does not know the codebase.

---

**Q72.** A developer productivity agent must change one of three byte-for-byte identical configuration blocks in a file. `Edit` fails because the target text is not unique, and a retry with more surrounding context fails again because the neighboring lines are identical too. What is the appropriate fallback?

A) Use `Grep` to find the line number of each occurrence, then call `Edit` with a line-number parameter for the right one.
B) Use `Bash` to run a `sed` substitution, which will apply the new value to the matching text wherever that text appears in the file.
C) Retry `Edit` with `replace_all` enabled so the non-unique match no longer causes the tool call to be rejected.
D) Use `Read` to load the full file, then use `Write` to save a complete corrected version with only the intended block changed.

**Correct Answer: D**
*Task 2.5: Select and apply built-in tools (Read, Write, Edit, Bash, Grep, Glob) effectively*

When `Edit` cannot find a unique anchor, `Read` followed by `Write` is the reliable fallback: the agent rewrites the file with exactly the intended change. Option B changes every occurrence rather than the one intended and bypasses the dedicated file tools. Option A relies on a line-number parameter that `Edit` does not have. Option C avoids the error but modifies all three blocks.

---

**Q73.** A developer productivity agent has a `PostToolUse` hook that transforms raw Bash output. Currently the hook appends a formatted summary but also preserves the full raw output in the result passed to the model. Sessions exploring large codebases are hitting context limits faster than expected.

What change would most effectively reduce unnecessary context consumption from tool results?

A) Have the hook return only the formatted summary, dropping the raw output instead of passing both to the model.
B) Disable the `PostToolUse` hook entirely and let the model process raw Bash output directly.
C) Switch from `PostToolUse` hooks to pre-processing the Bash commands themselves to produce shorter output.
D) Increase the model's `max_tokens` parameter to accommodate the additional context from both raw and formatted output.

**Correct Answer: A**
*Task 1.5: Apply Agent SDK hooks for tool call interception and data normalization*

`PostToolUse` hooks can trim verbose tool outputs to only the relevant data before the model processes them. Keeping both raw and summary output doubles the context consumption from each tool call. Modifying the hook to return only the formatted summary addresses the root cause directly. Option B removes normalization benefits. Option D increases output capacity but does not address the growing input context. Option C would require significant changes to tool invocation patterns and may not be feasible for all commands.

---

**Q74.** To plan a migration, the agent needs a list of every test file in the repository, wherever it lives. Test files follow the naming pattern `*.test.tsx`. Which tool is the right choice?

A) `Grep` with the pattern `test`, since it searches across the entire codebase very quickly.
B) `Read` on each directory in turn, to enumerate the files that it contains.
C) `Bash` running a recursive `ls`, with the model filtering the output.
D) `Glob` with the pattern `**/*.test.tsx`, since it matches files by name pattern.

**Correct Answer: D**
*Task 2.5: Select and apply built-in tools (Read, Write, Edit, Bash, Grep, Glob) effectively*

`Glob` finds files by name or extension pattern; `Grep` searches file contents. Option A would match any file containing the word "test", which is a different and much noisier question. Option B misuses `Read`, which loads file contents. Option C pulls a full listing into context when a dedicated tool answers the question directly.

---

**Q75.** A developer productivity agent needs to find all TypeScript files in a project that import from a deprecated module named `legacy-auth`. The project has thousands of files across many directories.

Which combination of built-in tools is most appropriate for this task?

A) Use `Grep` to search for the import pattern across all TypeScript files in the codebase.
B) Use `Read` on the project root directory to get a file listing, then recursively `Read` each subdirectory.
C) Use `Glob` to find all `.ts` files, then use `Read` to open each file and check whether it contains the import.
D) Use `Bash` to run `find . -name "*.ts"` and then `Bash` again to run `grep` on each file found.

**Correct Answer: A**
*Task 2.5: Select and apply built-in tools (Read, Write, Edit, Bash, Grep, Glob) effectively*

`Grep` is the correct built-in tool for searching file contents across a codebase. It efficiently searches all TypeScript files for the import pattern without requiring separate file enumeration. Option D uses Bash shell commands that should be replaced by dedicated tools when those tools are available. Option C uses `Glob` for enumeration and then `Read` on each file, which is far less efficient than `Grep` for a content search. Option B uses `Read` for directory traversal, which is not a supported use of that tool.

---

**Q76.** Your agent has `Bash` access for running builds and tests. Company policy forbids force-pushing to shared branches. The system prompt states the rule, yet logs show two violations last month. What gives the strongest guarantee?

A) Add few-shot examples that show the agent declining requests that involve force-pushing.
B) Restate the rule in stronger language and move it to the very top of the system prompt.
C) Review the session logs each week and revert any force-pushes that the agent has performed since then.
D) Add a hook that intercepts `Bash` tool calls and blocks commands matching force-push patterns.

**Correct Answer: D**
*Task 1.5: Apply Agent SDK hooks for tool call interception and data normalization*

Rules that must hold every time need deterministic enforcement. A hook that intercepts outgoing tool calls can block policy-violating commands regardless of how the model interprets its prompt. Options A and B improve compliance probabilistically, which has already proven insufficient. Option C acts after the damage is done.

---

**Q77.** A developer productivity agent investigates bug reports by calling `search_codebase`, `read_file`, and `run_tests`. During a code review, a colleague proposes adding an iteration cap: if the loop has not finished after 15 tool calls, terminate with a generic "investigation incomplete" response.

What is the correct characterization of this design?

A) A cap is a reasonable safety net against runaway loops, but `stop_reason` `"end_turn"` should remain the primary termination signal.
B) The cap should be replaced with a wall-clock timeout, because elapsed time tracks task completion more reliably than tool call count.
C) Iteration caps are unnecessary if the system prompt instructs the agent to always request only the minimum tools needed.
D) Iteration caps are the recommended primary stopping mechanism because they prevent runaway costs in production.

**Correct Answer: A**
*Task 1.1: Design and implement agentic loops for autonomous task execution*

The agentic loop should terminate primarily when `stop_reason` equals `"end_turn"`, which signals that the model has finished its task. An iteration cap can serve as a safety guardrail against runaway loops, but treating it as the primary stopping mechanism means the loop may cut off legitimate multi-step investigations. Options B and D misstate recommended practice. Option C conflates prompt-based guidance with loop control: even a well-prompted agent may legitimately need many tool calls for complex investigations.

---

**Q78.** An agent is performing a deep exploration of a 200,000-line legacy codebase to understand its payment processing flow. After approximately 90 minutes and dozens of file reads, the agent begins referencing "standard patterns in payment systems" rather than the specific classes and flows it found earlier, and its answers become inconsistent with findings from the first hour. What is the most likely cause and the best mitigation strategy?

A) Context degradation in a long session; have the agent record key findings in a scratchpad file and consult it as it works.
B) The legacy codebase's file structure is too complex for a single agent; break it into independent subsystems and run separate agents on each subsystem simultaneously.
C) The agent is using the wrong tools; switching from `Read` to `Grep` for file exploration would reduce context consumption.
D) The earliest file reads were evicted by a sliding context window; raise `max_tokens` so the first hour of results stays available.

**Correct Answer: A**
*Task 5.4: Manage context effectively in large codebase exploration*

Context degradation in extended sessions is a known pattern: the model starts giving inconsistent answers and referencing "typical patterns" rather than the specific classes it discovered earlier. A scratchpad file creates a persistent, explicit record of key findings that survives context pressure. Option D misidentifies the mechanism, and `max_tokens` controls output length, not how much input is retained. Option B adds parallelism but does not address degradation within a session. Option C changes tooling but does not preserve findings already made.

---

**Q79.** A long multi-agent codebase analysis crashes at hour three. On restart, every subagent begins from scratch because its progress existed only in conversation context. What design enables recovery?

A) The coordinator re-sends its complete conversation history to each of the subagents whenever the run is restarted.
B) Each agent exports its state to a known location, and the coordinator loads a manifest of that state on resume.
C) The whole analysis runs inside one agent, so only a single context ever needs to be restored.
D) Each subagent is given a larger context window so that its progress is less likely to be lost.

**Correct Answer: B**
*Task 5.4: Manage context effectively in large codebase exploration*

Structured state persistence enables crash recovery: agents export state to known locations and the coordinator loads a manifest on resume, injecting it into agent prompts. Option A cannot work because the conversation context was lost in the crash. Option D confuses context capacity with persistence. Option C makes the analysis more fragile, not less.

---

**Q80.** A developer productivity agent frequently makes multiple exploratory tool calls to discover what data sources are available in your MCP server before it can answer user questions. This pattern increases latency and consumes context for routine requests.

What MCP feature most directly addresses this discovery overhead?

A) Expose content catalogs as MCP resources so the agent can see what data exists without exploratory tool calls.
B) Add a caching layer that stores the results of previous exploratory calls and reuses them across sessions.
C) Add a `list_tools` meta-tool to the MCP server that returns all available tool names and descriptions.
D) Reduce the number of tools in the MCP server by merging similar tools together to minimize the discovery surface.

**Correct Answer: A**
*Task 2.4: Integrate MCP servers into Claude Code and agent workflows*

MCP resources are designed to expose content catalogs so agents know what data is available without making exploratory tool calls. This gives the agent upfront visibility at connection time, reducing the need for repeated discovery queries. Option C would still require a tool call to discover available resources. Option D reduces functionality to avoid a structural problem. Option B addresses symptom rather than cause, and cross-session caching of content catalogs may return stale data.

---

**Q81.** A developer returns to a week-old investigation session. Since then, a large refactor has renamed modules and moved most of the files that the session had read. What is the most reliable way to continue?

A) Resume the session with `--resume`; the agent will notice outdated results when its edits begin to fail.
B) Resume the session and run `/compact` so that the stale tool results get condensed into a summary.
C) Use `fork_session` on the old session so that its stale results stay behind in the original branch.
D) Start a new session and provide a structured summary of the earlier findings as the initial context.

**Correct Answer: D**
*Task 1.7: Manage session state, resumption, and forking*

When prior tool results are broadly stale, starting a new session with a structured summary is more reliable than resuming. Resumption suits cases where prior context is mostly valid and only a few known files changed. Option A lets the agent reason from outdated file contents. Option C copies the stale context into the fork. Option B condenses stale results but keeps them, in a less detectable form.

---

**Q82.** Your team is setting up a shared GitHub MCP server for all engineers on a project. The server requires a GitHub API token for authentication. You want every engineer who clones the repository to have the MCP server available without each person having to manually configure it, and you want to avoid committing the actual token to version control.

What is the correct configuration approach?

A) Create a setup script that each developer runs once to add the MCP server to their personal `~/.claude.json` with their own token.
B) Add the MCP server to `~/.claude.json` on each developer's machine with their personal token hardcoded.
C) Add the MCP server configuration to the root `CLAUDE.md` file under a `[mcp_servers]` section.
D) Define the server in the project-scoped `.mcp.json` using `${GITHUB_TOKEN}` environment variable expansion, and commit that file.

**Correct Answer: D**
*Task 2.4: Integrate MCP servers into Claude Code and agent workflows*

Project-scoped `.mcp.json` with environment variable expansion is the correct pattern for shared MCP servers: it is committed to the repository so all team members get the configuration automatically, and tokens are injected via environment variables at runtime rather than committed as plaintext. Option B requires manual per-person setup and hardcodes tokens. Option C describes a configuration mechanism that does not exist in CLAUDE.md. Option A also requires manual setup and does not solve the commit-to-version-control problem.

---

**Q83.** Your project `CLAUDE.md` contains universal coding standards plus a 150-line database migration runbook that is needed only a few times a month. Developers complain that the file is bloated. What is the right restructuring?

A) Move the coding standards into a skill, and keep the runbook in `CLAUDE.md` since it is the longer of the two.
B) Move both the standards and the runbook into `~/.claude/CLAUDE.md` so that the project file stays small.
C) Move the runbook into a skill that is invoked on demand, and keep the universal standards in `CLAUDE.md`.
D) Keep both in `CLAUDE.md`, but move the runbook to the end of the file, where it will carry less weight.

**Correct Answer: C**
*Task 3.2: Create and configure custom slash commands and skills*

Skills are for task-specific workflows invoked on demand; `CLAUDE.md` is for universal standards that should always be loaded. Option A inverts this, making the always-needed standards optional. Option B makes team content personal and unshared. Option D leaves the runbook loaded in every session.

---

## Scenario 5: Claude Code for Continuous Integration

You are integrating Claude Code into CI/CD pipelines. The system runs automated code reviews, generates test cases, and provides pull request feedback. You need prompts that provide actionable feedback and minimize false positives.

**Primary domains:** Domain 3, Domain 4

---

**Q84.** Your CI reviewer's coordinator spawns one subagent per changed file with the prompt "Review src/billing/invoice.ts." The subagents ignore the team's review criteria and the pull request description, both of which are present in the coordinator's context. Why?

A) Subagents run on a smaller model that is unable to follow the team's review criteria.
B) Subagents start with isolated context, so the criteria and PR details must be included in each prompt.
C) Subagents take their criteria from the coordinator's tool descriptions, which omit them.
D) Subagents can read the coordinator's context only if they are spawned one at a time.

**Correct Answer: B**
*Task 1.3: Configure subagent invocation, context passing, and spawning*

Subagent context must be provided explicitly in the prompt; subagents do not inherit the coordinator's context. Each delegation should carry the criteria and relevant details the subagent needs. Option A is an assumption unrelated to the symptom. Options C and D describe inheritance mechanisms that do not exist.

---

**Q85.** Your review pipeline posts every finding from an independent verification pass straight to the pull request. Some findings are solid and others are speculative, but developers cannot tell them apart. You want solid findings posted automatically and speculative ones routed to a human triager. What should the verification pass produce?

A) A self-reported confidence level alongside each individual finding, which the pipeline uses to route findings.
B) Prose findings in which the model uses hedging language wherever it is unsure about what it has found.
C) One overall confidence score for the pull request, which is then applied to all of that pull request's findings.
D) Only those findings that three repeated runs of the verification pass all independently agree on.

**Correct Answer: A**
*Task 4.6: Design multi-instance and multi-pass review architectures*

A verification pass can report confidence alongside each finding, giving the pipeline a per-finding signal for calibrated review routing. Option C is too coarse: a single score cannot separate solid findings from speculative ones in the same pull request. Option B is not machine-routable. Option D suppresses real issues that are only caught intermittently and triples cost.

---

**Q86.** Your CI review runs on every push. Developers complain that after they push fixes, the bot re-posts the same comments, including ones that have already been addressed. What is the best fix?

A) Include the prior findings in context and instruct Claude to report only new or still-unaddressed issues.
B) Run the review only once per pull request, at the moment when it is first opened.
C) Reduce the review's sensitivity so that fewer comments are produced on each run.
D) Add a script that deletes all of the bot's earlier comments before each new run posts.

**Correct Answer: A**
*Task 3.6: Integrate Claude Code into CI/CD pipelines*

When re-running a review after new commits, including prior findings in context lets Claude report only new or unaddressed issues and avoid duplicates. Option B leaves later commits unreviewed. Option D hides the duplication but still re-reports addressed issues and destroys discussion history. Option C reduces real findings along with duplicates.

---

**Q87.** You plan to move a nightly review job to the Message Batches API. In the current real-time design, Claude calls a `get_file_context` tool mid-review and your code returns the result so it can continue. What must you account for?

A) Batch requests cannot include tool definitions, so structured output has to be given up.
B) Batch requests are limited to one tool call each, so the tools have to be merged into one.
C) Batch requests cannot execute tools mid-request and continue, so needed context must be supplied upfront.
D) Batch results are returned in submission order, so each tool call has to be numbered.

**Correct Answer: C**
*Task 4.5: Design efficient batch processing strategies*

The batch API does not support multi-turn tool calling within a single request: there is no way to execute a tool mid-request and return its result. Context the review needs must be included in the request upfront. Option A is false; tool definitions are still usable for structured output. Options B and D describe constraints that do not exist; results are correlated by `custom_id`.

---

**Q88.** A CI code review pipeline is generating false positive findings at a high rate. The team wants to understand which specific code constructs are being flagged incorrectly so they can refine the prompt. The current findings output only includes `file`, `line`, and `description`. What schema change would best enable systematic false positive analysis?

A) Add a `confidence` field (0-100) to each finding so the team can filter by confidence threshold.
B) Add a `detected_pattern` field to each finding that records the specific code construct or pattern that triggered the finding.
C) Add an `is_false_positive` boolean field and instruct Claude to self-label its own false positives.
D) Add a `category` field so findings can be grouped by issue type for aggregate analysis.

**Correct Answer: B**
*Task 4.4: Implement validation, retry, and feedback loops for extraction quality*

The `detected_pattern` field directly captures what code construct triggered each finding, enabling the team to identify which patterns produce the most false positives and update prompt criteria accordingly. Option A provides confidence scores but does not identify what prompted the finding. Option D allows grouping but not pattern-level debugging. Option C asks Claude to self-identify its own false positives, which is unreliable since the model cannot accurately distinguish true from false positives without ground truth.

---

**Q89.** Your review prompt asks Claude to label findings as critical, major, or minor. The same kind of issue receives different labels on different runs, so the team cannot gate merges on "critical." What is the most effective fix?

A) Set the temperature to zero so that the same label is produced on each run.
B) Define explicit criteria for each severity level, with concrete code examples of each.
C) Have Claude also output a confidence score for each severity label it assigns.
D) Collapse the three levels into a single "issue" label in order to remove the inconsistency.

**Correct Answer: B**
*Task 4.1: Design prompts with explicit criteria to improve precision and reduce false positives*

Consistent classification requires explicit severity criteria with concrete code examples for each level. Option A may make output more repeatable but does not make the labels correct, and similar issues in different code would still be labeled differently. Option C adds a poorly calibrated signal without defining the levels. Option D removes the information the team needs for merge gating.

---

**Q90.** A Claude-based code reviewer is generating inconsistent feedback on documentation quality: sometimes flagging missing docstrings for private helper functions, sometimes not; sometimes requiring full parameter descriptions, sometimes accepting one-line summaries. The team wants consistent, predictable documentation feedback on public API functions only. Which change most directly addresses the inconsistency?

A) Instruct Claude to "apply documentation standards consistently and carefully."
B) Run three parallel review instances and accept feedback that appears in at least two of the three.
C) Define explicit criteria: public API functions need a summary plus parameter and return descriptions; private functions are excluded.
D) Restrict the review prompt to only one concern at a time, alternating between security, documentation, and style in three separate runs.

**Correct Answer: C**
*Task 4.1: Design prompts with explicit criteria to improve precision and reduce false positives*

Explicit criteria that specify exactly what is required, for which functions, and at what level of detail eliminate the ambiguity that causes inconsistency. Without a clear definition of "documented," Claude must infer the threshold each time, leading to variable results. Option A is the type of general instruction that already produces the problem. Option B adds overhead and suppresses legitimate feedback that may only appear in one instance. Option D separates concerns but does not fix the definition of what counts as adequate documentation.

---

**Q91.** A pipeline job uses one Claude Code session to generate a database migration and then, in the same session, asks "review the migration you just wrote." These reviews almost never find issues, yet human reviewers regularly do. What should change?

A) Have the session explain its design decisions in detail before it starts on the review.
B) Ask the same session to review the migration twice and then merge the two resulting sets of findings.
C) Run the review as a separate, independent Claude Code invocation without the generation context.
D) Add an instruction to "be extremely critical" to the review request in the same session.

**Correct Answer: C**
*Task 3.6: Integrate Claude Code into CI/CD pipelines*

A session that generated code retains its reasoning context and is less effective at reviewing its own changes. An independent invocation examines the code without those assumptions. Options B and D keep the same biased context. Option A reinforces the original reasoning immediately before the review.

---

**Q92.** A CI pipeline uses Claude Code to review pull requests and needs to post inline comments on specific lines in GitHub. The pipeline currently receives Claude's output as unstructured text, which requires a fragile regex parser to extract file paths, line numbers, and comment text. The parser breaks regularly as Claude's output format drifts between runs. What is the most robust solution?

A) Use `--output-format json` combined with `--json-schema` to define a schema with `file`, `line`, and `comment` fields, so each finding is machine-parseable by construction.
B) Switch from inline comments to a single summary comment, which is easier to extract since it does not require line-level parsing.
C) Add stricter formatting instructions to the system prompt specifying the exact text structure expected, and add validation to reject any response that does not match it exactly.
D) Add a post-processing step that uses a second Claude call to normalize the first response into a consistent structured format.

**Correct Answer: A**
*Task 3.6: Integrate Claude Code into CI/CD pipelines*

Using `--output-format json` with `--json-schema` produces structured output that conforms to the defined schema by construction, eliminating format drift entirely. The pipeline can parse the JSON directly without a regex layer. Option C makes prompt instructions more rigid but still relies on Claude maintaining format consistency across runs, which is the root cause of the breakage. Option D adds latency and cost by introducing a second API call for normalization. Option B changes the feature behavior to work around the parsing problem rather than solving it.

---

**Q93.** Claude Code follows your team's review conventions on developers' laptops, but the same prompts run in CI ignore them. The conventions were written by the tech lead in `~/.claude/CLAUDE.md` and copied by each developer into their own home directory. What is the right fix?

A) Paste the full text of the conventions into every CI prompt passed to `claude -p`.
B) Set an environment variable in CI that points Claude Code at the tech lead's file.
C) Move the conventions into the project-level `CLAUDE.md` that is committed to the repository.
D) Add a CI step that copies the tech lead's file into the home directory of the pipeline runner.

**Correct Answer: C**
*Task 3.1: Configure CLAUDE.md files with appropriate hierarchy, scoping, and modular organization*

User-level configuration exists only on the machine where it was created. Team conventions belong in project-level configuration, which travels with the repository to every developer and to CI. Options A and D work around the scoping mistake and must be maintained separately from the copies on developers' machines. Option B relies on a mechanism that does not exist.

---

**Q94.** Your team wants to reduce API costs. Two workflows: (1) a blocking pre-merge check that must complete before developers can merge, and (2) a technical debt report generated overnight for review the next morning. Your manager proposes switching both to the Message Batches API for 50% cost savings. How should you evaluate this proposal?

A) Switch both to batch processing with a timeout fallback to real-time if batches take too long.
B) Keep real-time calls for both workflows to avoid batch result ordering issues.
C) Use batch processing for the technical debt reports only; keep real-time calls for pre-merge checks.
D) Switch both workflows to batch processing with status polling to check for completion.

**Correct Answer: C**
*Task 4.5: Design efficient batch processing strategies*

The Message Batches API has up to 24-hour processing times with no guaranteed latency SLA. This makes it unsuitable for blocking pre-merge checks but ideal for overnight batch jobs. Option D is wrong because relying on "often faster" completion isn't acceptable for blocking workflows. Option B reflects a misconception: batch results can be correlated using `custom_id` fields.

---

**Q95.** Your pipeline script runs `claude "Analyze this pull request for security issues"` but the job hangs indefinitely. Logs indicate Claude Code is waiting for interactive input. What's the correct approach?

A) Add the `-p` flag: `claude -p "Analyze this pull request for security issues"`
B) Set the environment variable `CLAUDE_HEADLESS=true` before running the command
C) Add the `--batch` flag: `claude --batch "Analyze this pull request for security issues"`
D) Redirect stdin from `/dev/null`: `claude "Analyze this pull request for security issues" < /dev/null`

**Correct Answer: A**
*Task 3.6: Integrate Claude Code into CI/CD pipelines*

The `-p` (or `--print`) flag is the documented way to run Claude Code in non-interactive mode. Options B and C reference non-existent features. Option D is a Unix workaround that doesn't properly address Claude Code's command syntax.

---

**Q96.** You are building an automated code review system using Claude. The review must cover three aspects for every pull request: security vulnerabilities, style compliance, and performance implications. Each aspect has clear, defined criteria documented in your engineering handbook.

Which decomposition strategy is most appropriate?

A) Spawn three fully independent agents without shared context, then merge their outputs in a final aggregation step.
B) Dynamic adaptive decomposition: have the agent start by scanning the full pull request and generate a review plan based on what it finds there.
C) Prompt chaining with sequential focused passes: one pass per review aspect (security, style, performance), each with dedicated criteria.
D) A single comprehensive pass that examines all three aspects simultaneously to capture cross-cutting concerns.

**Correct Answer: C**
*Task 1.6: Design task decomposition strategies for complex workflows*

When a workflow has predictable, well-defined aspects that must each be covered, prompt chaining with sequential focused passes is the appropriate pattern. Each pass dedicates full attention to one concern rather than dividing attention across all three. Option B uses dynamic decomposition for a workflow whose structure is already known, adding unnecessary overhead. Option D suffers from the attention dilution problem that prompt chaining is designed to solve. Option A loses cross-file integration context by fully isolating the three agents.

---

**Q97.** Explicit criteria reduced false positives, but the reviewer still flags your codebase's intentional patterns, such as empty `catch` blocks in best-effort cleanup code, whenever they differ slightly from the exclusions listed in the prompt. What is the best next step?

A) Disable the error-handling category permanently, since it produces too much noise.
B) Add few-shot examples contrasting acceptable patterns with genuine issues, including the reasoning.
C) Tell Claude to flag only those issues about which it is completely certain.
D) Keep extending the exclusion list each time a new variation of the pattern gets flagged.

**Correct Answer: B**
*Task 4.2: Apply few-shot prompting to improve output consistency and quality*

Few-shot examples that distinguish acceptable patterns from genuine issues, with reasoning, let Claude generalize to novel variations instead of matching only pre-specified cases. Option D is unbounded maintenance that never generalizes. Option A gives up real findings in the category. Option C is a vague instruction of the kind that does not improve precision.

---

**Q98.** A CI pipeline runs Claude Code to generate test cases for each pull request. The team discovers that Claude is consistently suggesting test scenarios that already exist in the existing test files, wasting review time. Which approach in the CLAUDE.md configuration most directly addresses this problem?

A) Add a post-processing script to the pipeline that compares Claude's suggestions against the existing test files and filters duplicates.
B) Document in `CLAUDE.md` the testing standards, available fixtures, and instruct Claude to review existing test files before suggesting new scenarios.
C) Use `--output-format json` with `--json-schema` so that test suggestions are machine-parseable for deduplication.
D) Add the `-p` flag to the CI invocation command to prevent interactive prompts.

**Correct Answer: B**
*Task 3.6: Integrate Claude Code into CI/CD pipelines*

Providing existing test files in context and documenting testing standards in `CLAUDE.md` directly instructs Claude to avoid duplicate suggestions at generation time. This is the most efficient fix because it addresses the root cause: Claude does not know what tests already exist. Option D prevents interactive hangs but does not affect test content. Option C improves parseability but does not prevent duplicate suggestions. Option A is a workaround that adds pipeline complexity without fixing the underlying issue.

---

**Q99.** A CI code review prompt flags 60% of pull requests for "potential security vulnerabilities." Developers have stopped reading the reports because nearly all flags are false positives on standard input validation patterns they consider acceptable. Adding "only report high-confidence findings" to the prompt has had no measurable effect. What is the most effective next step?

A) Add a post-processing confidence threshold: discard any finding where Claude rates its own confidence below 80%.
B) Replace the security prompt with a rule-based static analysis tool, accepting that it cannot catch context-dependent issues.
C) Move the review to a larger model tier, since stronger reasoning should improve its judgment about which issues are real.
D) Temporarily disable the category, then add explicit criteria with code examples separating reportable issues from acceptable patterns.

**Correct Answer: D**
*Task 4.1: Design prompts with explicit criteria to improve precision and reduce false positives*

General instructions like "only report high-confidence findings" fail to reduce false positives because they do not define what counts as a positive. Temporarily disabling the noisy category restores developer trust immediately while explicit criteria with examples give Claude the specificity needed to distinguish real issues from acceptable patterns. Option B abandons the AI-based review entirely rather than fixing it. Option C is unlikely to change false positive rates when the root cause is imprecise criteria. Option A relies on self-reported confidence scores, which are poorly calibrated for LLMs.

---

**Q100.** A reporting job must deliver results within 30 hours of a document's arrival. Batches can take up to 24 hours to process. How often should documents be submitted in batches?

A) Once every 24 hours, so that submissions line up exactly with the batch processing window.
B) At any convenient interval, because most batches finish in well under an hour.
C) Every 4 hours, so that waiting time plus up to 24 hours of processing fits within 30 hours.
D) Once every 30 hours, so that submissions line up with the delivery deadline.

**Correct Answer: C**
*Task 4.5: Design efficient batch processing strategies*

Submission frequency must be derived from the SLA: the longest a document waits for submission plus the 24-hour processing window must fit within the deadline. With 4-hour windows the worst case is 28 hours. Option A allows a worst case of 48 hours and Option D 54 hours. Option B relies on typical completion times, which carry no guarantee.

---

**Q101.** A team uses Claude to generate code review comments for pull requests. The comments are technically accurate but vary widely in format: some include file paths and line numbers, others are vague summaries, some use bullet points, and others write prose paragraphs. Developers want a consistent, actionable format: file path, line number, issue description, suggested fix. What is the most effective way to achieve this?

A) Add a format specification to the system prompt that lists each of the four required fields by name.
B) Add 2-4 few-shot examples showing the exact output format (path, line, issue, fix) across different issue types.
C) Ask Claude to self-review its output and reformat any comment that does not match the required four-part structure.
D) Use `--output-format json` and parse the results in a post-processing step to normalize format.

**Correct Answer: B**
*Task 4.2: Apply few-shot prompting to improve output consistency and quality*

Few-shot examples demonstrating the exact desired output format are the most effective technique for achieving consistently formatted output when detailed instructions alone produce inconsistent results. Seeing concrete examples of the format makes the requirement unambiguous. Option A is a format specification that has likely already been tried given the problem description. Option D introduces parsing complexity and does not ensure consistent generation. Option C adds a round-trip that may still produce inconsistent intermediate output.

---

**Q102.** A pull request modifies 14 files across the stock tracking module. Your single-pass review produces inconsistent results: detailed feedback for some files, superficial comments for others, obvious bugs missed, and contradictory feedback. How should you restructure the review?

A) Split into focused passes: analyze each file individually for local issues, then run a separate integration-focused pass examining cross-file data flow.
B) Switch to a higher-tier model with a larger context window to give all 14 files adequate attention in one pass.
C) Require developers to split large PRs into smaller submissions of 3-4 files before the automated review runs.
D) Run three independent review passes on the full PR and only flag issues that appear in at least two of the three runs.

**Correct Answer: A**
*Task 4.6: Design multi-instance and multi-pass review architectures*

Splitting reviews into focused passes directly addresses attention dilution. Option C shifts burden to developers without improving the system. Option B misunderstands that larger context windows don't solve attention quality issues. Option D would suppress detection of real bugs by requiring consensus on issues that may only be caught intermittently.

---

**Q103.** A Claude-based pull request reviewer raises "magic number" warnings on every numeric literal in the codebase, including well-understood constants like HTTP status codes and standard buffer sizes. Developers want magic numbers flagged only when they appear in business logic with no explanation. How should the prompt be updated?

A) Add an instruction telling Claude to use good judgment about whether a given numeric literal is truly a magic number.
B) Maintain an allowlist of specific numeric values, such as 200, 404, and 1024, that the reviewer must never flag.
C) Add a severity field to each finding and instruct Claude to omit any magic-number finding that it rates as low severity.
D) Define explicit criteria: flag unexplained literals in business logic; exclude HTTP status codes, standard sizes, and documented values.

**Correct Answer: D**
*Task 4.1: Design prompts with explicit criteria to improve precision and reduce false positives*

Explicit, specific criteria that define what to report and what to exclude are far more effective than general guidance or exclusion lists. Describing the precise conditions that make a number "magic" gives Claude a clear decision rule rather than requiring inference. Option A is the kind of vague instruction that causes the problem in the first place. Option C introduces a severity layer that does not address the underlying definitional problem. Option B would require maintaining an incomplete and fragile list that does not generalize to new values.

---

## Scenario 6: Structured Data Extraction

You are building a structured data extraction system using Claude. The system extracts information from unstructured documents, validates output using JSON schemas, and maintains high accuracy. It must handle edge cases gracefully and integrate with downstream systems.

**Primary domains:** Domain 4, Domain 5

---

**Q104.** After calibration, extractions with confidence of 0.9 or higher skip human review. How do you make sure accuracy in this auto-approved stream does not silently degrade, including through novel error patterns?

A) Repeat the calibration exercise only when a downstream consumer reports a problem with the data.
B) Pass every auto-approved extraction through a second model and require agreement.
C) Raise the threshold to 0.99 so that any remaining errors become negligible.
D) Review a stratified random sample of high-confidence extractions on an ongoing basis.

**Correct Answer: D**
*Task 5.5: Design human review workflows and confidence calibration*

Stratified random sampling of high-confidence extractions measures the ongoing error rate and detects novel error patterns that confidence alone would miss. Option A waits for damage to be noticed downstream. Option C assumes calibration stays valid forever and floods reviewers. Option B doubles cost, and two models can share the same blind spots.

---

**Q105.** Extraction of methodology details from research papers works when a paper has a dedicated Methods section but returns empty fields when the details are embedded in the introduction or footnotes. The same instructions are used for all papers. What is the most effective improvement?

A) Make the methodology fields required in the schema so that the model has to fill them in.
B) Add few-shot examples showing correct extraction from papers with several different structures.
C) Instruct the model to read through each paper twice before it begins extracting any of the fields.
D) Send every paper that lacks a dedicated Methods section to a human for manual extraction.

**Correct Answer: B**
*Task 4.2: Apply few-shot prompting to improve output consistency and quality*

Few-shot examples demonstrating correct handling of varied document structures address empty extraction of fields the model fails to locate. Option A pressures the model to fill fields and encourages fabrication. Option C is a vague instruction that does not show where to look. Option D forgoes automation for a problem that examples can solve.

---

**Q106.** A 180-page contract is extracted in a single pass. Fields drawn from the first and last sections are accurate, but clauses in the middle of the document are often missed. Which restructuring is most appropriate?

A) Move the extraction instructions from the start of the prompt to the end of the prompt.
B) Run section-by-section extraction passes, then a consolidation pass that reconciles cross-references.
C) Repeat the single-pass extraction three times and take the majority value for each field.
D) Increase `max_tokens` so that the model has room to output a larger number of fields.

**Correct Answer: B**
*Task 1.6: Design task decomposition strategies for complex workflows*

Decomposing a large input into focused per-section passes followed by an integration pass gives every section full attention and still handles cross-section references. Option C repeats the same attention problem three times. Option A does not change how the middle of a long document is processed. Option D addresses output length, which is not the constraint.

---

**Q107.** An invoice extraction pipeline uses tool use with a strict JSON schema. After validation, 8% of extracted invoices fail a business rule check: the sum of line item amounts does not equal the `total_amount` field. These are semantic errors, not schema syntax errors. The invoices are well-formed documents with no missing data. How should you implement the retry loop?

A) On failure, append the original document, the failed extraction, and the specific validation error ("line items sum to X but total_amount is Y") to the follow-up prompt for model self-correction.
B) Flag all invoices with this error as missing data and route them directly to human review without retry.
C) Add a `calculated_total` field to the schema and populate it with the sum of line items in post-processing, then use the calculated total as the canonical value.
D) Retry up to 3 times with the same prompt; schema-compliant extraction will converge on a valid answer with additional attempts.

**Correct Answer: A**
*Task 4.4: Implement validation, retry, and feedback loops for extraction quality*

Retry-with-error-feedback works by giving the model the specific discrepancy it needs to self-correct. Since the invoices are well-formed and the data is present, the model has the information it needs to fix the arithmetic alignment on retry. Option D retries without feedback and is unlikely to improve results since the model will reproduce the same error. Option B routes to human review prematurely when a retry with feedback could resolve the issue. Option C silently replaces the model's extracted total with a calculated value, which could propagate errors if the line items themselves were extracted incorrectly.

---

**Q108.** A 10,000-document batch finishes with 400 failures. All 400 are documents that exceeded the context limit. What is the right recovery?

A) Resubmit the entire batch of 10,000 documents on a model that has a larger context window.
B) Exclude the 400 documents from the results and record them as unprocessable.
C) Identify the failures by `custom_id`, chunk those documents, and resubmit only them.
D) Resubmit only the 400 failed documents unchanged, since batch failures are usually transient.

**Correct Answer: C**
*Task 4.5: Design efficient batch processing strategies*

Batch failure handling means identifying failed requests by `custom_id` and resubmitting only those, with the modification that addresses the cause, here chunking oversized documents. Option A reprocesses 9,600 successful documents. Option D repeats a deterministic failure. Option B abandons recoverable work.

---

**Q109.** The pipeline's single `analyze_document` tool takes a free-text `instructions` string and is used for extracting data points, summarizing, and verifying claims. Its outputs vary in shape, and the agent often passes vague instructions. What redesign is best?

A) Keep the single tool and add few-shot examples of good `instructions` strings to the prompt.
B) Remove the tool and let the model perform all three of the tasks in free-form text.
C) Keep the single tool and validate the `instructions` string with a regex before execution.
D) Split it into purpose-specific tools, each with its own defined input and output contract.

**Correct Answer: D**
*Task 2.1: Design effective tool interfaces with clear descriptions and boundaries*

Splitting a generic tool into purpose-specific tools (for example `extract_data_points`, `summarize_content`, `verify_claim_against_source`) with defined contracts makes both selection and output predictable. Option A still depends on free-text instructions. Option C checks form, not intent. Option B gives up structured, validated output.

---

**Q110.** A structured data extraction system is extracting contract clauses from legal documents. The model handles standard clauses well but consistently misclassifies ambiguous clauses that could fit two or more categories, such as a clause that contains both termination conditions and force majeure language. What few-shot prompting approach is most effective for improving accuracy on these edge cases?

A) Add a confidence score field and route all low-confidence classifications to human review without attempting to improve the model's judgment.
B) Add more few-shot examples of standard, unambiguous clauses to reinforce the classification schema overall.
C) Add targeted examples of ambiguous clauses that show the reasoning for choosing one category over the other.
D) Switch from classification to extraction: ask Claude to extract the clause text without categorizing it, then apply a rule-based classifier.

**Correct Answer: C**
*Task 4.2: Apply few-shot prompting to improve output consistency and quality*

Targeted few-shot examples for ambiguous scenarios that show the reasoning behind the classification decision are the most effective technique for improving handling of edge cases. Standard examples do not teach the model how to handle cases that span category boundaries. Option B reinforces behavior that already works rather than addressing the gap. Option D sidesteps the classification problem rather than solving it. Option A is a reasonable operational safeguard but does not improve model accuracy.

---

**Q111.** Documents are classified with a `document_type` enum of `invoice`, `receipt`, and `purchase_order`. New types appear every month (credit notes, pro-forma invoices) and are forced into the closest wrong category. What is the best schema design?

A) Replace the enum with a free-text string field so that any document type at all can be expressed.
B) Add an `"other"` enum value paired with a detail string field that describes the actual type.
C) Keep the enum as it is and have humans re-check every `invoice` classification.
D) Add every document type that the team is able to anticipate to the enum in advance.

**Correct Answer: B**
*Task 4.3: Enforce structured output using tool use and JSON schemas*

An `"other"` value with a detail string keeps the known categories machine-consistent while giving unanticipated types an honest place to go. Option A loses consistency for the common categories. Option D can never be complete, so the forcing problem returns. Option C adds review cost and checks only one of the categories affected.

---

**Q112.** Your schema marks `tax_id` as a required string. For invoices that contain no tax ID, the model outputs plausible-looking but invented IDs. What schema change addresses this?

A) Keep the field required and add a prompt instruction telling the model never to invent tax IDs.
B) Remove the field from the schema and extract tax IDs with a separate regular-expression pass.
C) Keep the field required and add a regex pattern so that any value the model supplies is always well-formed.
D) Make the field nullable, so that the model can return null when the document does not contain the value.

**Correct Answer: D**
*Task 4.3: Enforce structured output using tool use and JSON schemas*

A required field forces the model to supply a value even when the source has none, which invites fabrication. Optional or nullable fields let it truthfully report absence. Option C makes the fabricated values better formed. Option A leaves the prompt in conflict with a schema that still demands a value. Option B abandons model extraction for a field it handles well when the data is present.

---

**Q113.** After you move extraction to tool use with a JSON schema, parse failures drop to zero. Which class of errors should you still expect and validate for?

A) Output that is truncated in the middle of a string value, even when the token limit has not been reached.
B) Semantic errors, such as values placed in the wrong field or line items that do not sum to the total.
C) Responses that come back as conversational prose in place of the structured tool input.
D) Malformed JSON output, such as unclosed brackets or trailing commas after the last element.

**Correct Answer: B**
*Task 4.3: Enforce structured output using tool use and JSON schemas*

Tool use with a JSON schema eliminates syntax errors but not semantic ones: a schema-valid object can still hold a value in the wrong field or totals that do not reconcile. Semantic validation remains necessary. Options A and D are syntax-level failures of the kind schema-enforced tool use removes. Option C is a tool selection issue addressed by `tool_choice`.

---

**Q114.** Your model outputs one confidence score per document. Reviewers find that low-scoring documents usually have a single problematic field, yet they have to re-check all thirty fields. What is the improvement?

A) Replace confidence routing with a full review of every tenth document processed.
B) Have the model output field-level confidence so that review attention goes to the uncertain fields.
C) Have reviewers check a random selection of five fields in each flagged document.
D) Lower the document-level threshold so that fewer documents are sent to the reviewers.

**Correct Answer: B**
*Task 5.5: Design human review workflows and confidence calibration*

Field-level confidence scores, calibrated against labeled validation sets, direct limited reviewer capacity to the specific fields that are uncertain. Option D lets more errors through unreviewed. Option C will usually miss the one problematic field. Option A discards the routing signal altogether.

---

**Q115.** A financial document extraction pipeline is failing on the "guarantor address" field for a set of loan summaries. After 3 retry attempts with error feedback, the field still extracts as null. Each retry prompt includes the original document and the validation error. What should you investigate before scheduling further retries?

A) Increase the retry limit from 3 to 5, since complex field extraction may require more attempts to converge.
B) Switch to a larger model tier for the retry attempts, since the current model may lack the reasoning capacity for this field.
C) Check whether the address actually appears in the document or is only referenced as living in an external exhibit.
D) Restructure the schema to make the guarantor address field optional, allowing the pipeline to proceed when the field cannot be extracted.

**Correct Answer: C**
*Task 4.4: Implement validation, retry, and feedback loops for extraction quality*

Retries are only effective when the information needed to satisfy the validation is present in the document. A loan summary that references guarantor details in an external exhibit does not contain the address. No number of retries will extract information that is not in the input. Before adding retry cycles, validate that the target field is actually present in the source document. Option A adds more retries without diagnosing why the existing retries are failing. Option B may improve performance on difficult extractions but does not address absence of data. Option D removes the validation rather than diagnosing the root cause.

---

**Q116.** Your extraction agent has `extract_metadata` plus three enrichment tools. Enrichment only works correctly once metadata exists, but the model sometimes starts with an enrichment tool. How do you guarantee the order?

A) Set `tool_choice` to `"any"` so that the model is required to begin with a tool call.
B) State in each enrichment tool's description that metadata should be extracted first.
C) List `extract_metadata` first in the tools array, since the model favors earlier tools.
D) Force `extract_metadata` with `tool_choice` on the first request, then enrich in follow-up turns.

**Correct Answer: D**
*Task 2.3: Distribute tools appropriately across agents and configure tool_choice*

Forced tool selection (`{"type": "tool", "name": "extract_metadata"}`) guarantees that the specific tool runs first; subsequent steps are then handled in follow-up turns. Option A guarantees a tool call but not which tool. Option C relies on an ordering preference that provides no guarantee. Option B is guidance the model can still ignore.

---

**Q117.** You want the extraction step itself to surface invoices whose line items do not add up, rather than discovering this downstream. Which schema design supports that?

A) A `confidence` field attached to `total`, which the model lowers whenever it is unsure of the extracted value.
B) Separate `stated_total` and `calculated_total` fields, so that a mismatch can be detected and flagged.
C) A single `total` field, with an instruction telling the model to double-check its arithmetic.
D) A `total` field constrained by a pattern so that values always have exactly two decimal places.

**Correct Answer: B**
*Task 4.4: Implement validation, retry, and feedback loops for extraction quality*

Extracting the document's stated total alongside a total calculated from the line items makes discrepancies explicit and machine-checkable. Option C leaves no trace of whether a discrepancy existed. Option A relies on poorly calibrated self-assessment. Option D constrains formatting, not correctness.

---

**Q118.** You have written a new extraction prompt and are about to submit 50,000 documents to the Batches API. What step most reduces the risk of costly re-submissions?

A) Add instructions to the prompt telling the model to retry any extraction it gets wrong.
B) Submit the full volume twice and keep whichever of the two result sets validates better afterward.
C) Divide the volume into fifty smaller batches so that any failures stay isolated.
D) Refine the prompt on a representative sample set first, and only then submit the full volume.

**Correct Answer: D**
*Task 4.5: Design efficient batch processing strategies*

Prompt refinement on a sample set before batch processing maximizes first-pass success and avoids paying to iterate at full volume. Option B doubles cost without improving the prompt. Option C isolates infrastructure failures but not prompt flaws, which would affect every batch equally. Option A cannot work, because the model has no validation feedback inside a single batch request.

---

**Q119.** An extraction pipeline achieves high accuracy on average but the team wants to implement confidence-based routing: high-confidence extractions proceed automatically while low-confidence ones go to human review. A developer proposes using the model's stated confidence scores directly as the routing threshold. What is the critical flaw in this approach?

A) Routing on confidence scores creates two separate code paths that are harder to maintain than a single uniform review workflow.
B) Confidence scores add tokens to every response, increasing API costs unnecessarily.
C) Confidence scores only work when the model outputs a single extraction; multi-field documents require a different approach.
D) Raw confidence scores are uncalibrated; thresholds must be validated against a labeled set before they are used for routing.

**Correct Answer: D**
*Task 5.5: Design human review workflows and confidence calibration*

A model's raw confidence scores need calibration: without comparing stated confidence against actual correctness on a labeled validation set, there is no reliable mapping between a score of "0.85" and an acceptable error rate. Calibrating the threshold ensures that the routing cut-off corresponds to a known accuracy level. Option B is a minor operational concern, not a critical flaw. Option C is incorrect; confidence scores can be applied at the field level for multi-field documents. Option A is an engineering tradeoff, not a flaw in the confidence approach itself.

---

**Q120.** Your extraction pipeline uses a prompt that requests JSON output with a code block. In production, approximately 3% of responses have JSON syntax errors: missing commas, unescaped characters, or truncated objects. These errors break your downstream parser and require manual reprocessing. What is the most reliable way to eliminate JSON syntax errors?

A) Switch to tool use with a defined JSON schema as the input parameter; extract structured data from the `tool_use` response block.
B) Add a validation step that re-runs the prompt if the output fails JSON parsing, up to 3 retries.
C) Add an instruction to the prompt: "Your response must be valid JSON. Double-check for syntax errors before responding."
D) Use a regex post-processor to fix the most common syntax errors before passing output to the parser.

**Correct Answer: A**
*Task 4.3: Enforce structured output using tool use and JSON schemas*

Tool use with a JSON schema guarantees schema-compliant structured output by construction, eliminating syntax errors entirely. The model populates the tool call's input parameters according to the schema rather than generating free-text JSON. Option B reduces the frequency of failures but does not eliminate syntax errors. Option C relies on model self-checking, which does not provide the deterministic guarantee that tool use provides. Option D is a fragile workaround that cannot handle all syntax error patterns.

---

**Q121.** Your structured data extraction pipeline processes invoices. You have two extraction tools: `extract_invoice_schema` and `extract_receipt_schema`. For each document, you do not know in advance which type it is. After switching to `tool_choice: "auto"`, you observe that 30% of the time the model returns a text description of what it found rather than calling either tool. What is the correct fix?

A) Set `tool_choice: {"type": "tool", "name": "extract_invoice_schema"}` to always call a specific tool.
B) Add a system prompt instruction: "Always call one of the extraction tools and never return text."
C) Set `tool_choice: "any"` to guarantee the model calls one of the available extraction tools without specifying which one.
D) Merge both schemas into a single `extract_document_schema` tool with an optional `document_type` field.

**Correct Answer: C**
*Task 4.3: Enforce structured output using tool use and JSON schemas*

`tool_choice: "any"` guarantees the model calls a tool rather than returning conversational text, without requiring you to specify which tool. This is exactly the documented use case when you have multiple valid tools and want to ensure one is called. Option A forces a specific tool, which defeats the purpose when you do not know the document type in advance. Option B is a prompt-based approach with probabilistic compliance, which already failed as evidenced by the 30% text response rate. Option D is a valid architectural change but requires more engineering effort than a single configuration change.

---

**Q122.** A compliance team runs a weekly audit that analyzes 50,000 contract documents for regulatory clauses. The audit results are reviewed by a compliance analyst every Monday morning. The team is considering the Message Batches API. A colleague raises a concern: "What if a batch fails partway through the 50,000 documents?" How should partial batch failures be handled?

A) Use `custom_id` to identify which requests failed and resubmit only those documents in a new batch.
B) Set a shorter processing window timeout to force faster completion and reduce the risk of partial failures.
C) Switch to real-time API calls with retry logic; the batch API is not suitable for mission-critical compliance workloads.
D) Always resubmit the entire batch; tracking partial failures adds implementation complexity.

**Correct Answer: A**
*Task 4.5: Design efficient batch processing strategies*

The `custom_id` field is specifically designed for correlating batch request and response pairs, enabling teams to identify which documents failed and resubmit only those, avoiding the cost of reprocessing the entire batch. Option D wastes 50% cost savings by reprocessing successful documents. Option B misunderstands the batch API; processing windows are managed by Anthropic and cannot be shortened on demand. Option C is overly conservative: the batch API is appropriate for non-blocking, latency-tolerant compliance audits, which this workflow is.

---

**Q123.** A structured data extraction system for insurance claims achieves 97% overall accuracy on a validation set. The team proposes automating the full workflow without human review. A colleague argues this aggregate metric masks important risks. What is the most important concern?

A) Human review should always be retained regardless of accuracy metrics because automation of insurance decisions creates regulatory risk.
B) Aggregate accuracy can hide weak performance on specific document types or fields; analyze accuracy by segment before automating.
C) 97% accuracy means 3% of claims will have errors, which could create legal liability if unchecked.
D) The validation set may not be representative of production data volumes, so the 97% figure cannot be trusted.

**Correct Answer: B**
*Task 5.5: Design human review workflows and confidence calibration*

The core risk is that aggregate metrics can hide poor performance on specific segments. A document type with 85% accuracy on a critical field like `claim_amount` would be masked by strong performance across other document types. Before automating, accuracy should be validated by document type and field segment to confirm consistent performance across all dimensions. Option C is a valid concern but describes the error rate, not the masking risk. Option D raises a data quality concern but is not the most important concern about the specific 97% figure. Option A makes a policy argument that does not engage with the analytical gap identified.

---

**Q124.** A document extraction system uses Claude to pull financial figures from quarterly earnings reports. The reports have varied formats: some use tables, some use inline prose, some use both. Extraction accuracy for tabular data is high (94%) but prose-only documents show only 72% accuracy. What is the most targeted approach to improve prose extraction accuracy?

A) Increase the system prompt's emphasis on accuracy with stronger language and more detailed instructions.
B) Pre-process all documents to convert prose financial data into table format before sending to Claude.
C) Add few-shot examples specifically showing correct extraction from prose-formatted documents, including cases where numbers appear in sentence form rather than tables.
D) Use a separate prompt for prose documents that instructs Claude to first identify all sentences containing numbers, and then extract figures from those sentences only.

**Correct Answer: C**
*Task 4.2: Apply few-shot prompting to improve output consistency and quality*

Few-shot examples demonstrating correct extraction from documents with varied formats directly address the accuracy gap on prose documents. The model already generalizes well to tabular data; the gap is in prose, and targeted examples for that format close the gap most efficiently. Option A relies on emphasis, which does not resolve structural pattern differences. Option B requires reliable pre-processing of arbitrarily structured prose, which is non-trivial. Option D adds complexity and may miss numbers that are discussed without appearing in sentences Claude isolates.

---

## Answer Key

| Q | Answer | | Q | Answer | | Q | Answer | | Q | Answer |
|---|--------|-|---|--------|-|---|--------|-|---|--------|
| 1 | B | | 32 | B | | 63 | D | | 94 | C |
| 2 | B | | 33 | C | | 64 | A | | 95 | A |
| 3 | A | | 34 | A | | 65 | C | | 96 | C |
| 4 | B | | 35 | B | | 66 | D | | 97 | B |
| 5 | B | | 36 | C | | 67 | C | | 98 | B |
| 6 | A | | 37 | D | | 68 | D | | 99 | D |
| 7 | A | | 38 | C | | 69 | B | | 100 | C |
| 8 | B | | 39 | D | | 70 | A | | 101 | B |
| 9 | B | | 40 | C | | 71 | D | | 102 | A |
| 10 | A | | 41 | C | | 72 | D | | 103 | D |
| 11 | B | | 42 | D | | 73 | A | | 104 | D |
| 12 | C | | 43 | C | | 74 | D | | 105 | B |
| 13 | A | | 44 | D | | 75 | A | | 106 | B |
| 14 | D | | 45 | B | | 76 | D | | 107 | A |
| 15 | D | | 46 | D | | 77 | A | | 108 | C |
| 16 | A | | 47 | C | | 78 | A | | 109 | D |
| 17 | D | | 48 | A | | 79 | B | | 110 | C |
| 18 | A | | 49 | C | | 80 | A | | 111 | B |
| 19 | D | | 50 | B | | 81 | D | | 112 | D |
| 20 | C | | 51 | A | | 82 | D | | 113 | B |
| 21 | D | | 52 | D | | 83 | C | | 114 | B |
| 22 | C | | 53 | B | | 84 | B | | 115 | C |
| 23 | D | | 54 | A | | 85 | A | | 116 | D |
| 24 | C | | 55 | C | | 86 | A | | 117 | B |
| 25 | A | | 56 | C | | 87 | C | | 118 | D |
| 26 | A | | 57 | A | | 88 | B | | 119 | D |
| 27 | B | | 58 | B | | 89 | B | | 120 | A |
| 28 | D | | 59 | A | | 90 | C | | 121 | C |
| 29 | B | | 60 | B | | 91 | C | | 122 | A |
| 30 | D | | 61 | C | | 92 | A | | 123 | B |
| 31 | A | | 62 | C | | 93 | C | | 124 | C |

---

*Unofficial practice exam based on the Claude Certified Architect – Foundations exam guide. 124 questions across 6 scenarios and 5 domains. Not an official Anthropic product.*

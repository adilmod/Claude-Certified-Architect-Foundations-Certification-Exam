# Claude Certified Architect – Foundations: Practice Exam

> Built by [Olivier Legris](https://www.alterhq.com), Claude Ambassador and co-founder of [Alter](https://www.alterhq.com) — a macOS native, model-agnostic Claude Cowork for advanced users.
>
> This was built using publicly available information and is not part of the Claude Ambassador program. Anthropic is not involved in any form with this project.

A community-built practice exam for the **Claude Certified Architect – Foundations** certification by Anthropic.

124 scenario-based questions across 6 scenarios and 5 domains, built from the official exam guide. Includes study notes and an interactive Claude Code skill that runs a 60-question exam simulation in your terminal.

---

## Exam Structure

| Domain | Topic | Exam Weight | Questions Here |
|--------|-------|-------------|----------------|
| 1 | Agentic Architecture & Orchestration | 27% | 31 |
| 2 | Tool Design & MCP Integration | 18% | 22 |
| 3 | Claude Code Configuration & Workflows | 20% | 24 |
| 4 | Prompt Engineering & Structured Output | 20% | 27 |
| 5 | Context Management & Reliability | 15% | 20 |

- **Format:** Multiple choice, 4 options (1 correct, 3 distractors)
- **Structure:** Scenario-based. A real sitting is reported to use 4 of the 6 scenarios, about 60 questions.
- **Scoring:** Scaled 100–1,000, pass at 720. The raw-to-scaled conversion is not published.
- **This bank:** 124 questions, 20–22 per scenario, all 30 task statements covered, every option explained.

---

## Files

| File | Description |
|------|-------------|
| `Claude Certification Exam.md` | 124-question practice exam, grouped by scenario, with explanations and answer key |
| `Study Notes.md` | Condensed review of each task statement and the decision patterns the exam rewards |
| `cert-exam.skill` | Claude Code skill for interactive exam sessions |

---

## How to Prepare

1. Read `Study Notes.md` once, start to finish.
2. Run an exam simulation with summary-only feedback. Treat it as the real thing: no notes, about 2 minutes per question.
3. For every miss, read why each of the four options is right or wrong, then re-read that task's section in the notes.
4. Drill your weakest domain, then run another simulation.
5. Aim for 85%+ on questions you have not seen before, with no domain under 75%. Scores on repeated questions measure memory, not readiness.

Practice questions cannot replace hands-on experience. The exam guide recommends building an agent with tool use and hooks, configuring Claude Code for a real project (CLAUDE.md, rules, skills, MCP), building a structured extraction pipeline, and building a multi-agent research pipeline.

---

## Run the Exam Interactively in Claude Code

`cert-exam.skill` is a Claude Code skill. From the root of this repository:

**1. Install the skill:**

```bash
mkdir -p .claude/skills/cert-exam
```

```bash
cp cert-exam.skill .claude/skills/cert-exam/SKILL.md
```

**2. Run it from Claude Code:**

```
/cert-exam          # choose a mode (60-question exam simulation recommended)
/cert-exam 20       # quick 20-question mixed drill
```

The skill reads `Claude Certification Exam.md` from the current directory, so start Claude Code in the repository root.

The skill will:
- Offer an exam simulation (4 random scenarios, 15 questions each), a quick drill, or a domain or scenario drill
- Present each question using Claude's interactive UI (options A/B/C/D)
- Give immediate feedback or a summary at the end (your choice)
- Report your raw score, a readiness band, and a domain-by-domain breakdown
- List every missed question with the task statement to review

---

## Design Notes

- Correct answers are evenly distributed (31 each for A, B, C, D), and option lengths are balanced so the longest option is not a tell.
- Questions are grouped by scenario and mixed across domains. The task statement appears only after the answer.
- Distractors are meant to be plausible: common anti-patterns, over-engineered fixes, and fixes for a different problem.
- Answers follow the official exam guide. Where the product has changed since the guide was written, the guide's terminology is used.
- Questions 1–12 of the original set come from the exam guide's sample questions; the rest are community-written and have not been validated against live exam items.

---

## What the Exam Covers

Questions are drawn from 6 realistic production scenarios:

1. **Customer Support Resolution Agent** — agentic loops, tool design, escalation
2. **Code Generation with Claude Code** — CLAUDE.md, plan mode, slash commands
3. **Multi-Agent Research System** — coordinator patterns, error propagation, context
4. **Developer Productivity with Claude** — built-in tools, MCP integration
5. **Claude Code for CI/CD** — non-interactive mode, structured output, batch processing
6. **Structured Data Extraction** — JSON schemas, validation loops, human review

---

## Source

Based on the official *Claude Certified Architect – Foundations Certification Exam Guide* (Anthropic, Feb 2025). The guide provides domain descriptions, task statements, sample questions, and preparation exercises. This repo extends it with 112 additional questions covering all 30 task statements.

---

## Disclaimer

This is an unofficial community resource. It is not affiliated with or endorsed by Anthropic. The certification exam itself is administered separately by Anthropic.

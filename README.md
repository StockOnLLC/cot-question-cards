# CoT (Chain of Thought) Question Cards

**Public Agent Skill** for aligning any plan or design — without mid-flight A/B votes.

**Macro cards → private multi-scheme fission → exactly one Optimized Solution → execute → post-execution regression (satisfied card only then).**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-SKILL.md-black.svg)](#installation)
[![Works with](https://img.shields.io/badge/Claude%20Code%20%7C%20Coco%20%7C%20Cursor%20%7C%20Codex%20%7C%20WorkBuddy%20%7C%20CodeBuddy%20%7C%20OpenCode%20%7C%20Gemini%20%7C%20Windsurf%20%7C%20Cline%20%7C%20CoTree-compatible-blue.svg)](#installation)
[![Related](https://img.shields.io/badge/vs-grill--me%20%7C%20AskUserQuestion%20%7C%20grilling-orange.svg)](#positioning-versus-grill-me-grilling-and-askuserquestion)
[![SEO](https://img.shields.io/badge/Agent%20Skill-plan%20alignment%20%7C%20Goal%20Contract-informational.svg)](#seo-and-discovery-keywords)

> **External product name (English):** **Question Cards** only.  
> **Never brand this product as Grill, grill-me, grilling, or grill-with-docs.** Those names belong to related prior art and search neighborhoods; this skill is a different loop with hard timing rules. Chinese product name is **闪电问** only in the appendix — never 「问题卡」.

**Repository:** [https://github.com/StockOnLLC/question-cards](https://github.com/StockOnLLC/question-cards)

**Skill bodies:**
- Core loop: [`skills/cot-question-cards/SKILL.md`](./skills/cot-question-cards/SKILL.md)
- Lightweight companion: [`skills/choice-cards/SKILL.md`](./skills/choice-cards/SKILL.md)

---

## Table of contents

1. [TL;DR](#tldr)
2. [Problem statement: why interview skills stall teams](#problem-statement-why-interview-skills-stall-teams)
3. [Positioning versus grill-me, grilling, and AskUserQuestion](#positioning-versus-grill-me-grilling-and-askuserquestion)
4. [Audience personas](#audience-personas)
5. [Hard timing rule (non-negotiable)](#hard-timing-rule-non-negotiable)
6. [Master Loop overview (Phases 0–4)](#master-loop-overview-phases-04)
7. [Phase 0 — First principles (private)](#phase-0--first-principles-private)
8. [Phase 1 — Macro Question Cards only](#phase-1--macro-question-cards-only)
9. [Goal Contract deep dive](#goal-contract-deep-dive)
10. [Phase 2 — Multi-scheme fission (Agent-private)](#phase-2--multi-scheme-fission-agent-private)
11. [Phase 3 — Execute the unique Optimized Solution + regression](#phase-3--execute-the-unique-optimized-solution--regression)
12. [Phase 4 — Micro tweak (default OFF)](#phase-4--micro-tweak-default-off)
13. [Card UX by host](#card-ux-by-host)
14. [Installation](#installation)
15. [Suite layout](#suite-layout)
16. [Worked example A — Product launch Goal Contract](#worked-example-a--product-launch-goal-contract)
17. [Worked example B — Agent Skill packaging and publish](#worked-example-b--agent-skill-packaging-and-publish)
18. [Worked example C — Spec sharpening for an API redesign](#worked-example-c--spec-sharpening-for-an-api-redesign)
19. [Worked example D — Migrating a noisy grill-me session](#worked-example-d--migrating-a-noisy-grill-me-session)
20. [Worked example E — Recursive planning after a failed regression](#worked-example-e--recursive-planning-after-a-failed-regression)
21. [Migration guide from grill-me / grilling](#migration-guide-from-grill-me--grilling)
22. [Anti-patterns catalog](#anti-patterns-catalog)
23. [End artifact template](#end-artifact-template)
24. [Relationship to Code Fission and design trees](#relationship-to-code-fission-and-design-trees)
25. [FAQ](#faq)
26. [Glossary](#glossary)
27. [Keyword index (SEO)](#keyword-index-seo)
28. [Contributing](#contributing)
29. [License](#license)
30. [Links](#links)
31. [Chinese appendix](#chinese-appendix--中文摘要)

---

## TL;DR

| You get | You do not get |
| --- | --- |
| Clear success criteria via **macro Question Cards** | Three to five half-baked options dumped for you to vote |
| Agent **internally** expands 2–5 schemes, gates them, keeps **one** champion | Mid-fission “which do you prefer?” preference polls |
| A **Goal Contract** written from your answers (no confirm-card spam) | “Are you happy?” before anything shipped |
| A **satisfied card only after execute** (regression loop) | Satisfaction glued to the first swipe deck of macro questions |
| Card UX compatible with `AskUserQuestion`, `AskQuestion`, `request_user_input`, and Grok Bot widgets | A product branded as Grill |

**One sentence:** CoT (Chain of Thought) Question Cards is an Agent Skill (`SKILL.md`) that keeps structured question widgets for plan alignment and design interview work, but forbids mid-loop scheme voting and forbids satisfied/not-satisfied cards until the unique Optimized Solution has been executed.

**Five beats:**

1. Phase 0 — First principles (private): surface ask vs bedrock assumptions vs inherited assumptions.
2. Phase 1 — Macro Question Cards only (2–3 load-bearing cards). No satisfied card. No “adopt Optimized Solution” card.
3. Agent writes the Goal Contract privately → Phase 2 multi-scheme fission (2–5 schemes) → gates → **exactly one** Optimized Solution.
4. **Execute** that Optimized Solution end-to-end.
5. Phase 3 regression — **only now** ask satisfied / not satisfied; recurse or rewrite the Goal Contract until confirmed.

---
## Problem statement: why interview skills stall teams

The Agent Skills ecosystem exploded around structured interviews. People search for **grill-me**, **grilling**, **grill-with-docs**, **AskUserQuestion**, **AskQuestion**, **request_user_input**, **choice cards**, **choice-cards**, **Socratic interview**, **plan alignment**, **design interview**, **spec sharpening**, and **product discovery**. Those searches are healthy. The failure mode is not “asking questions.” The failure mode is **when** and **what** gets asked.

### Failure mode 1 — Mid-fission preference votes

A typical grill-me or grilling session surfaces several partial schemes and asks the human to pick. That feels collaborative. In practice it:

- Forces the user to compare incomplete designs without gates
- Turns the Agent into a waiter instead of a decision engine
- Creates decision fatigue before any Optimized Solution exists
- Confuses **macro goal clarity** with **micro implementation taste**

Question Cards treats multi-scheme fission as **Agent-private**. The user never sees a shortlist of half-baked winners mid-loop. The Agent expands schemes, applies hard gates and guardrails, and returns **exactly one** Optimized Solution.

### Failure mode 2 — Satisfaction asked too early

Many card UIs make it easy to append “Are you satisfied?” to the first swipe group. That destroys the regression loop. Satisfaction before execution is theater: there is nothing concrete to be satisfied about. Question Cards hard-codes the opposite:

> Satisfied / not-satisfied cards **MUST NOT** appear with Phase 1 macro questions. Ask satisfied **only after** (1) the user answered Phase 1, (2) the Agent delivered the unique Optimized Solution **and executed it**, (3) the **regression** round.

### Failure mode 3 — Mixing macro and micro in one deck

Macro questions ask what success looks like, for whom, bedrock constraints, and the cost of being wrong. Micro questions ask which module, which API, which button color. Mixing them in one AskUserQuestion / AskQuestion / request_user_input deck creates false precision: the user “decides” implementation details before the Goal Contract exists. Question Cards forbids micro preference votes during Phase 1 and Phase 2.

### Failure mode 4 — Naming collision with Grill

Teams searching for grill-me, grilling, Builder.io grill-me, nicolasgalvez grilling, or “Grill the plan” often want structured cards. If your product also brands itself Grill, you inherit their timing habits and SEO confusion. **Question Cards** keeps the card UX neighborhood (AskUserQuestion family, choice cards, question widgets) while owning a distinct loop name and a distinct hard timing rule.

### Failure mode 5 — No execute step

Some interview skills stop at “shared understanding.” Shared understanding without shipping is unfinished work. Question Cards requires the Agent to **deliver and execute** the unique Optimized Solution before opening the regression satisfied card. Execution may mean: push a repo, publish a skill, update a config, write the PR, configure topics — whatever the Goal Contract defined as done.

### Failure mode 6 — Inherited assumptions smuggled into the goal

Teams inherit analogies (“we should do it like Slack”, “every Agent Skill needs a marketplace listing first”, “Claude Code AskUserQuestion is the only card UX”). Inherited assumptions are useful as hypotheses and dangerous as bedrock. Phase 0 of Question Cards separates **bedrock assumptions** (hard, proven, must hold) from **inherited assumptions** (habit, analogy, fashion). Inherited assumptions must not sneak into the Goal Contract without being surfaced in Phase 1.

### Why Agent Skills make this worse if timing is wrong

Modern hosts — Claude Code, Coco, Cursor, OpenAI Codex, WorkBuddy, CodeBuddy, OpenCode, Gemini CLI, Windsurf, Cline, Continue, Trae, Zed, Copilot, CoTree, Grok Bot, and more — make cards cheap. `AskUserQuestion`, `AskQuestion`, `request_user_input`, and in-chat widgets lower the friction of asking. Lower friction without timing discipline means more mid-loop votes. Question Cards is the timing discipline layer on top of those card primitives.

### What “high information density” means for this skill

A public Agent Skill README must teach:

- The Master Loop
- The hard timing rule
- How Goal Contract differs from a satisfaction poll
- How Optimized Solution differs from a shortlist
- How to install a `SKILL.md` into Claude Code, Cursor, Codex, Grok Bot, and OpenCode
- How this relates to grill-me, grilling, grill-with-docs, AskUserQuestion, choice-cards, agentskills.io, anthropics/skills, Terminal Skills, `npx skills add`, plugin marketplace, CLAUDE.md, and AGENTS.md

That is why this document is long on purpose. Search engines and humans installing Agent Skills need prose that connects **Question Cards** to every high-heat noun in the neighborhood — without claiming ownership of Builder.io grill-me, nicolasgalvez grilling, Matt Pocock-style skills ecosystems, Filip Hric interactive SKILL.md notes, or Anthropic’s anthropics/skills repository.

---
## Positioning versus grill-me, grilling, and AskUserQuestion

### Short comparison table

| Dimension | grill-me / grilling (typical) | AskUserQuestion / AskQuestion / request_user_input alone | choice-cards companion | Question Cards |
| --- | --- | --- | --- | --- |
| Interaction surface | Structured interview cards | Host question tool | Lightweight A/B/C | Same card family, macro-first |
| Mid-loop options | Often exposes multiple schemes | Whatever the prompt asks | One-off picks | **Forbidden** — fission is Agent-private |
| Output shape | Shared understanding / plan text | Answers to questions | A single pick | **Exactly one** Optimized Solution + **execute** |
| “Are you happy?” | Easy to ask early | Easy to ask early | Usually not used | **Only** post-execution regression |
| Naming | Grill / grill-me / grilling | Tool names | choice-cards | **Question Cards** only |
| Goal Contract | Optional / informal | None | None | Required, Agent-written after Phase 1 |
| Multi-scheme fission | Sometimes user-visible | N/A | N/A | Private 2–5 schemes → one champion |
| Recursive planning | Varies | N/A | N/A | Regression re-enters Phase 2 or Phase 1 |

### What we borrow (inspiration, not forks)

Question Cards sits in the same discovery neighborhood as:

- [Builder.io grill-me](https://www.skills.sh/builderio/builder-agent-skills/grill-me) — relentless plan interview patterns
- [nicolasgalvez grilling](https://www.skills.sh/nicolasgalvez/skills/grilling) and grill-with-docs style flows
- Anthropic [Agent Skills](https://github.com/anthropics/skills) and the broader `SKILL.md` convention
- [agentskills.io](https://agentskills.io) catalogs and Terminal Skills style install paths
- `npx skills add` marketplace installers and plugin marketplace listings
- Filip Hric’s notes on interactive `SKILL.md` plus AskUserQuestion
- Matt Pocock-style skills ecosystems (engineering skill packs, issue trackers, deep modules) — related ecosystem language; **not** owned by this repo
- Claude Code `AskUserQuestion`, Cursor `AskQuestion`, OpenAI Codex `request_user_input`, Grok Bot question widgets, OpenCode `question` / `ask_user`

We borrow: structured cards, Socratic pressure, first-principles decomposition, and the idea that plans deserve interrogation.

We reject: branding as Grill; mid-fission A/B votes; satisfied cards in the Phase 1 swipe group; stopping at “alignment” without an executed Optimized Solution.

### AskUserQuestion is a tool; Question Cards is a loop

`AskUserQuestion` (Claude Code), `AskQuestion` (Cursor), and `request_user_input` (Codex) are **primitives**. They do not encode when satisfaction is legal. Question Cards is a **Master Loop** that uses those primitives only in Phase 1 (macro), Phase 3 (regression), and optional Phase 4 (micro tweak). Phase 2 never opens a multi-scheme vote through those tools.

### choice-cards is a companion, not a replacement

The companion skill [`skills/choice-cards/SKILL.md`](./skills/choice-cards/SKILL.md) handles one-off A/B/C picks with no decision tree. If you need plan alignment, design interview, Goal Contract, multi-scheme fission, unique Optimized Solution, execute, and regression loop — use **Question Cards**, not choice-cards.

### Frontier questions and design trees

Some teams talk about “frontier questions” (the next load-bearing unknown) and “design trees” (branching decision graphs). Question Cards Phase 1 is frontier-question oriented: only ask the macro gaps that block a Goal Contract. The design tree is expanded **inside** Phase 2 by the Agent, not by carding every branch to the user. That is how recursive planning stays recursive without becoming a preference referendum.

---
## Audience personas

### Persona 1 — Founder / PM sharpening a Goal Contract

You need checkable success criteria before engineering burns a week. You have used grill-me or grilling before and liked the pressure, but you hated voting on three incomplete roadmaps. You want Question Cards to ask macro cards, write a Goal Contract, deliver one Optimized Solution, and actually ship the first slice before asking if you are satisfied.

### Persona 2 — Agent Skill author packaging for Claude Code / Cursor / Codex

You maintain `SKILL.md` files, care about agentskills.io discovery, `npx skills add`, plugin marketplace metadata, CLAUDE.md, and AGENTS.md. You want a public skill that SEO-connects to AskUserQuestion, choice cards, grill-me, and plan alignment — while teaching a stricter loop. You install Question Cards as a Claude Code skill, Cursor skill, Codex skill, or Grok Bot skill.

### Persona 3 — Staff engineer tired of mid-design polls

Your Agent keeps opening AskQuestion decks mid-refactor. You want the Agent to hold multi-scheme fission privately, gate schemes, and present one Optimized Solution with rollback notes. You will answer Phase 1 macro cards; you refuse to pick between Scheme B and Scheme D before gates run.

### Persona 4 — Bilingual product org (English docs, Chinese operators)

Your public README and skill discoverability are English-first for Agent Skills SEO. Operators may speak Chinese. User-facing cards follow the user’s language. This README’s main body is English; a concise Chinese appendix at the bottom summarizes hard timing and install under the Chinese product name used in that appendix.

### Persona 5 — Team migrating off grill-me / grilling

You already have muscle memory for Socratic interview skills. You want a migration path: keep card UX, drop Grill branding, adopt Goal Contract + unique Optimized Solution + execute-before-satisfied. See the [Migration guide](#migration-guide-from-grill-me--grilling).

### Persona 6 — OpenCode / multi-host agent runner

You run the same `SKILL.md` across OpenCode, Claude Code, Cursor, Codex, and Grok Bot. You need portable rules about when `question` / `ask_user` / AskUserQuestion / AskQuestion / request_user_input may appear. Question Cards is host-agnostic on timing even when card chrome differs.

---
## Hard timing rule (non-negotiable)

This rule is the product. Everything else is commentary.

### The rule

1. **Satisfied / not-satisfied cards MUST NOT appear with Phase 1 macro questions.**
2. Ask **satisfied only after** all of the following are true:
   - The user finished answering Phase 1 macro Question Cards (and any gap-driven follow-up macro cards).
   - The Agent wrote the Goal Contract privately (no confirm swipe required).
   - The Agent completed Phase 2 multi-scheme fission and selected **exactly one** Optimized Solution.
   - The Agent **delivered and executed** that Optimized Solution (ship / push / apply / publish — as defined by the Goal Contract).
   - The session is now in the **regression** round (Phase 3).
3. Do not phrase a Goal Contract lock as “adopt Optimized Solution.” Adopting happens at regression after execution evidence exists.
4. Do not bundle a Goal-Contract “confirm / start work” card in the same swipe deck as macro questions.
5. Mid-fission “which variant do you prefer?” is always illegal.

### Why the rule exists

Without this rule, Question Cards collapses into generic grilling with nicer labels. The satisfied card is powerful precisely because it is scarce. Scarcity forces the Agent to finish work before seeking approval theater.

### What “execute” means

Execution is whatever the Goal Contract’s success line makes checkable. Examples:

- GitHub public repo created, topics set, MIT LICENSE present, README pushed
- Claude Code skill copied into `~/.claude/skills/cot-question-cards` and invocable
- API redesign PR opened with the champion scheme’s modules
- Config flags flipped in production with rollback documented
- Marketplace / `npx skills add` metadata published if that was in scope

If nothing executed, you may not open the satisfied card. You may still show the Optimized Solution prose **without** a satisfaction widget — then execute — then regress.

### Regression outcomes (only legal after execute)

- **Satisfied — adopt / close** — freeze Goal Contract and Optimized Solution; close the loop
- **Not satisfied — recurse** — capture concrete feedback → Phase 2 again → new unique Optimized Solution → execute again → ask satisfied again
- **Macro gate wrong** — return to Phase 1; rewrite Goal Contract; do not pretend a micro re-fission will fix a wrong success criterion
- **Need expand** — user asks for more detail; explain, then re-enter the appropriate phase

### Two unsatisfied rounds that are actually macro

If feedback twice reveals the Goal Contract’s success line was wrong, force Phase 1. Do not spin Phase 2 forever on a broken bedrock.

---
## Master Loop overview (Phases 0–4)

```text
Phase 0  First principles (private)
         surface ask | bedrock assumptions | inherited assumptions
            |
            v
Phase 1  Macro Question Cards only (2–3 load-bearing)
         success / audience / bedrock / cost of being wrong
         NO satisfied card | NO adopt-Optimized-Solution card
            |
            v
         Agent writes Goal Contract privately (no confirm swipe)
            |
            v
Phase 2  Multi-scheme fission (Agent-private)
         seed → expand 2–5 schemes → hard gates → one champion
         NO mid-fission preference vote
            |
            v
         Deliver exactly one Optimized Solution
            |
            v
         EXECUTE the Optimized Solution end-to-end
            |
            v
Phase 3  Regression loop — satisfied card ONLY NOW
         adopt/close | re-fission | rewrite Goal Contract | expand
            |
            v
Phase 4  Micro tweak (default OFF)
         only if user explicitly asks inside the adopted solution
```

### Loop invariants

1. **Cards to the user** happen in Phase 1, Phase 3, and optional Phase 4 only.
2. **Phase 2 never cards schemes** for preference voting.
3. **Goal Contract** is written by the Agent after Phase 1 without a satisfaction or confirm card.
4. **Optimized Solution** is singular. Dual champions are a bug.
5. **Regression** requires execution evidence.
6. **Recursive planning** re-enters Phase 2 (or Phase 1 if macro was wrong) after concrete dissatisfaction feedback.
7. **choice-cards** may handle unrelated one-off picks outside this loop; they do not replace Question Cards for plan alignment.

### Mapping to host primitives

| Phase | Claude Code | Cursor | OpenAI Codex | Grok Bot | OpenCode |
| --- | --- | --- | --- | --- | --- |
| 0 | Private reasoning | Private reasoning | Private reasoning | Private reasoning | Private reasoning |
| 1 | `AskUserQuestion` | `AskQuestion` | `request_user_input` | Question widget / steps | `question` / `ask_user` |
| 2 | No user card | No user card | No user card | No user card | No user card |
| Deliver | Prose Optimized Solution | Prose | Prose | Prose | Prose |
| Execute | Tools / shell / git / APIs | Same | Same | Same | Same |
| 3 | `AskUserQuestion` satisfied | `AskQuestion` | `request_user_input` | Widget | `question` |
| 4 | Optional cards | Optional | Optional | Optional | Optional |

### Relationship to CLAUDE.md and AGENTS.md

Projects often keep standing instructions in `CLAUDE.md` or `AGENTS.md`. You may reference Question Cards there (“for plan alignment, load the Question Cards Agent Skill and obey hard timing”). Do not paste the entire Master Loop into every CLAUDE.md; load the `SKILL.md` instead so updates stay centralized in this repository’s [`skills/cot-question-cards/SKILL.md`](./skills/cot-question-cards/SKILL.md).

---

## Phase 0 — First principles (private)

Phase 0 is mandatory before any Question Card. It is usually private. Show a short conclusion only when it helps the user trust the framing.

### Steps

1. **One sentence surface ask** — What is the human literally asking right now?
2. **Bedrock assumptions** — What must be true, proven, or non-negotiable for any success definition?
3. **Inherited assumptions** — What habits, analogies, vendor defaults, or “everyone uses grill-me” fashion might be smuggled in?
4. **Separation** — Inherited assumptions must not enter the Goal Contract as if they were bedrock. Surface the risky ones in Phase 1 card copy when they could poison success criteria.

### First principles versus Socratic interview theater

A Socratic interview that only asks clever questions can still accept inherited assumptions. First principles work in Question Cards means: strip the ask to physics-like constraints (time, money, safety, compliance, single Optimized Solution requirement, execute-before-satisfied) before you design schemes.

### Examples of bedrock vs inherited

| Statement | Likely class | Why |
| --- | --- | --- |
| “We must not lose user data” | Bedrock | Safety / trust invariant |
| “Done means the public GitHub README is pushed” | Bedrock if stated | Checkable success |
| “We should brand this Grill because grill-me ranks” | Inherited | SEO fashion; naming collision |
| “Users must vote on three schemes” | Inherited | Opposite of this skill |
| “Claude Code AskUserQuestion is required on every host” | Inherited | Hosts differ; loop is portable |
| “Satisfied card belongs in the first swipe deck” | Inherited (harmful) | Violates hard timing |

### Anti-patterns in Phase 0

- Skipping Phase 0 and jumping to AskUserQuestion with implementation options
- Treating “similar to Builder.io grill-me” as a bedrock product requirement
- Hiding inherited assumptions so Phase 1 never challenges them
- Writing the Goal Contract before Phase 1 answers exist

---

## Phase 1 — Macro Question Cards only

Phase 1 is the **only** dense user-card phase before execution. Aim: make “what success is” crystal clear. No fission until clear.

### Ask only (gap-driven)

Ask a question only if the answer is still foggy:

- **Success look like** — checkable outcomes, not adjectives (“elegant”, “world-class”)
- **For whom / not for whom** — audience and explicit non-audience
- **Out of scope** — what we will not do even if tempting
- **Bedrock constraints** — hard limits, compliance, brand rules (including: external name is Question Cards, never Grill)
- **Cost of being wrong** — how tight gates must be in Phase 2

### Round structure

- Round 1: **2–3 load-bearing macro cards**
- Clear means: executable verification criteria and no blocking fog
- If fog remains: expand **1–3 cards on the foggy macro branch only**
- Do not widen into micro implementation

### Forbidden in Phase 1

- Any **satisfied / not satisfied / adopt Optimized Solution** card
- Bundling a Goal-Contract confirm / start-work card in the same swipe deck as macro questions
- Phrasing contract lock as “adopt Optimized Solution”
- Implementation details, module picks, API votes, UI micro-preferences
- Dumping grill-me style multi-scheme choices “just to get signal”

### Card copy guidance

- Detailed question text; short option labels
- Multi-question prefix: `①` `②` `③`
- Long, clear subtitles
- Usually 3 substance options + expand + host custom
- Do not put `A|` inside labels when the host already letters options
- Color marks when the host supports them: recommended first, risky marked, expand marked
- If the host has Something else / `allowCustom`, do not add a duplicate “I will write it myself” option
- User-facing cards follow the **user’s language**. This README’s English body stays English.

### Recommended option placement

When using choice UIs (AskUserQuestion, AskQuestion, request_user_input, Grok widgets), put the recommended macro option first and label it Recommended when the host supports descriptions. Recommendations are hypotheses, not pre-chosen Optimized Solutions. The Optimized Solution appears only after Phase 2.

### “You decide” / “whatever”

If the user declines to choose in Phase 1, take the current recommended option and proceed — still write the Goal Contract, still fission privately, still execute, still regress. Do not stall the Master Loop on politeness.

### Clarity exit criteria

Exit Phase 1 only when:

1. Success is checkable in one or two sentences
2. Scope and non-goals are explicit
3. Bedrock constraints are listed
4. Cost of being wrong informs gate tightness
5. No blocking fog remains on the macro goal

Then the Agent **privately** writes the Goal Contract and enters Phase 2 **with no user card**.

---
## Goal Contract deep dive

The Goal Contract is the acceptance object for Phase 2 gates and Phase 3 regression. It is not a satisfaction poll. It is not a mid-loop “confirm to start” swipe.

### When it is written

Immediately after Phase 1 answers are clear. Written by the Agent. **No user confirm card.** If regression later proves the macro wrong, return to Phase 1 and rewrite — that is the legal edit path.

### Template

```markdown
## Goal Contract
- Success: …
- Scope / non-goals: …
- Bedrock: …
- Gates: …
- Regression: ask satisfied only after the Optimized Solution is executed
```

### Field dictionary

**Success**  
Checkable. Prefer verbs and artifacts: “public repo StockOnLLC/question-cards exists with MIT LICENSE, English-first README, skills/cot-question-cards/SKILL.md, topics set.” Avoid “great SEO” without a proxy metric.

**Scope / non-goals**  
Name temptations you will refuse. Example non-goal: “Do not rebrand Question Cards as Grill for keyword capture.”

**Bedrock**  
Hard constraints: safety, legal, brand (English external name CoT (Chain of Thought) Question Cards; Chinese 闪电问), host compatibility targets (Claude Code, Coco, Cursor, Codex, WorkBuddy, CodeBuddy, OpenCode, Gemini CLI, Windsurf, Cline, CoTree, Grok Bot, and the full Installation matrix), license (MIT).

**Gates**  
What disqualifies a Phase 2 scheme automatically. Examples: “any scheme that asks the user to pick among 2–5 incomplete designs mid-fission is DQ”; “any scheme that places satisfied card in Phase 1 is DQ.”

**Regression**  
Always restate the hard timing rule so future Agents reading the artifact cannot “helpfully” ask satisfied early.

### Worked Goal Contract — publishing this skill

```markdown
## Goal Contract
- Success: https://github.com/StockOnLLC/question-cards is public; MIT LICENSE; README is English-first with Chinese appendix only; skills/cot-question-cards/SKILL.md and skills/choice-cards/SKILL.md present; topics include agent-skill, question-cards, askuserquestion, grill-me (as related search), goal-contract, optimized-solution.
- Scope / non-goals: No Grill product branding; no bilingual mash in the English README body; no mid-fission user votes in the skill rules.
- Bedrock: External English name is CoT (Chain of Thought) Question Cards (id cot-question-cards); Chinese 闪电问; satisfied only post-execute; unique Optimized Solution required.
- Gates: DQ any publish plan that ships a thin README; DQ any plan that asks satisfied in the same deck as macro cards.
- Regression: ask satisfied only after push and topics are live.
```

### Worked Goal Contract — API redesign

```markdown
## Goal Contract
- Success: New read path returns v2 envelope in staging; p95 latency under agreed budget; old clients continue on compatibility layer; rollback switch documented.
- Scope / non-goals: No UI redesign; no database vendor migration in this round.
- Bedrock: Zero silent data loss; compatibility layer required for one quarter.
- Gates: DQ schemes without rollback; DQ schemes that require a user preference vote on serializer bikesheds.
- Regression: ask satisfied only after staging execute checklist is green.
```

### Worked Goal Contract — product discovery workshop

```markdown
## Goal Contract
- Success: One Optimized Solution for the onboarding experiment is live for 10% traffic; primary metric event fires; kill switch tested.
- Scope / non-goals: No pricing page rewrite; no brand rename.
- Bedrock: Privacy review passed; metric must be checkable in existing analytics.
- Gates: DQ multi-scheme user votes; DQ “satisfied?” before traffic is live.
- Regression: post-execute satisfied card with adopt / re-fission / rewrite contract options.
```

### Anti-patterns

- Asking the user to “approve the Goal Contract” in the Phase 1 swipe group
- Writing Success as adjectives only
- Putting implementation preferences into Bedrock
- Omitting Regression timing (Agents will invent early satisfaction)
- Using Goal Contract as a synonym for Optimized Solution (they are different artifacts)

### Goal Contract versus Optimized Solution

| Artifact | Author | When | User card? | Purpose |
| --- | --- | --- | --- | --- |
| Goal Contract | Agent | After Phase 1 | No | Acceptance + gates |
| Optimized Solution | Agent | After Phase 2 | No (prose deliver) | Singular champion design |
| Execution record | Agent | During Phase 3 pre-regression | No | Proof of ship |
| Regression answer | User | Phase 3 | Yes | Adopt / recurse / rewrite |

---
## Phase 2 — Multi-scheme fission (Agent-private)

Phase 2 borrows the **select-one-champion skeleton** from Code Fission-style inner loops, applied at the plan layer. Full Code Fission release tournaments (dozens of variants with real fixtures) stay in Code Fission proper. Question Cards expands **2–5** executable schemes (default 3, max 5), gates them, and keeps **exactly one** Optimized Solution.

### 2.1 Seed

From the Goal Contract extract:

- **Primary metric / gates**
- **Guardrails** (brand rules, safety, “never call this Grill”, hard timing)
- **Seeds:** 1 default draft + up to 2 distinct directions (at most 3 seeds before expand)

### 2.2 Expand

Expand to 2–5 executable schemes. **Change one lever class per variant** so comparison is fair.

Each scheme must include:

| Field | Requirement |
| --- | --- |
| How | Modules, steps, data flow, hook-in points |
| Fail / rollback | Where it dies; how to restore |
| Fit | Which Goal Contract lines it satisfies |
| Risk | Inherited assumptions marked explicitly |
| Lever | Path / cut / integration / feedback loop / packaging / SEO surface / host adapter |

**Agent order:** write seed A → mutate one lever → B/C/(D/E) → fill the table → gate in 2.3. Self-research facts. BLOCKED variants stay out of ranking. If a user-only secret changes gates, return to **one Phase 1 macro card**, not a micro preference ask.

### 2.3 Gate and pick (Agent-only)

1. Hard gate fail → disqualify
2. Guardrail hit → disqualify or demote
3. Rank survivors: closer to Success, fewer inherited assumptions, more rollbackable, fewer new systems → pick **one champion**
4. Optional runner-up for one-line contrast in the deliverable — **never** present two winners for a user vote

**Output of Phase 2 is always a single Optimized Solution.** No dual champions. No “pick A or B.”

### 2.4 Forbidden

- Mid-fission “which variant do you prefer?” via AskUserQuestion, AskQuestion, request_user_input, or Grok widgets
- Dumping 2–5 half-baked schemes for multi-select
- Vibes without gates
- Renaming the champion “the Grill plan” for SEO
- Asking satisfied before execute because “the design looks good”

### Lever classes worth mutating (examples)

When aligning an Agent Skill publish plan, levers might include:

- README information density versus thin badge-only landing pages
- English-first with Chinese appendix versus bilingual mash (Question Cards chooses English-first + appendix)
- Marketplace path (`npx skills add`, plugin marketplace, agentskills.io listing) versus git-clone install only
- Companion choice-cards included versus core-only
- Topic set emphasizing AskUserQuestion / grill-me neighborhood versus pure brand terms

When aligning an API redesign, levers might include:

- Compatibility layer thickness
- Event-driven versus synchronous migration
- Staging-only execute versus canary percentage
- Serializer strategy
- Rollback switch placement

### Internal bake-off summary (not a user vote)

Keep an internal record:

```markdown
## Internal bake-off
- Variants: N
- Passed gates: M
- Winner: …
- DQ one-liners: …
```

Show a one-line contrast to the user only if it clarifies tradeoffs. Do not reopen a card deck for the bake-off.

### Recursive planning inside Phase 2

Recursive planning means the Agent may deepen a scheme’s how/fail/fit table when gates demand more detail — still without user cards. Recursion that needs new macro truth belongs in Phase 1, not in a fake micro vote.

---

## Phase 3 — Execute the unique Optimized Solution + regression

### Deliver (pre-execute, no satisfied card)

Present **one** Optimized Solution covering:

- How it works
- Why it passed gates
- Fail / rollback
- Key tradeoffs
- One line on directions that lost (optional)

Prose is allowed. **Satisfaction widgets are not allowed yet.**

### Execute

Do the work. Examples of execute evidence:

- `git push` completed; commit SHA recorded
- Host skill path populated; invocation smoke-checked
- Staging checklist green
- Traffic percentage live; kill switch tested
- Topics and LICENSE verified on GitHub

### Open regression (satisfied card only now)

Legal options:

- Satisfied — adopt / close
- Not satisfied — recurse (requires **specific** feedback) → Phase 2 → new unique Optimized Solution → execute again → ask satisfied again
- Macro gate wrong → Phase 1 rewrite Goal Contract
- Need expand → explain, then re-ask or re-enter phase

### Regression rules

- Satisfied card appears **only** post-execution — never with Phase 1, never before operate
- Dissatisfaction needs specific feedback before re-fission (no empty spin)
- Two unsatisfied rounds with feedback that is actually macro → force Phase 1
- Until the user confirms at regression, the loop continues
- “You decide” at regression means adopt / close

### Why execute-before-satisfied beats design-before-satisfied

Design approval without execution trains teams to confuse taste with reality. Question Cards forces contact with the real artifact: the pushed README, the live skill path, the staging API, the canary. That is product discovery with consequences, not Socratic theater.

---

## Phase 4 — Micro tweak (default OFF)

Phase 4 opens only if the user **explicitly** asks to choose one load-bearing detail **inside** the adopted Optimized Solution.

Rules:

- At most 3 cards per round
- Clear → stop
- No full design-tree reopen
- No satisfied card mixed into micro tweaks unless you are genuinely back in regression after another execute
- Prefer Agent judgment for non-load-bearing details

If the user asks for a pure one-off unrelated pick, you may route to **choice-cards** instead of opening Phase 4.

---
## Card UX by host

CoT (Chain of Thought) Question Cards is portable. The Master Loop is identical; only the chrome changes.

### Claude Code — AskUserQuestion

Claude Code exposes `AskUserQuestion` for structured options. Use it in Phase 1 and Phase 3. Do not use it in Phase 2 to present multi-scheme fission. Prefer 2–3 macro questions per round. Put recommended options first. Keep descriptions long enough to be decision-grade.

Installation pointer: copy `skills/cot-question-cards` into `~/.claude/skills/` or `.claude/skills/`. Invoke with `/cot-question-cards` or natural language “use CoT Question Cards for plan alignment.” Standing notes may live in `CLAUDE.md`, but the loop lives in `SKILL.md`.

### Cursor — AskQuestion

Cursor agents often expose `AskQuestion` or AskUserQuestion-compatible flows. Same timing rules. Project skills may live under `.cursor/skills` or the bot’s skill library. Cursor skill discovery should still name the skill **cot-question-cards** / **CoT (Chain of Thought) Question Cards**, not Grill. Prefer both `.cursor/skills` and `.agents/skills`. AGENTS.md may reference the skill for plan alignment and design interview tasks.

### OpenAI Codex — request_user_input

Codex interactive flows use `request_user_input` when enabled. If the tool is off, render the same macro options as a text card with clear marks. Never treat missing `request_user_input` as permission to dump mid-fission schemes. Codex skill path commonly `~/.codex/skills/cot-question-cards`.

### Grok Bot — widgets / steps / allowCustom

Grok Bot supports in-chat question widgets, multi-step swipe groups, `allowCustom`, and primary/danger styling. Phase 1 swipe groups contain **macro cards only**. Do not append a satisfied step to that group. Phase 3 opens a separate regression widget after execute evidence exists.

### OpenCode — question / ask_user

OpenCode-style runners often provide `question` or `ask_user`. Map Phase 1 and Phase 3 to those tools. Keep Phase 2 silent. OpenCode users installing from git should follow the same suite layout as other Agent Skills hosts.

### Text-card fallback (any host)

When no structured tool exists:

```text
① Success criteria (macro)
- Recommended: …
- Alternative: …
- Risky: …
- Expand: …
```

Still forbid mid-fission votes and early satisfied asks.

### choice-cards overlap

choice-cards uses the same host adapters for **one-off** picks. If a session is clearly Goal Contract / Optimized Solution work, load cot-question-cards (CoT Question Cards) instead. Linking between the two skills is intentional: choice-cards points up to CoT Question Cards for full alignment.

### WorkBuddy / CodeBuddy — Import Skill + widgets

WorkBuddy and CodeBuddy load skills from `.codebuddy/skills` / `~/.codebuddy/skills` or Settings → Import Skill. After importing `cot-question-cards`, use their question widgets for Phase 1 and Phase 3 only. Same hard timing.

### Windsurf / Cline / Continue / Trae / Zed / Copilot / Roo / Goose / Amp / Junie

These hosts either read `.agents/skills` (or a product-specific skills root) or fall back to custom instructions. See the numbered Installation subsections for exact project/global paths, invoke strings, and debug steps. Timing rules never change by host.

### CoTree / contree — router, not a separate loop

CoTree/`contree` installs this skill into Claude/Codex/OpenCode/Amp/Cline (and friends) skill directories. Invoke CoT Question Cards inside the destination host after `contree skill install` or manual `cp -R`.

### Filip Hric-style interactive SKILL.md notes

Interactive skill authoring discussions (including Filip Hric’s AskUserQuestion + SKILL.md notes in the broader ecosystem) emphasize that skills can drive structured UI. Question Cards agrees — and adds hard timing so interactivity does not become premature satisfaction polling.

---
## Installation

Compatible with the **Agent Skills** layout (`SKILL.md` + YAML frontmatter). This section is **operational**, not a handwave: for each host you get **project path**, **global path**, **how to write/invoke**, and **how to debug/tune**. Skill folder to copy: `skills/cot-question-cards` (and companion `skills/choice-cards`). Skill id / frontmatter `name`: **`cot-question-cards`** (kebab-case; folder name must match).

**English product name:** CoT (Chain of Thought) Question Cards  
**Chinese product name (appendix only):** 闪电问  
**Repo:** https://github.com/StockOnLLC/question-cards  
**Related search nouns (not product identity):** question cards, AskUserQuestion, AskQuestion, request_user_input, choice-cards, grill-me, grilling, plan alignment, Goal Contract, Optimized Solution, Agent Skills, SKILL.md, Terminal Skills, agentskills.io

### Universal clone

```bash
git clone https://github.com/StockOnLLC/question-cards.git
cd question-cards
# Core skill body:
#   skills/cot-question-cards/SKILL.md
# Companion single-pick helper:
#   skills/choice-cards/SKILL.md
```

### Universal multi-agent installer (vercel-labs / skills / agentskills.io)

When your catalog supports the vercel-labs `skills` CLI / Terminal Skills / agentskills.io style installers:

```bash
# Conceptual — exact flags follow your catalog version
npx skills add StockOnLLC/question-cards
# or point at the skill subfolder explicitly if the installer supports it:
# npx skills add StockOnLLC/question-cards/skills/cot-question-cards
```

What this does: copies `SKILL.md` (+ optional companions) into one or more agent skill roots your CLI knows about (Claude Code, Codex, Cursor, OpenCode, Amp, Cline, etc.). Always verify the destination folder name is **`cot-question-cards`** and frontmatter `name: cot-question-cards`.

Debug: if the skill does not appear, run the installer with verbose/list flags, confirm the destination path exists, restart the host, and check that description triggers include “CoT Question Cards”, “Chain of Thought Question Cards”, “plan alignment”, “Goal Contract”.

### Master compatibility matrix (quick index)

| Host | Project path | Global / user path | Invoke | Debug / tune |
| --- | --- | --- | --- | --- |
| Claude Code / Coco | `.claude/skills/cot-question-cards` | `~/.claude/skills/cot-question-cards` | `/cot-question-cards` or NL | CLAUDE.md pointer; restart session; check frontmatter |
| Cursor IDE + Cursor CLI | `.cursor/skills/` **and** `.agents/skills/` | `~/.cursor/skills/`, `~/.agents/skills/` (also loads `.claude/` / `.codex/`) | NL / agent skill picker; kebab name=folder | AGENTS.md; name must equal folder |
| OpenAI Codex | `.codex/skills/`, often `.agents/skills/` | `~/.codex/skills/` | NL + `request_user_input` | enable interactive input; restart Codex |
| WorkBuddy / CodeBuddy | `.codebuddy/skills/` | `~/.codebuddy/skills/` | Settings → Import Skill; NL | re-import; check YAML name |
| OpenCode | `.agents/skills/` or `.opencode/skills/` | `~/.config/opencode/skills/` | NL / `/cot-question-cards` | check opencode config skills root |
| Gemini CLI | `.agents/skills/` | `~/.gemini/skills/` | NL | restart CLI; list skills |
| Windsurf | `.windsurf/skills/` | `~/.codeium/windsurf/skills/` | NL / Cascade skills | Cascade reload |
| Cline | `.agents/skills/` or `.cline/skills/` | `~/.agents/skills/` or `~/.cline/skills/` | NL | VS Code reload window |
| Continue.dev | `.continue/skills/` | `~/.continue/skills/` | NL / config | continue config.json |
| Trae | `.trae/skills/` | `~/.trae/skills/` | NL | restart Trae |
| Zed | `.agents/skills/` | `~/.agents/skills/` | NL / agent | Zed agent settings |
| GitHub Copilot Chat | `.agents/skills/` | `~/.copilot/skills/` | agent/skills if supported; else custom instructions paste | Copilot Chat agents panel |
| Roo Code | `.roo/skills/` | `~/.roo/skills/` | NL | reload extension |
| Goose | `.goose/skills/` | `~/.config/goose/skills/` | NL / goose session | goose configure |
| Amp | `.agents/skills/` | `~/.config/agents/skills/` | NL | amp skills list |
| Junie (JetBrains) | `.junie/skills/` | `~/.junie/skills/` | NL | IDE restart |
| AiderDesk | `.aider-desk/skills/` | `~/.aider-desk/skills/` | NL | restart AiderDesk |
| Cortex / CoCo Snowflake | `.cortex/skills/` | `~/.snowflake/cortex/skills/` | NL | cortex skill list |
| Grok Build / Grok skill libs | `.grok/skills/` | `~/.grok/skills/` (+ bot libraries) | load skill name | bot skill library refresh |
| Kiro | `.kiro/skills/` | `~/.kiro/skills/` | NL | restart |
| Warp | `.agents/skills/` | `~/.agents/skills/` | Warp AI agent | Warp settings |
| Antigravity | `.agents/skills/` | `~/.gemini/antigravity/skills/` | NL | restart |
| CoTree / contree | targets other hosts’ dirs | via `contree skill install` specs | contree CLI | see CoTree section |
| VS Code + Copilot (no SKILL.md) | `.github/copilot-instructions.md` / prompts | user custom instructions | paste loop rules | instructions file |
| JetBrains AI Assistant | `.aiassistant/` / project docs | IDE AI settings | paste SKILL body / rules | AI Actions |
| Aider (classic) | `CONVENTIONS.md` / `.aider.conf.yml` | user conf | paste rules into conventions | aider conf |
| Web IDEs (Codespaces, Gitpod, …) | repo `.agents/skills/` or `.claude/skills/` | N/A ephemeral | clone + copy in terminal | re-copy after rebuild |
| OpenHands / Devin / Replit / Kilo / Hermes / Mistral Vibe / Crush / others | host-specific or `.agents/skills/` | see host docs | import SKILL.md | see per-host notes |

---

### 1. Claude Code / Coco

**Project path:** `.claude/skills/cot-question-cards/SKILL.md`  
**Global path:** `~/.claude/skills/cot-question-cards/SKILL.md`  
**Also used by:** Coco-branded Claude Code forks that still read `.claude/skills`.

**Install (user / global):**

```bash
mkdir -p ~/.claude/skills
cp -R skills/cot-question-cards ~/.claude/skills/cot-question-cards
cp -R skills/choice-cards ~/.claude/skills/choice-cards
```

**Install (project):**

```bash
mkdir -p .claude/skills
cp -R skills/cot-question-cards .claude/skills/cot-question-cards
cp -R skills/choice-cards .claude/skills/choice-cards
```

**How to write / invoke:**

- Slash: `/cot-question-cards`
- Natural language: “use CoT Question Cards to align this plan”, “run Chain of Thought Question Cards”, “Goal Contract with question cards timing”
- Description auto-load: frontmatter `description` should list plan alignment, Goal Contract, Optimized Solution, design interview, AskUserQuestion-style cards
- Optional `CLAUDE.md` pointer:

```markdown
For plan alignment / design interview / Goal Contract work, use the cot-question-cards skill
(CoT (Chain of Thought) Question Cards). Obey hard timing: satisfied only after execute.
```

**How to debug / tune:**

1. `ls ~/.claude/skills/cot-question-cards/SKILL.md` (or project path)
2. Confirm YAML `name: cot-question-cards` matches folder name
3. Start a new Claude Code session (skills often load at session start)
4. If `/cot-question-cards` missing, check skill discovery settings / plugins
5. Tune triggers by editing `description:` — add phrases your team actually says
6. Card UX: Phase 1/3 via `AskUserQuestion`; Phase 2 stays silent

---

### 2. Cursor IDE + Cursor CLI / Cursor agent

**Project paths:** `.cursor/skills/cot-question-cards/` **and** `.agents/skills/cot-question-cards/`  
**Global paths:** `~/.cursor/skills/cot-question-cards/`, `~/.agents/skills/cot-question-cards/`  
**Also loads:** project/user `.claude/skills` and `.codex/skills` on many Cursor builds — so a Claude/Codex install may already surface the skill inside Cursor.

**Critical Cursor rule:** frontmatter `name` **must** be kebab-case and **must** match the folder name (`cot-question-cards`).

**Install:**

```bash
# Prefer both Cursor-native roots for maximum discoverability
mkdir -p .cursor/skills .agents/skills
cp -R skills/cot-question-cards .cursor/skills/cot-question-cards
cp -R skills/choice-cards .cursor/skills/choice-cards
cp -R skills/cot-question-cards .agents/skills/cot-question-cards
cp -R skills/choice-cards .agents/skills/choice-cards

# User-global
mkdir -p ~/.cursor/skills ~/.agents/skills
cp -R skills/cot-question-cards ~/.cursor/skills/cot-question-cards
cp -R skills/choice-cards ~/.cursor/skills/choice-cards
cp -R skills/cot-question-cards ~/.agents/skills/cot-question-cards
cp -R skills/choice-cards ~/.agents/skills/choice-cards
```

**How to write / invoke:**

- Agent chat: “use CoT (Chain of Thought) Question Cards”, “align this with cot-question-cards”
- Cursor CLI / agent runners: same skill folder if the CLI loads `.agents/skills` or `.cursor/skills`
- Optional `AGENTS.md`:

```markdown
Plan / design alignment → skill cot-question-cards (CoT Question Cards).
Hard timing: no satisfied card until after execute.
Card primitive: AskQuestion for Phase 1 and Phase 3 regression only.
```

**How to debug / tune:**

1. Folder name === `name` field (kebab-case)
2. Reload Cursor window / restart Cursor CLI
3. If skill invisible, try the alternate root (`.agents/skills` vs `.cursor/skills`) or rely on `.claude/skills` mirror
4. Check agent rules / AGENTS.md are not overriding timing
5. Tune `description` for Cursor retrieval

---

### 3. OpenAI Codex

**Project paths:** `.codex/skills/cot-question-cards/`, often also `.agents/skills/cot-question-cards/`  
**Global path:** `~/.codex/skills/cot-question-cards/`

**Install:**

```bash
mkdir -p ~/.codex/skills .codex/skills .agents/skills
cp -R skills/cot-question-cards ~/.codex/skills/cot-question-cards
cp -R skills/choice-cards ~/.codex/skills/choice-cards
cp -R skills/cot-question-cards .codex/skills/cot-question-cards
cp -R skills/choice-cards .codex/skills/choice-cards
cp -R skills/cot-question-cards .agents/skills/cot-question-cards
```

**How to write / invoke:**

- Natural language skill load by description
- Interactive picks: enable / use `request_user_input` for Phase 1 and Phase 3; text-card fallback always valid
- Point from `AGENTS.md` if your Codex workflow uses it

**How to debug / tune:**

1. Confirm `~/.codex/skills/cot-question-cards/SKILL.md`
2. Restart Codex session
3. If cards don’t appear, check whether interactive `request_user_input` is enabled for the environment
4. Tune description triggers; keep Phase 2 silent even if the tool is available

---

### 4. WorkBuddy / CodeBuddy (Tencent)

**Project path:** `.codebuddy/skills/cot-question-cards/`  
**Global path:** `~/.codebuddy/skills/cot-question-cards/`  
**UI path:** Settings → **Import Skill** (select the `cot-question-cards` folder or its `SKILL.md`)

**Install (filesystem):**

```bash
mkdir -p ~/.codebuddy/skills .codebuddy/skills
cp -R skills/cot-question-cards ~/.codebuddy/skills/cot-question-cards
cp -R skills/choice-cards ~/.codebuddy/skills/choice-cards
cp -R skills/cot-question-cards .codebuddy/skills/cot-question-cards
cp -R skills/choice-cards .codebuddy/skills/choice-cards
```

**Install (UI):** WorkBuddy / CodeBuddy → Settings → Import Skill → choose `skills/cot-question-cards` → confirm name `cot-question-cards`.

**How to write / invoke:** After import, invoke by skill name or NL (“CoT Question Cards”, “Chain of Thought Question Cards”, “闪电问” if the host localizes). Prefer structured question widgets when WorkBuddy exposes them; otherwise text cards.

**How to debug / tune:** Re-import if YAML changes don’t apply; verify folder under `.codebuddy/skills`; restart WorkBuddy/CodeBuddy; check Import Skill error log if name invalid.

---

### 5. OpenCode

**Project paths:** `.agents/skills/cot-question-cards/` or `.opencode/skills/cot-question-cards/`  
**Global path:** `~/.config/opencode/skills/cot-question-cards/`

```bash
mkdir -p ~/.config/opencode/skills .opencode/skills .agents/skills
cp -R skills/cot-question-cards ~/.config/opencode/skills/cot-question-cards
cp -R skills/choice-cards ~/.config/opencode/skills/choice-cards
cp -R skills/cot-question-cards .opencode/skills/cot-question-cards
cp -R skills/cot-question-cards .agents/skills/cot-question-cards
```

**Invoke:** NL or `/cot-question-cards` if slash skills enabled; map Phase 1/3 to OpenCode `question` / `ask_user`.  
**Debug:** Confirm which skills root your OpenCode version reads (`opencode` config); restart; list installed skills.

---

### 6. Gemini CLI

**Project path:** `.agents/skills/cot-question-cards/`  
**Global path:** `~/.gemini/skills/cot-question-cards/`

```bash
mkdir -p ~/.gemini/skills .agents/skills
cp -R skills/cot-question-cards ~/.gemini/skills/cot-question-cards
cp -R skills/choice-cards ~/.gemini/skills/choice-cards
cp -R skills/cot-question-cards .agents/skills/cot-question-cards
```

**Invoke:** Gemini CLI natural language with skill description triggers.  
**Debug:** `ls ~/.gemini/skills`; restart CLI; if Antigravity overlay is in use, also check `~/.gemini/antigravity/skills/`.

---

### 7. Grok Bot / Grok skill libraries / Grok Build

**Project path:** `.grok/skills/cot-question-cards/`  
**Global / library paths:** `~/.grok/skills/cot-question-cards/`, plus Grok Bot personal/agent skill libraries (often under a managed skills root or bot store). Many Grok Bot setups also honor `~/.agents/skills/`.

```bash
mkdir -p ~/.grok/skills ~/.agents/skills .grok/skills
cp -R skills/cot-question-cards ~/.grok/skills/cot-question-cards
cp -R skills/choice-cards ~/.grok/skills/choice-cards
cp -R skills/cot-question-cards ~/.agents/skills/cot-question-cards
cp -R skills/cot-question-cards .grok/skills/cot-question-cards
```

**Invoke:** Load skill **cot-question-cards** / product name **CoT (Chain of Thought) Question Cards**. Use Grok Bot widgets / steps / `allowCustom` for Phase 1 and Phase 3 only.  
**Debug:** Refresh bot skill library; confirm description triggers; verify widgets don’t append satisfied into the macro swipe group.

---

### 8. Terminal Skills / npx skills add / agentskills.io catalogs

**Purpose:** Multi-host install from a catalog (vercel-labs/skills style, Terminal Skills, agentskills.io).

```bash
npx skills add StockOnLLC/question-cards
# After install, verify destinations contain:
#   .../cot-question-cards/SKILL.md
#   .../choice-cards/SKILL.md   # if companion selected
```

**Write / invoke:** Host-specific after the CLI drops files into Claude/Cursor/Codex/OpenCode/Amp/Cline roots.  
**Debug:** Run installer `--help` / list; confirm skill id `cot-question-cards`; re-run with force if partial copy; check agentskills.io listing metadata (name, description, keywords).

**Marketplace keywords to publish with:** Agent Skill, SKILL.md, CoT Question Cards, Chain of Thought Question Cards, question cards, AskUserQuestion, AskQuestion, request_user_input, choice-cards, Claude Code, Coco, Cursor, Codex, WorkBuddy, CodeBuddy, OpenCode, Gemini CLI, Windsurf, Cline, Continue, Trae, Zed, Copilot, Roo, Goose, Amp, Junie, AiderDesk, Cortex, Grok, Kiro, Warp, Antigravity, CoTree, contree, plan alignment, Goal Contract, Optimized Solution, grill-me (related), grilling (related).

---

### 9. Anthropic skills marketplace / plugin patterns

Follow anthropics/skills / Claude Code plugin marketplace conventions:

- Package the folder `skills/cot-question-cards` with valid frontmatter
- Register skill id `cot-question-cards`
- Install via marketplace UI or CLI into `~/.claude/skills/` or project `.claude/skills/`
- Do **not** claim this is an Anthropic product; etiquette: related ecosystem, separate MIT skill

**Debug:** Marketplace “installed skills” list; reinstall if SKILL.md hash stale; check plugin enablement.

---

### 10. VS Code + GitHub Copilot Chat

**When SKILL.md is supported (newer Copilot agents / skills):**

- Project: `.agents/skills/cot-question-cards/`
- Global: `~/.copilot/skills/cot-question-cards/`

```bash
mkdir -p .agents/skills ~/.copilot/skills
cp -R skills/cot-question-cards .agents/skills/cot-question-cards
cp -R skills/cot-question-cards ~/.copilot/skills/cot-question-cards
```

**When SKILL.md is NOT loaded (classic Copilot Chat):**

1. Paste the hard timing + Master Loop summary into `.github/copilot-instructions.md` or repo custom instructions
2. Or create a Copilot **prompt/agent** that embeds the CoT Question Cards rules
3. Use Copilot Chat slash prompts for Phase 1 macro questions manually; forbid mid-scheme votes in the instructions text

**Debug:** Copilot Chat agents panel → confirm skill/agent visible; if not, fall back to instructions file; Reload Window.

---

### 11. Windsurf

**Project:** `.windsurf/skills/cot-question-cards/`  
**Global:** `~/.codeium/windsurf/skills/cot-question-cards/`

```bash
mkdir -p .windsurf/skills ~/.codeium/windsurf/skills
cp -R skills/cot-question-cards .windsurf/skills/cot-question-cards
cp -R skills/choice-cards .windsurf/skills/choice-cards
cp -R skills/cot-question-cards ~/.codeium/windsurf/skills/cot-question-cards
```

**Invoke:** Cascade / Windsurf agent NL with skill triggers.  
**Debug:** Cascade reload; confirm skills directory in Windsurf settings; check Codeium account skill sync if cloud-synced.

---

### 12. Cline (VS Code extension)

**Project:** `.agents/skills/cot-question-cards/` or `.cline/skills/cot-question-cards/`  
**Global:** `~/.agents/skills/` or `~/.cline/skills/`

```bash
mkdir -p .cline/skills .agents/skills ~/.cline/skills ~/.agents/skills
cp -R skills/cot-question-cards .cline/skills/cot-question-cards
cp -R skills/cot-question-cards .agents/skills/cot-question-cards
cp -R skills/cot-question-cards ~/.cline/skills/cot-question-cards
```

**Invoke:** Cline chat NL.  
**Debug:** VS Code “Developer: Reload Window”; confirm Cline skills path setting; watch Cline output channel for skill load errors.

---

### 13. Continue.dev

**Project:** `.continue/skills/cot-question-cards/`  
**Global:** `~/.continue/skills/cot-question-cards/`

```bash
mkdir -p .continue/skills ~/.continue/skills
cp -R skills/cot-question-cards .continue/skills/cot-question-cards
cp -R skills/cot-question-cards ~/.continue/skills/cot-question-cards
```

**Invoke:** Continue chat / agent with skill description. If your Continue version uses `config.json` / `config.yaml` assistants instead of SKILL.md, paste Master Loop rules into the assistant prompt and keep `SKILL.md` in-repo for hosts that do support it.  
**Debug:** Continue output log; restart IDE; validate config schema.

---

### 14. Aider (classic) and AiderDesk

**AiderDesk (skills-aware):**

- Project: `.aider-desk/skills/cot-question-cards/`
- Global: `~/.aider-desk/skills/cot-question-cards/`

```bash
mkdir -p .aider-desk/skills ~/.aider-desk/skills
cp -R skills/cot-question-cards .aider-desk/skills/cot-question-cards
cp -R skills/cot-question-cards ~/.aider-desk/skills/cot-question-cards
```

**Classic Aider (no SKILL.md loader):**

1. Copy key rules into `CONVENTIONS.md` or a file listed in `.aider.conf.yml` (`read:`)
2. Or `--message` / system prompt prepend summarizing hard timing
3. Keep `skills/cot-question-cards/SKILL.md` in the repo for other tools sharing the tree

**Debug:** `aider` conf path; AiderDesk skill list; ensure conventions aren’t truncated.

---

### 15. Trae

**Project:** `.trae/skills/cot-question-cards/`  
**Global:** `~/.trae/skills/cot-question-cards/`

```bash
mkdir -p .trae/skills ~/.trae/skills
cp -R skills/cot-question-cards .trae/skills/cot-question-cards
cp -R skills/cot-question-cards ~/.trae/skills/cot-question-cards
```

**Invoke / debug:** NL after restart; confirm Trae skills setting points at `.trae/skills`.

---

### 16. JetBrains AI Assistant / Junie / JetBrains IDEs

**Junie (skills-aware JetBrains agent):**

- Project: `.junie/skills/cot-question-cards/`
- Global: `~/.junie/skills/cot-question-cards/`

```bash
mkdir -p .junie/skills ~/.junie/skills
cp -R skills/cot-question-cards .junie/skills/cot-question-cards
cp -R skills/cot-question-cards ~/.junie/skills/cot-question-cards
```

**Classic JetBrains AI Assistant (limited/no SKILL.md):**

1. Add project AI rules / `.aiassistant` notes summarizing CoT Question Cards hard timing
2. Or paste SKILL body into a custom AI Action / prompt snippet
3. Prefer Junie path when available

**Debug:** Restart IDE; Junie skills toolwindow; invalidate caches if skill stale.

---

### 17. Zed

**Project:** `.agents/skills/cot-question-cards/`  
**Global:** `~/.agents/skills/cot-question-cards/`

```bash
mkdir -p .agents/skills ~/.agents/skills
cp -R skills/cot-question-cards .agents/skills/cot-question-cards
cp -R skills/cot-question-cards ~/.agents/skills/cot-question-cards
```

**Invoke:** Zed agent panel NL.  
**Debug:** Zed agent settings → skills roots; restart Zed.

---

### 18. CoTree / contree (ly-jq/CoTree ecosystem)

**What CoTree is here:** the CoTree / `contree` collaborator tooling (see ly-jq/CoTree) that installs skills **into other agents’ directories** via specs such as `claude:~`, `codex:~`, `opencode:~`, `amp:~`, `cline:~`. CoTree does not replace those hosts; it **routes** `SKILL.md` into them.

**Verified pattern:** `contree skill install` with host specs that map onto:

| contree spec (illustrative) | Typical destination |
| --- | --- |
| `claude:~` | `~/.claude/skills/<id>` |
| `codex:~` | `~/.codex/skills/<id>` |
| `opencode:~` | `~/.config/opencode/skills/<id>` |
| `amp:~` | `~/.config/agents/skills/<id>` |
| `cline:~` | `~/.cline/skills/<id>` or `~/.agents/skills/<id>` |

**For THIS skill (`cot-question-cards`) — recommended:**

1. **Manual drop-in (always works):** copy `skills/cot-question-cards` into every target directory your contree specs would use (Claude, Codex, OpenCode, Amp, Cline, Cursor `.agents/skills`, WorkBuddy `.codebuddy/skills`, etc.).
2. **Optional contree wrap:** if your CoTree checkout exposes `contree skill install`, point it at this repo’s `skills/cot-question-cards` and pass the host specs you need, e.g. conceptually:

```bash
# Conceptual — follow your contree version’s help
contree skill install ./skills/cot-question-cards --to claude:~ --to codex:~ --to opencode:~ --to amp:~ --to cline:~
# Then verify:
ls ~/.claude/skills/cot-question-cards/SKILL.md
ls ~/.codex/skills/cot-question-cards/SKILL.md
```

3. **If contree skill path is unavailable in your build:** treat CoTree as an orchestrator docs/rules layer — keep `SKILL.md` in-repo, document targets in project agent rules, and manually `cp -R` into the same dirs contree would use. **Native CoTree-only skills directory is not assumed;** wire through the host dirs above.

**How to write / invoke after CoTree install:** Invoke inside the **destination** host (Claude Code `/cot-question-cards`, Codex NL, Cline NL, …). CoTree itself is the installer/router.

**How to debug / tune:**

1. `contree skill install --help` (or your CoTree README) for exact flags
2. List each destination `ls` after install
3. Confirm kebab folder `cot-question-cards`
4. If a spec is unknown, fall back to manual copy into that host’s row in the master matrix
5. Keep companion `choice-cards` copied the same way when you want the thin A/B/C helper

---

### 19. Web IDEs without durable local skills (Codespaces, Gitpod, StackBlitz-like, cloud VS Code)

**Reality:** ephemeral VMs often wipe home directories; prefer **project-committed** skill folders.

```bash
# Inside the cloud workspace terminal
git clone https://github.com/StockOnLLC/question-cards.git /tmp/question-cards
mkdir -p .claude/skills .agents/skills .cursor/skills .codex/skills
cp -R /tmp/question-cards/skills/cot-question-cards .claude/skills/
cp -R /tmp/question-cards/skills/cot-question-cards .agents/skills/
cp -R /tmp/question-cards/skills/cot-question-cards .cursor/skills/
cp -R /tmp/question-cards/skills/choice-cards .agents/skills/
# Commit these into YOUR product repo if the cloud workspace is your project
```

**Paste/import procedures when no skills directory exists:**

1. Open `skills/cot-question-cards/SKILL.md` on GitHub raw
2. Paste into the Web IDE’s custom instructions / system prompt / agent starter
3. Or import via the host’s “Upload skill / Import prompt” UI if present
4. After Codespace rebuild, re-run the copy commands or rely on committed `.agents/skills/`

**Debug:** Confirm files survived rebuild; pin skill folders in the project repo; don’t rely only on `~/.claude` in ephemeral clouds.

---

### 20. Additional Agent Skills clients (vercel / agentskills.io showcase neighborhood)

Install the same folder into each client’s documented root (project first, then global). Skill id remains `cot-question-cards`.

#### Roo Code

```bash
mkdir -p .roo/skills ~/.roo/skills
cp -R skills/cot-question-cards .roo/skills/cot-question-cards
cp -R skills/cot-question-cards ~/.roo/skills/cot-question-cards
```

Invoke via Roo NL; debug by reloading the Roo Code extension.

#### Goose

```bash
mkdir -p .goose/skills ~/.config/goose/skills
cp -R skills/cot-question-cards .goose/skills/cot-question-cards
cp -R skills/cot-question-cards ~/.config/goose/skills/cot-question-cards
```

Invoke in a goose session; `goose configure` / skills list to debug.

#### Amp

```bash
mkdir -p .agents/skills ~/.config/agents/skills
cp -R skills/cot-question-cards .agents/skills/cot-question-cards
cp -R skills/cot-question-cards ~/.config/agents/skills/cot-question-cards
```

#### Cortex / CoCo Snowflake

```bash
mkdir -p .cortex/skills ~/.snowflake/cortex/skills
cp -R skills/cot-question-cards .cortex/skills/cot-question-cards
cp -R skills/cot-question-cards ~/.snowflake/cortex/skills/cot-question-cards
```

#### Kiro

```bash
mkdir -p .kiro/skills ~/.kiro/skills
cp -R skills/cot-question-cards .kiro/skills/cot-question-cards
cp -R skills/cot-question-cards ~/.kiro/skills/cot-question-cards
```

#### Warp

```bash
mkdir -p .agents/skills ~/.agents/skills
cp -R skills/cot-question-cards .agents/skills/cot-question-cards
cp -R skills/cot-question-cards ~/.agents/skills/cot-question-cards
```

Use Warp AI agent settings to confirm skills roots.

#### Antigravity

```bash
mkdir -p .agents/skills ~/.gemini/antigravity/skills
cp -R skills/cot-question-cards .agents/skills/cot-question-cards
cp -R skills/cot-question-cards ~/.gemini/antigravity/skills/cot-question-cards
```

#### OpenHands, Devin, Replit Agent, Kilo, Hermes, Mistral Vibe, Crush, and similar

These hosts vary week to week. Operational rule:

1. Prefer `.agents/skills/cot-question-cards/` inside the project (most portable)
2. If the product documents a dedicated skills root, copy there too
3. If only “custom instructions” / “knowledge” / “bot brain” exists, paste the SKILL.md body (or hard-timing excerpt) and keep the git skill folder for real Agent Skills clients
4. Debug by checking the host’s agent/skills settings page and re-uploading after edits

SEO / discovery: keep mentioning OpenHands, Devin, Replit Agent, Kilo, Hermes, Mistral Vibe, Crush, Amp, Goose, Roo Code, Warp, Kiro, Antigravity, Cortex, Junie, AiderDesk alongside Claude Code, Coco, Cursor, Codex, WorkBuddy, CodeBuddy, OpenCode, Gemini CLI, Windsurf, Cline, Continue, Trae, Zed, Copilot, CoTree, contree, Grok Bot — so installers searching any of those nouns can land on this README.

---

### Frontmatter / write contract (all hosts)

Every install must keep:

```yaml
---
name: cot-question-cards
description: >-
  CoT (Chain of Thought) Question Cards / 闪电问. Use when aligning a plan or
  design: Phase 1 macro cards only (no satisfaction); Agent multi-scheme fission
  privately; deliver and execute exactly one Optimized Solution; ask satisfied
  only in the post-execute regression loop. ...
---
```

Rules:

- `name` kebab-case = folder name = `cot-question-cards`
- Description carries English product name + Chinese 闪电问 + high-heat triggers (AskUserQuestion, plan alignment, Goal Contract, …)
- Never set product name to Grill / grill-me / grilling

---

### anthropics/skills and ecosystem etiquette

[anthropics/skills](https://github.com/anthropics/skills) popularized Agent Skills patterns. CoT (Chain of Thought) Question Cards follows `SKILL.md` conventions and is **not** an Anthropic product. Same courtesy for Builder.io grill-me, nicolasgalvez grilling, Matt Pocock-style skill packs, Terminal Skills, agentskills.io, vercel-labs/skills, WorkBuddy/CodeBuddy Import Skill, CoTree/contree routers, and marketplace listings: related search neighborhood, separate MIT skill.

---

### Verify install (any host)

1. `SKILL.md` exists at the host path with folder `cot-question-cards`
2. Frontmatter `name: cot-question-cards`
3. Invoke CoT Question Cards on a toy plan
4. Phase 1 cards appear **without** a satisfied option
5. Agent writes Goal Contract **without** a confirm swipe
6. Phase 2 does **not** open a multi-scheme vote
7. Satisfied appears **only after** a real execute step
8. Companion optional: `choice-cards` present if you use thin A/B/C picks

### Smoke commands

```bash
test -f skills/cot-question-cards/SKILL.md && echo "repo ok"
test -f ~/.claude/skills/cot-question-cards/SKILL.md && echo "claude ok" || echo "claude missing"
test -f ~/.codex/skills/cot-question-cards/SKILL.md && echo "codex ok" || echo "codex missing"
test -f ~/.cursor/skills/cot-question-cards/SKILL.md -o -f ~/.agents/skills/cot-question-cards/SKILL.md && echo "cursor/agents ok" || echo "cursor/agents missing"
test -f ~/.codebuddy/skills/cot-question-cards/SKILL.md && echo "codebuddy ok" || echo "codebuddy missing"
```

---
## Suite layout

```text
question-cards/
├── LICENSE                      # MIT
├── README.md                    # English-first docs + SEO + Chinese appendix (闪电问)
└── skills/
    ├── cot-question-cards/
    │   └── SKILL.md             # CoT (Chain of Thought) Question Cards — Master Loop
    ├── choice-cards/
    │   └── SKILL.md             # thin A/B/C helper; points back for full alignment
    └── question-cards/          # compatibility alias folder (same body as cot-question-cards)
        └── SKILL.md
```

| Skill folder | Skill name (frontmatter) | When to use |
| --- | --- | --- |
| `skills/cot-question-cards` | `cot-question-cards` | CoT (Chain of Thought) Question Cards — plan / design / goal alignment; one Optimized Solution + execute |
| `skills/choice-cards` | `choice-cards` | Single lightweight pick only; points back to CoT Question Cards for full loops |
| `skills/cot-question-cards` | `cot-question-cards` | Compatibility alias of the core skill (prefer `cot-question-cards` on install) |

### Frontmatter expectations

Each `SKILL.md` begins with YAML frontmatter (`name`, `description`). Hosts use description text for retrieval. Include triggers such as: CoT Question Cards, Chain of Thought Question Cards, question cards, plan alignment, Goal Contract, Optimized Solution, design interview, first principles, regression loop, AskUserQuestion-style cards — and explicitly avoid instructing hosts to brand the skill as Grill.

### Topics / GitHub discovery

Suggested repository topics:

`agent-skill` · `agent-skills` · `cot-question-cards` · `question-cards` · `chain-of-thought` · `skill-md` · `claude-code` · `coco` · `cursor` · `codex` · `openai-codex` · `workbuddy` · `codebuddy` · `opencode` · `gemini-cli` · `windsurf` · `cline` · `continue-dev` · `trae` · `zed` · `github-copilot` · `roo-code` · `goose` · `amp` · `junie` · `aider` · `cotree` · `contree` · `grok-bot` · `kiro` · `warp` · `antigravity` · `askuserquestion` · `askquestion` · `request-user-input` · `choice-cards` · `grill-me` · `grilling` · `plan-alignment` · `goal-contract` · `optimized-solution` · `first-principles` · `product-discovery` · `spec-sharpening` · `decision-alignment` · `agentskills` · `terminal-skills`

Using `grill-me` / `grilling` as topics means **related search**, not product identity.

---

## Worked example A — Product launch Goal Contract

### Context

A founder wants to launch a waitlist landing page in one week. They previously ran grill-me and ended with four incomplete positioning options and an early “does this feel right?” card.

### Phase 0 (private)

- Surface ask: ship a waitlist page that converts early adopters
- Bedrock: one primary CTA; privacy policy link; analytics event on submit
- Inherited: “must A/B three headlines with the founder mid-design”; “brand it like a Grill session for energy”

### Phase 1 macro Question Cards (illustrative)

① What does success look like on launch day?  
- Recommended: 100 emails, CTA click tracked, page LCP under budget  
- Alternative: press mention only  
- Risky: “feels premium” with no metric  

② Who is this for / not for?  
- Recommended: technical founders already using Agent Skills  
- Alternative: general consumers  
- Risky: everyone  

③ What is explicitly out of scope this week?  
- Recommended: no billing, no SSO, no blog engine  
- Alternative: include blog  
- Risky: rebuild design system  

No satisfied card. No adopt Optimized Solution card.

### Goal Contract (Agent-written, no confirm swipe)

Success: waitlist live; event fires; LCP budget held; 100 emails or kill-criteria documented.  
Non-goals: billing, SSO, design-system rewrite.  
Bedrock: privacy link; single CTA.  
Gates: DQ schemes that require mid-fission headline voting; DQ early satisfied.  
Regression: post-execute only.

### Phase 2 fission (private)

Schemes might mutate levers: static site vs CMS, email vendor, social proof placement. Agent gates on speed and rollback. Champion: static page + one email vendor + one social proof block.

### Execute

Ship page, verify event, verify LCP, record URLs.

### Phase 3 regression

Now open satisfied / not satisfied. If not satisfied with concrete feedback (“social proof below fold kills conversion”), re-fission Phase 2, execute again, ask again.

---

## Worked example B — Agent Skill packaging and publish

### Context

A team wants a public Agent Skill for plan alignment that ranks near AskUserQuestion, grill-me, and choice cards searches. They almost named it Grill. Question Cards forbids that brand.

### Phase 1 focus

Success must be checkable on GitHub and install paths: MIT LICENSE, English-first README with Chinese appendix only, `skills/cot-question-cards/SKILL.md`, companion choice-cards, topics set, hard timing documented.

### Optimized Solution shape

- Public repo StockOnLLC/question-cards
- Dense README (this document’s strategy)
- SKILL.md Master Loop
- Install sections for Claude Code, Cursor, Codex, Grok Bot, OpenCode
- SEO glossary linking Question Cards to Agent Skills, SKILL.md, AskUserQuestion, AskQuestion, request_user_input, grill-me (related), grilling (related), Goal Contract, Optimized Solution, first principles, recursive planning, regression loop, agentskills.io, npx skills add, plugin marketplace, CLAUDE.md, AGENTS.md, anthropics/skills, Terminal Skills, Matt Pocock-style ecosystems (related), Builder.io grill-me (related), nicolasgalvez grilling (related), Filip Hric interactive SKILL.md notes (related)

### Execute evidence

Push, topics, smoke clone install into `~/.claude/skills/cot-question-cards`.

### Regression

Satisfied only after execute. If README is still too thin, that feedback is legitimate Phase 2 re-fission material (information density lever), not a Phase 1 satisfied mishap.

---

## Worked example C — Spec sharpening for an API redesign

### Context

Staff engineers argue in chat. Someone pastes three serializer designs and asks the PM to vote via AskQuestion. That is an anti-pattern under Question Cards.

### Corrective loop

Phase 1 asks only: success metric, compatibility requirements, rollback definition, cost of being wrong.  
Goal Contract forbids user votes on serializers.  
Phase 2 Agent expands schemes privately (compatibility thickness lever, canary lever, event-driven lever).  
Champion includes rollback.  
Execute in staging.  
Regression satisfied card with adopt / re-fission / rewrite contract.

### Spec sharpening outcome

The end artifact includes Goal Contract, Optimized Solution, internal bake-off summary, execution record, and regression result — sharper than a grill-with-docs transcript that never shipped.

---

## Worked example D — Migrating a noisy grill-me session

### Before

- Named the ritual Grill
- Used AskUserQuestion to show four roadmaps
- Asked “happy?” in the same swipe deck
- Stopped at shared understanding

### After (Question Cards)

1. Rename ritual to Question Cards in prompts and CLAUDE.md / AGENTS.md
2. Keep AskUserQuestion for macro only
3. Delete satisfied from Phase 1 templates
4. Require Goal Contract auto-write
5. Require unique Optimized Solution
6. Require execute checklist before regression
7. Keep choice-cards for unrelated one-offs

### Prompt rewrite examples

Bad: “Grill me on this plan and show me options A/B/C/D.”  
Good: “Use Question Cards. Macro cards only first. Then one Optimized Solution and execute. Satisfied only after ship.”

Bad: “AskUserQuestion: which scheme do you prefer?” mid-design.  
Good: Agent-private fission; user sees one champion after gates.

---

## Worked example E — Recursive planning after a failed regression

### Story

Phase 1 seemed clear: “publish the skill.” Optimized Solution executed: repo live. Regression: not satisfied — “README too thin; need ~10x content; English-first; Chinese only at the end; weave Agent Skill SEO nouns.”

### Correct branch

Feedback is specific → Phase 2 re-fission on the documentation lever → new unique Optimized Solution (long English README + Chinese appendix) → execute (overwrite README, push) → ask satisfied again.

### Incorrect branch

Asking another satisfied card without rewriting the README. Or jumping to Phase 1 satisfaction language. Or opening choice-cards to vote on heading synonyms mid-fission.

### Recursive planning moral

Recursion is allowed and expected. Empty recursion without feedback is not. Macro-wrong feedback must climb to Phase 1, not thrash Phase 2.

---
## Migration guide from grill-me / grilling

### Step 1 — Inventory

List prompts, CLAUDE.md snippets, AGENTS.md rules, and host skills that say grill-me, grilling, grill-with-docs, or Grill.

### Step 2 — Replace names

External product name becomes **Question Cards**. Related searches may still mention grill-me as prior art. Do not dual-brand.

### Step 3 — Split templates

Create a Phase 1 macro template without satisfied options. Create a Phase 3 regression template used only post-execute.

### Step 4 — Ban mid-fission votes

Search your skills for “which option”, “pick a scheme”, “A/B/C roadmap” inside plan-alignment flows. Route those moments into Agent-private fission.

### Step 5 — Add Goal Contract + Optimized Solution artifacts

If your grill-me sessions ended as chat prose, add the end artifact sections from this README.

### Step 6 — Add execute checklist

Define done. Wire regression to that checklist.

### Step 7 — Install Question Cards SKILL.md

Copy from this repo. Keep Builder.io grill-me / nicolasgalvez grilling installed if you still want them for other rituals — but do not run both loops on the same decision.

### Step 8 — Teach the team the hard timing rule

One sentence drill: “No happy card until it shipped.”

### Compatibility with AskUserQuestion muscle memory

You do not need to abandon AskUserQuestion, AskQuestion, or request_user_input. You need to stop misusing them for Phase 2. Question Cards is compatible with the same card muscles and stricter timing.

---

## Anti-patterns catalog

1. **Satisfied in Phase 1 swipe group** — hard timing violation  
2. **Adopt Optimized Solution card before execute** — naming and timing violation  
3. **Goal Contract confirm swipe with macros** — confirm spam  
4. **Mid-fission AskUserQuestion bake-off** — preference referendum  
5. **Branding as Grill** — SEO and product collision  
6. **Thin README for a public Agent Skill** — discovery failure  
7. **Bilingual mash in every heading** — harms English SEO clarity; use English body + Chinese appendix  
8. **Adjectival success criteria** — ungatable  
9. **Inherited assumptions marked as bedrock** — poisoned Goal Contract  
10. **Dual champions** — not an Optimized Solution  
11. **Empty re-fission without feedback** — recursion theater  
12. **Using choice-cards for full design trees** — wrong skill  
13. **Stopping at alignment without execute** — unfinished Master Loop  
14. **Host-specific loop forks** — Claude Code vs Cursor timing should not diverge  
15. **Marketplace keyword stuffing without teaching the loop** — users bounce  
16. **Asking micro API votes in Phase 1** — false precision  
17. **Hiding rollback** — ungated schemes  
18. **Pretending agentskills.io listing replaces SKILL.md quality** — catalog entry ≠ loop discipline  
19. **Paste entire README into CLAUDE.md** — drift magnet; load the skill  
20. **Satisfied card as politeness after every message** — destroys scarcity  

---

## End artifact template

```markdown
## Goal Contract
- Success: …
- Scope / non-goals: …
- Bedrock: …
- Gates: …
- Regression: ask satisfied only after the Optimized Solution is executed

## Optimized Solution (singular)
- How: …
- Why it passed gates: …
- Fail / rollback: …
- Tradeoffs: …
- Directions that lost (one line): …

## Internal bake-off
- Variants: N
- Passed gates: M
- Winner: …
- DQ one-liners: …

## Execution record
- What shipped: …
- Evidence (URLs, SHAs, checklists): …

## Regression
- Result: Satisfied close | Feedback → round k fission | Macro rewrite | Expand
- User confirm (post-execute only): Adopt/close | Re-fission | Rewrite contract
```

---

## Relationship to Code Fission and design trees

| Code Fission idea | Question Cards usage |
| --- | --- |
| Outer feature acceptance | Phase 1 Goal Contract (Agent-written, no mid confirm card) |
| Inner tournament | Phase 2 fission + gates → one Optimized Solution |
| Hard gates / guardrails | From contract + brand/safety rules; Agent judges |
| Freeze → ship | Phase 3 execute first, then regression confirm |
| Re-open round | Post-execute unsatisfied → feedback → Phase 2 again |
| Don’t ask non-workers | No micro preference votes mid-fission |

Design trees remain useful mentally. Question Cards expands branches inside Phase 2. Frontier questions belong in Phase 1 when they block the Goal Contract. This keeps recursive planning powerful without turning every branch into an AskQuestion referendum.

---
## FAQ

### Is Question Cards just grill-me with a new name?

No. grill-me / grilling / grill-with-docs are related prior art in the Socratic interview and plan alignment neighborhood. Question Cards keeps structured cards but changes the Master Loop: Goal Contract without confirm spam, Agent-private multi-scheme fission, unique Optimized Solution, mandatory execute, satisfied only at regression. External branding is Question Cards, never Grill.

### Can I still use AskUserQuestion?

Yes. AskUserQuestion (Claude Code), AskQuestion (Cursor), and request_user_input (Codex) are the preferred Phase 1 and Phase 3 primitives. They are not permission to run Phase 2 preference votes.

### Does this work as a Cursor skill and a Claude Code skill?

Yes. The same `SKILL.md` layout is intended for Claude Code skill paths, Cursor skill paths, OpenAI Codex skills, Grok Bot skills, and OpenCode skills. Install details differ by directory; timing rules do not.

### What about OpenAI Codex without request_user_input?

Use text cards with the same macro options and marks. The Agent Skills loop does not depend on one tool vendor.

### How does choice-cards relate?

choice-cards is a lightweight companion for one-off A/B/C picks. For decision trees, Goal Contract work, design interview, product discovery, or spec sharpening that needs an Optimized Solution, use Question Cards.

### Why mention Matt Pocock-style skills ecosystems?

Because many engineers discover Agent Skills through that broader teaching and tooling neighborhood (deep modules, issue trackers, skill packs). Question Cards is related by ecosystem adjacency for SEO and onboarding mental models. This repo does not claim ownership of that ecosystem.

### Why mention Builder.io grill-me and nicolasgalvez grilling?

Discovery. Teams searching those names often want structured plan interviews. We acknowledge them as related prior art and explain differences so users can choose deliberately.

### Why mention Filip Hric interactive SKILL.md notes?

Because interactive SKILL.md + AskUserQuestion patterns are part of how practitioners think about card-driven skills. Question Cards participates in that conversation with harder timing.

### Why mention anthropics/skills, agentskills.io, Terminal Skills, npx skills add, and plugin marketplace?

Those are how Agent Skills are published, listed, and installed. A public skill README that ignores them fails SEO and fails operator onboarding.

### Why mention CLAUDE.md and AGENTS.md?

Teams store standing orders there. They should reference Question Cards, not fork the entire loop into a second source of truth.

### Can the Agent show me multiple schemes if I insist?

You can ask. The skill still says Phase 2 is Agent-private for preference voting. If you need transparency, ask for the internal bake-off summary (variants count, DQ reasons, winner). That is an explanation, not a vote deck.

### What if I am satisfied with the design before execute?

You may like the prose. You still do not get a satisfied card until execute evidence exists. You may tell the Agent to execute immediately.

### What if execution is blocked on a secret only I know?

Return to a Phase 1 macro card about the gate-changing secret. Do not convert that into a micro scheme vote.

### Is first principles mandatory theater?

Phase 0 is mandatory thinking. Showing it can be brief. Skipping the bedrock vs inherited split is how Goal Contracts get poisoned.

### How many Phase 1 cards?

Usually 2–3 load-bearing cards per round. Expand only on foggy macro branches.

### How many Phase 2 schemes?

2–5, default 3, max 5. Exactly one Optimized Solution after gates.

### What is the regression loop?

The post-execute satisfied / not-satisfied cycle that may re-enter Phase 2 or Phase 1 until confirmed.

### What is recursive planning here?

Re-entering fission (or macro alignment) with feedback after reality, not endless pre-ship hypothesizing.

### What is decision alignment vs product discovery vs spec sharpening?

All three are valid triggers for Question Cards. Decision alignment emphasizes choose-and-ship. Product discovery emphasizes checkable learning. Spec sharpening emphasizes acceptance criteria quality. The Master Loop is the same.

### Can I use this for non-software plans?

Yes. Any plan or design with checkable success can use Question Cards: ops runbooks, launch checklists, research protocols, skill packaging, org process changes.

### Does Grok Bot require special widgets?

Use whatever question widgets / steps / allowCustom features exist. Timing rules are identical.

### Is bilingual documentation required inside SKILL.md?

This public README is English-first with a Chinese appendix. The skill body in-repo may evolve; user-facing cards follow the user’s language. Do not mash languages inside English headings in this README.

### What license?

MIT. See [LICENSE](LICENSE).

### Where is the source of truth for the loop?

[`skills/cot-question-cards/SKILL.md`](./skills/cot-question-cards/SKILL.md)

### Can satisfied cards appear with Phase 1 if labeled carefully?

No. Hard timing is unconditional.

### What if my marketplace requires the word Grill in the title?

Do not comply by renaming the product. Use topics and body SEO to appear in related searches while keeping the external name Question Cards.

### How do I invoke it verbally?

Examples:

```text
Use Question Cards to align this launch plan.
Run Question Cards with hard timing — satisfied only after ship.
Replace grill-me for this design review; keep AskUserQuestion-style cards but no mid-vote.
Load the Question Cards Agent Skill and produce one Optimized Solution, then execute.
```

### What goes in the Chinese appendix?

A concise summary of hard timing, install pointers, and the five-step flow under the Chinese product name documented there — not a full second translation of this entire English document.

---
## Glossary

**Agent Skill**  
A reusable instruction pack, usually a folder with `SKILL.md` and YAML frontmatter, loaded by agent hosts.

**Agent Skills**  
The ecosystem / convention spanning Claude Code, Cursor, Codex, Grok Bot, OpenCode, anthropics/skills-style repos, agentskills.io catalogs, Terminal Skills, marketplace installers, and related tooling.

**SKILL.md**  
The markdown file that defines a skill’s name, description, and body instructions.

**Question Cards**  
**CoT (Chain of Thought) Question Cards** — this product’s English external name (skill id `cot-question-cards`). Structured macro-first plan alignment skill with hard timing. Chinese appendix: 闪电问.

**question cards**  
Lowercase phrase used in SEO and casual reference to the same product / pattern.

**Claude Code skill**  
An Agent Skill installed for Claude Code (often under `~/.claude/skills` or `.claude/skills`).

**Cursor skill**  
An Agent Skill installed for Cursor agents / bot libraries.

**Codex skill / OpenAI Codex**  
An Agent Skill installed for OpenAI Codex (often under `~/.codex/skills`), commonly paired with `request_user_input` when interactive.

**Grok Bot**  
An agent host that can load skills and render question widgets / steps.

**OpenCode**  
An agent runner / host that may expose `question` or `ask_user` style tools and load SKILL.md packs.

**AskUserQuestion**  
Claude Code structured question tool; Phase 1 / Phase 3 primitive for Question Cards.

**AskQuestion**  
Cursor-oriented structured question tool / compatible pattern.

**request_user_input**  
OpenAI Codex interactive input primitive.

**choice cards / choice-cards**  
Lightweight A/B/C companion skill for one-off picks; not a full Goal Contract loop.

**grill-me**  
Popular plan interview skill name (e.g., Builder.io grill-me). Related prior art; not this product’s name.

**grilling**  
Related Socratic interview skill pattern (e.g., nicolasgalvez grilling).

**grill-with-docs**  
Related variant that emphasizes document artifacts during grilling.

**Grill**  
Umbrella nickname people use for the above. Forbidden as branding for Question Cards.

**Socratic interview**  
Question-driven interrogation of a plan; Question Cards uses this pressure in Phase 1 with different later timing.

**plan alignment**  
Making success criteria and constraints shared and checkable before build.

**design interview**  
Structured questioning of a design; Phase 1 macro focus in this skill.

**first principles**  
Phase 0 decomposition into surface ask, bedrock assumptions, inherited assumptions.

**bedrock assumptions**  
Hard, proven, non-negotiable constraints.

**inherited assumptions**  
Habits, analogies, fashion; must not silently enter the Goal Contract.

**Goal Contract**  
Agent-written acceptance object after Phase 1; includes Success, Scope, Bedrock, Gates, Regression timing.

**Optimized Solution**  
The singular champion scheme after Phase 2 gates.

**unique Optimized Solution**  
Emphasis that dual winners are invalid.

**multi-scheme fission**  
Private expansion of 2–5 schemes from seeds by mutating levers.

**recursive planning**  
Re-entering planning/fission with feedback, especially after regression.

**regression loop**  
Post-execute satisfied cycle until adopt/close or macro rewrite.

**decision alignment**  
Using the loop to force a shippable decision.

**product discovery**  
Using execute + regression to learn from reality.

**spec sharpening**  
Improving acceptance criteria quality via Phase 1 and Goal Contract.

**frontier questions**  
The next load-bearing unknowns; Phase 1 asks these when they block the contract.

**design tree**  
Branching decision graph; expanded privately in Phase 2.

**question widgets**  
Host UI for structured options (Grok Bot and others).

**option cards**  
Card-shaped choices; shared UX neighborhood with AskUserQuestion family.

**structured questions**  
Machine-renderable questions with options, not freeform only.

**agentskills.io**  
Public catalog / education site in the Agent Skills neighborhood.

**Terminal Skills**  
Catalog / distribution style in the skills ecosystem.

**npx skills add**  
Common marketplace installer invocation pattern.

**plugin marketplace**  
Host-specific skill/plugin distribution surface.

**anthropics/skills**  
Reference GitHub organization/repo popularizing Agent Skills patterns.

**CLAUDE.md**  
Project standing instructions for Claude Code-oriented agents.

**AGENTS.md**  
Project standing instructions for multi-agent / Cursor-style setups.

**Code Fission**  
Related select-one-champion tournament spirit borrowed at plan layer (2–5 schemes), not full release tournaments.

**Master Loop**  
Phases 0–3 (and optional 4) as defined by this skill.

**hard timing rule**  
Satisfied only after Phase 1 answers + unique Optimized Solution delivered and executed + regression round.

**execute**  
Performing the champion end-to-end until Goal Contract success is checkable.

**bake-off**  
Internal gating/ranking of schemes; not a user vote.

**load-bearing card**  
A Phase 1 question whose answer blocks or unblocks the Goal Contract.

**non-goals**  
Explicit out-of-scope items in the Goal Contract.

**guardrails**  
Brand/safety/policy constraints applied during gating.

**lever**  
The single dimension mutated between Phase 2 scheme variants.

**runner-up**  
Optional one-line contrast loser; never a second champion for voting.

**Phase 0 / 1 / 2 / 3 / 4**  
First principles; macro cards; fission; execute+regression; optional micro tweak.

**Matt Pocock-style skills ecosystem**  
Related engineering-skills teaching/tooling neighborhood; adjacency only.

**Builder.io grill-me**  
Specific well-known grill-me skill listing; related prior art.

**nicolasgalvez grilling**  
Specific grilling skill listing; related prior art.

**Filip Hric interactive SKILL.md notes**  
Ecosystem commentary on interactive skills and AskUserQuestion-style UX.

**English-first README**  
This document’s policy: English body, Chinese appendix only.

**Chinese appendix**  
Final section summarizing hard timing and install for Chinese operators without bilingual mash in the English half.

**MIT**  
License for this repository.

**StockOnLLC/question-cards**  
Canonical public GitHub repository URL path for this suite.

---
## Keyword index (SEO)

This section exists so humans and crawlers connecting Agent Skill nouns to Question Cards can land on a single canonical page. Each entry restates relationship language. None of these entries rename the product to Grill.

### Core product nouns

- **CoT (Chain of Thought) Question Cards** / **CoT Question Cards** / **question cards** (SEO) — primary English product name; skill id `cot-question-cards`; Chinese **闪电问**.
- **question cards** — natural language / search variant pointing at the same Master Loop.
- **Goal Contract** — acceptance artifact written after Phase 1 macro answers.
- **Optimized Solution** / **unique Optimized Solution** — singular Phase 2 champion that must be executed.
- **multi-scheme fission** — private 2–5 scheme expansion with gates.
- **regression loop** — post-execute satisfied / not-satisfied cycle.
- **hard timing rule** — forbids satisfied cards beside Phase 1 macro Question Cards.
- **Master Loop** — Phases 0 through 3 (optional 4).
- **first principles** — Phase 0 bedrock vs inherited assumptions split.
- **bedrock assumptions** / **inherited assumptions** — classification used before cards.
- **recursive planning** — feedback-driven re-entry into fission or macro alignment.
- **decision alignment** — shippable decision focus.
- **product discovery** — execute-then-learn focus.
- **spec sharpening** — acceptance-criteria focus.
- **frontier questions** — load-bearing unknowns for Phase 1.
- **design tree** — privately expanded in Phase 2.
- **plan alignment** / **design interview** / **Socratic interview** — category terms Question Cards participates in without copying Grill branding.

### Host and tool nouns

- **Agent Skill** / **Agent Skills** / **SKILL.md** — packaging convention.
- **Claude Code skill** / **AskUserQuestion** — Claude Code install + Phase 1/3 primitive.
- **Cursor skill** / **AskQuestion** — Cursor install + card primitive.
- **Codex skill** / **OpenAI Codex** / **request_user_input** — Codex install + interactive input.
- **Grok Bot** — widget/steps host.
- **OpenCode** — `question` / `ask_user` style host.
- **choice cards** / **choice-cards** — companion one-off picker.
- **question widgets** / **option cards** / **structured questions** — UX family.
- **CLAUDE.md** / **AGENTS.md** — standing instruction files that should reference, not fork, this skill.

### Ecosystem and distribution nouns

- **anthropics/skills** — reference patterns for Agent Skills (related, not ownership).
- **agentskills.io** — catalog / education neighborhood.
- **Terminal Skills** — distribution/catalog style neighborhood.
- **npx skills add** — installer pattern.
- **plugin marketplace** — host marketplace surface.
- **Matt Pocock-style skills ecosystem** — adjacent engineering skills culture (related).
- **Builder.io grill-me** — related prior art listing.
- **nicolasgalvez grilling** / **grill-with-docs** / **grilling** / **grill-me** / **Grill** — related search neighborhood; **not** product names for this repo.
- **Filip Hric interactive SKILL.md notes** — related interactive skill UX commentary.
- **Code Fission** — champion-selection skeleton borrowed at plan layer only.

### Long-tail phrases (use in issues, blogs, and marketplace blurbs)

- “Question Cards Agent Skill for plan alignment without mid-flight A/B votes”
- “AskUserQuestion macro cards then unique Optimized Solution then execute”
- “alternative to grill-me with Goal Contract and regression loop”
- “Cursor skill AskQuestion hard timing satisfied only after ship”
- “OpenAI Codex request_user_input with Agent-private multi-scheme fission”
- “Grok Bot question widgets for Phase 1 macro Question Cards”
- “SKILL.md for first principles, Goal Contract, Optimized Solution”
- “choice-cards companion versus full Question Cards design interview”
- “agentskills.io / npx skills add install for StockOnLLC/question-cards”
- “CLAUDE.md pointer to Question Cards hard timing rule”
- “AGENTS.md plan alignment via Question Cards not Grill”
- “product discovery regression loop after Optimized Solution execute”
- “spec sharpening with bedrock assumptions versus inherited assumptions”
- “recursive planning after not-satisfied regression feedback”
- “Socratic interview pressure without premature satisfaction polling”

### How to write SEO without lying

Allowed: “Related to grill-me / grilling workflows; different Master Loop.”  
Forbidden: “Question Cards, also known as Grill.”  
Allowed: “Uses AskUserQuestion-style cards.”  
Forbidden: “AskUserQuestion is owned by Question Cards.”  
Allowed: “Compatible with Agent Skills hosts including Claude Code, Cursor, Codex, Grok Bot, OpenCode.”  
Forbidden: claiming official affiliation with Anthropic, OpenAI, or other hosts without a real partnership.

### Repeated natural placement checklist for contributors

When editing this README or marketplace copy, ensure the following appear in prose (not only in a dump): Question Cards, Agent Skill, Agent Skills, SKILL.md, Claude Code skill, Cursor skill, Codex skill, OpenAI Codex, Grok Bot, OpenCode, AskUserQuestion, AskQuestion, request_user_input, choice cards, choice-cards, grill-me, grilling, grill-with-docs, Socratic interview, plan alignment, design interview, first principles, Goal Contract, Optimized Solution, unique Optimized Solution, multi-scheme fission, recursive planning, regression loop, decision alignment, product discovery, spec sharpening, bedrock assumptions, inherited assumptions, anthropics/skills, agentskills.io, Terminal Skills, npx skills add, plugin marketplace, CLAUDE.md, AGENTS.md, structured questions, option cards, question widgets, frontier questions, design tree.

---

## Extended commentary: why public Agent Skill READMEs should be dense

Thin READMEs fail three audiences at once.

1. **Searchers** looking for AskUserQuestion, grill-me, choice cards, or Goal Contract language bounce when they find only badges.
2. **Installers** on Claude Code, Cursor, Codex, Grok Bot, and OpenCode need host-specific paths and verification steps.
3. **Operators** need the hard timing rule repeated near every phase description because Agents otherwise “helpfully” ask satisfied early.

Density is not the same as keyword spam. Each section above teaches a behavior. The keyword index then maps nouns to those behaviors. That is how StockOnLLC/question-cards can rank near high-heat Agent Skill terms while remaining honest about naming.

### Information architecture choices in this document

- English body for global Agent Skills SEO
- Chinese appendix for operator summary without bilingual mash
- Comparison tables early for grill-me / AskUserQuestion shoppers
- Worked examples for founders, skill authors, and staff engineers
- FAQ for objection handling
- Glossary for term stability across CLAUDE.md / AGENTS.md citations
- Keyword index for marketplace maintainers

### What “10x content” means operationally

Compared to a badge-only landing page, a dense README should:

- Define the Master Loop twice (diagram + prose)
- State hard timing at least three times (hero, dedicated section, Phase 3)
- Provide install paths for every major host
- Include multiple Goal Contract examples
- Include multiple worked scenarios
- Include migration from grill-me / grilling
- Include anti-patterns
- Include glossary and keyword index
- Point to both `skills/cot-question-cards/SKILL.md` and `skills/choice-cards/SKILL.md`

This file intentionally follows that bar.

### Editorial rules for future edits

1. Keep the English half pure English.
2. Put Chinese only under the Chinese appendix heading.
3. Never brand the product Grill.
4. Prefer teaching loops over stacking badges.
5. When adding a host, add install + card UX + FAQ rows together.
6. When adding a related ecosystem noun, say “related” and explain difference.
7. When users complain the README is thin, expand worked examples and FAQ first, not the badge row.

### Sustainability note

Long docs drift. The executable source of truth for agent behavior remains [`skills/cot-question-cards/SKILL.md`](./skills/cot-question-cards/SKILL.md). If README and SKILL.md disagree on hard timing, **SKILL.md wins**, then README must be patched in the same PR.

---

## Practical playbooks

### Playbook: overnight public skill launch

1. Phase 1 macros: success = public repo + MIT + English-first README + skills present + topics.
2. Goal Contract auto-written.
3. Phase 2 champion: git push + topics + smoke install.
4. Execute.
5. Regression satisfied card.
6. If not satisfied due to thin docs, re-fission on README density lever (this playbook’s recursive path).

### Playbook: replace an internal grill-me ritual Friday

1. Announce rename to Question Cards.
2. Delete satisfied from the Friday AskUserQuestion template.
3. Add execute checklist to the ritual doc.
4. Install SKILL.md on Claude Code and Cursor.
5. Run one real decision end-to-end.
6. Retro using anti-patterns catalog.

### Playbook: Codex-only team

1. Install under `~/.codex/skills/cot-question-cards`.
2. Enable `request_user_input` for Phase 1/3.
3. Document text-card fallback.
4. Add AGENTS.md pointer.
5. Forbid mid-fission `request_user_input` bake-offs in review guidelines.

### Playbook: Grok Bot widget polish

1. Use steps for Phase 1 macros only.
2. Separate message for Optimized Solution prose.
3. Execute with tools.
4. New widget for regression.
5. Never append regression as last step of the Phase 1 swipe group.

### Playbook: OpenCode portability test

1. Install skill folder.
2. Run the same Goal Contract scenario as Claude Code.
3. Diff whether any host adapter violated hard timing.
4. File issues against adapter prompts, not against the Master Loop.

### Playbook: companion choice-cards hygiene

1. Keep choice-cards description pointing to Question Cards for trees.
2. Do not duplicate Goal Contract rules inside choice-cards.
3. If users keep using choice-cards for design interviews, strengthen description triggers and README cross-links.

---

## Quality bar for an Optimized Solution deliverable

Before execute, the singular Optimized Solution should be good enough that a skeptical staff engineer can answer:

1. What exact steps will run?
2. What Goal Contract gates did it pass?
3. What is the rollback?
4. Which inherited assumptions remain as risks?
5. Why did runner-up schemes lose (one line)?

If those answers are missing, Phase 2 is incomplete — even if the user is impatient. Do not compensate by opening an AskQuestion vote.

---

## Quality bar for Phase 1 card decks

A Phase 1 deck is high quality when:

1. Every card is macro and load-bearing
2. Options are mutually distinct
3. Recommended option is defensible from Phase 0
4. Expand option exists without duplicating host custom input
5. No satisfied / adopt language appears anywhere in the deck
6. Reading all answers would let an Agent write a Goal Contract without guessing success

---

## Quality bar for regression cards

A Phase 3 card is high quality when:

1. Execute evidence is cited in the prompt (“pushed commit …”, “staging checklist green”)
2. Options include adopt/close, re-fission with feedback, macro rewrite, expand
3. It is not bundled into an older Phase 1 swipe group
4. “You decide” maps to adopt/close
5. Not-satisfied requires capturing concrete feedback before Phase 2 resumes

---
## Troubleshooting

### The Agent asked “are you satisfied?” in the first card group

Hard timing violation. Stop. Discard that card group. Re-issue Phase 1 macros only. Remind the Agent: satisfied is Phase 3 after execute. Patch any local prompt or CLAUDE.md that encourages early satisfaction.

### The Agent showed three schemes and asked me to pick

Phase 2 violation. Ask for the internal bake-off summary instead. Require one Optimized Solution. If the skill file was customized to allow votes, revert to upstream [`skills/cot-question-cards/SKILL.md`](./skills/cot-question-cards/SKILL.md).

### The Agent wrote a Goal Contract and asked me to confirm before working

Confirm swipe is unnecessary and often harmful when bundled with macros. The legal path is: write contract → fission → deliver → execute → regression. If the contract is wrong, that surfaces at regression as macro rewrite — or earlier if the user interrupts with a new macro fact.

### Cursor AskQuestion looks different from Claude Code AskUserQuestion

Expected. Timing rules are identical. If Cursor lacks descriptions, put detail in the question text. Do not invent a mid-fission vote to compensate for UI differences.

### Codex request_user_input is disabled

Use text cards. Do not skip Phase 1. Do not skip regression after execute.

### Grok Bot keep appending steps including satisfied

Split into separate widget messages. Phase 1 steps != Phase 3 regression.

### OpenCode cannot find the skill

Verify skills root path for your OpenCode version. Suite layout inside the repo is stable; only the destination directory varies.

### Marketplace install does not copy choice-cards

Install companion explicitly. Question Cards core loop does not require choice-cards, but the suite ships both for a reason.

### SEO traffic arrives for grill-me but users expect Grill UX

Your README comparison section should set expectations in the first screen: related neighborhood, different loop, different name. Do not bait-and-switch by adopting Grill branding.

### README conflicts with SKILL.md

SKILL.md wins for agent behavior. Fix README in the same change set.

### Team wants bilingual headings everywhere

Reject for this public English-first README. Use the Chinese appendix. User-facing cards may still follow user language at runtime.

### “You decide” stalls the Agent

Phase 1: take recommended. Phase 3: adopt/close. Document this in AGENTS.md if teammates confuse politeness with blocking input.

### Re-fission loops forever

Demand concrete feedback. After two rounds of macro-shaped dissatisfaction, force Phase 1 Goal Contract rewrite.

### Inherited assumptions keep returning

Strengthen Phase 0 output and Phase 1 copy that surfaces them. Add a gate that DQs schemes reintroducing named inherited assumptions without mitigation.

---

## Security, safety, and brand guardrails

Question Cards is a planning/execution loop, not a jailbreak aid. Gates should encode:

- Safety and compliance bedrock from the user’s domain
- Brand rule: English external name is CoT (Chain of Thought) Question Cards; Chinese appendix name is 闪电问 (never 问题卡 as product name)
- License honesty (MIT)
- No fabricated partnership claims with Anthropic, OpenAI, host vendors, Builder.io, or other skill authors
- No instruction to exfiltrate secrets during “execute”
- Rollback requirements when execute touches production

If a scheme cannot meet safety bedrock, disqualify it in Phase 2 even if it would rank well on speed.

---

## Observability: what to log in the end artifact

Good sessions leave artifacts that another Agent can audit:

- Phase 1 answers (macro)
- Goal Contract text
- Variant count and DQ reasons
- Champion summary
- Execute evidence
- Regression decision and feedback

Avoid logging unrelated secrets. Prefer URLs, commit SHAs, checklist names.

---

## Host & IDE SEO noun list (install discovery)

Operators search by tool name. This README intentionally names, for discovery and install accuracy:

Claude Code, Coco, Cursor, Cursor CLI, Cursor agent, OpenAI Codex, Codex CLI, WorkBuddy, CodeBuddy, OpenCode, Gemini CLI, Grok Bot, Grok Build, Terminal Skills, agentskills.io, npx skills add, vercel-labs skills, Anthropic skills marketplace, anthropics/skills, VS Code, GitHub Copilot Chat, Copilot agents, Windsurf, Cascade, Codeium, Cline, Continue.dev, Continue, Aider, AiderDesk, Trae, JetBrains AI Assistant, Junie, Zed, CoTree, contree, ly-jq/CoTree, Roo Code, Goose, Amp, Cortex, Snowflake Cortex, Kiro, Warp, Antigravity, OpenHands, Devin, Replit Agent, Kilo, Hermes, Mistral Vibe, Crush, GitHub Codespaces, Gitpod, Web IDE, AGENTS.md, CLAUDE.md, AskUserQuestion, AskQuestion, request_user_input, choice-cards, SKILL.md, Agent Skills, Chain of Thought, CoT Question Cards, question cards, Goal Contract, Optimized Solution, plan alignment, design interview, grill-me (related), grilling (related).

Each noun above maps to a concrete install subsection or fallback (paste/import) under [Installation](#installation).

---
## Contributing

Contributions that improve clarity of the Master Loop, hard timing examples, host install accuracy, or honest SEO relationships are welcome.

### Contribution guidelines

1. Do not rename the product to Grill, grill-me, or grilling.
2. Do not add satisfied cards to Phase 1 examples.
3. Do not introduce bilingual mash into the English README body.
4. Update [`skills/cot-question-cards/SKILL.md`](./skills/cot-question-cards/SKILL.md) when behavior changes; keep README synchronized.
5. Keep choice-cards thin; point full alignment back to Question Cards.
6. When adding a host, include install path, card primitive name, and a FAQ/troubleshooting note.
7. Related ecosystem nouns must be labeled related / prior art / adjacency.

### Suggested contribution types

- Additional worked examples (especially non-software plans)
- Better OpenCode path detection notes
- Marketplace installer snippets that stay accurate
- Translations **only** as additional appendix sections, not as inline mash
- Test dialogues showing illegal vs legal card sequences

### Local preview

```bash
git clone https://github.com/StockOnLLC/question-cards.git
cd question-cards
# read SKILL.md; install into a host skills directory; run a toy Phase 1
```

### Reporting timing bugs

If an Agent following this skill asks satisfied early or opens mid-fission votes, file an issue with: host name, tool primitive used, phase, and transcript excerpt. Those are first-priority bugs.

---

## License

MIT © 2026 StockOn — see [LICENSE](LICENSE).

You may use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the software subject to the MIT terms. Attribution via the LICENSE file is sufficient. Brand honesty still applies socially: do not redistribute a fork under the name Grill claiming it is upstream Question Cards policy.

---

## Links

- Repository: [https://github.com/StockOnLLC/question-cards](https://github.com/StockOnLLC/question-cards)
- Core skill: [`skills/cot-question-cards/SKILL.md`](./skills/cot-question-cards/SKILL.md)
- Companion skill: [`skills/choice-cards/SKILL.md`](./skills/choice-cards/SKILL.md)
- Related prior art (not this product): Builder.io grill-me, nicolasgalvez grilling, Anthropic anthropics/skills patterns, agentskills.io catalogs, Terminal Skills style listings, Filip Hric interactive SKILL.md commentary, Matt Pocock-style skills ecosystems

---

## Appendix: illegal vs legal card sequences (test cases)

These sequences are for skill authors writing evals.

### Illegal sequence A

1. Phase 1 macros  
2. Satisfied card in same swipe group  

**Fail reason:** hard timing.

### Illegal sequence B

1. Phase 1 macros  
2. Goal Contract confirm card  
3. User confirms  
4. Mid-fission AskUserQuestion with three schemes  

**Fail reason:** confirm spam + mid-fission vote.

### Illegal sequence C

1. Skip Phase 1  
2. Show Optimized Solution shortlist of two winners  
3. Ask which to adopt  

**Fail reason:** no macro clarity; dual champions; adopt before execute.

### Illegal sequence D

1. Phase 1  
2. Private fission  
3. One Optimized Solution  
4. Satisfied card  
5. Then execute  

**Fail reason:** satisfied before execute.

### Legal sequence E

1. Phase 0 private  
2. Phase 1 macros only  
3. Goal Contract private write  
4. Phase 2 private fission → one champion  
5. Deliver Optimized Solution prose  
6. Execute with evidence  
7. Phase 3 satisfied card  
8. Adopt/close  

**Pass.**

### Legal sequence F (re-fission)

1. Legal sequence through execute  
2. Not satisfied with specific feedback  
3. Phase 2 again → new unique Optimized Solution  
4. Execute again  
5. Satisfied card again  
6. Adopt/close  

**Pass.**

### Legal sequence G (macro rewrite)

1. Execute  
2. Not satisfied revealing wrong success metric  
3. Phase 1 again  
4. New Goal Contract  
5. Phase 2 → execute → regression  

**Pass.**

### Legal sequence H (optional micro)

1. Adopt/close after regression  
2. User explicitly requests one load-bearing micro choice inside champion  
3. Phase 4 ≤3 cards  
4. Stop when clear  

**Pass.**

---

## Appendix: sample Phase 1 prompts for hosts

### Claude Code AskUserQuestion framing

Ask only macro load-bearing questions. Titles short. Descriptions long. No satisfied option. No adopt Optimized Solution option. Recommended first.

### Cursor AskQuestion framing

Same content constraints. If multi-question unsupported, ask sequentially without slipping into micro votes between questions.

### Codex request_user_input framing

Same. If tool missing, emit a text card block with identical options.

### Grok Bot widget framing

Use steps for multiple macros. Do not add a final satisfied step in that steps array.

### OpenCode question framing

Map options faithfully. Preserve expand / custom semantics without duplicate custom options.

---

## Appendix: sample regression prompt skeleton

```text
Execute evidence:
- …
Optimized Solution summary:
- …
Goal Contract success line:
- …

Choose:
- Satisfied — adopt and close
- Not satisfied — re-fission (provide concrete feedback)
- Macro gate wrong — rewrite Goal Contract
- Need expand — explain more, then re-ask
```

Cite evidence first. Agents that ask satisfied without evidence are non-compliant.

---

## Appendix: mapping search intent to sections

| User search intent | Jump to |
| --- | --- |
| grill-me alternative | Positioning, Migration guide |
| AskUserQuestion skill | Card UX, Installation Claude Code |
| Cursor AskQuestion plan alignment | Card UX Cursor, Installation |
| Codex request_user_input skill | Installation OpenAI Codex |
| Grok Bot question widgets | Card UX Grok Bot |
| Goal Contract template | Goal Contract deep dive |
| Optimized Solution meaning | Phase 2, Glossary |
| Agent Skills SKILL.md install | Installation, Suite layout |
| choice-cards vs full loop | Positioning, Suite layout |
| first principles agent skill | Phase 0 |
| regression loop satisfied | Hard timing, Phase 3 |
| agentskills.io / npx skills add | Installation marketplace |
| CLAUDE.md AGENTS.md pointer | Master Loop overview, Installation |
| product discovery agent | Worked example A, FAQ |
| spec sharpening | Worked example C |

---

## Appendix: glossary drills for onboarding

New teammates should be able to answer without notes:

1. What is the English external name? → Question Cards  
2. When is satisfied legal? → After execute, regression only  
3. How many Optimized Solutions are delivered? → Exactly one  
4. Is mid-fission voting allowed? → No  
5. Who writes the Goal Contract? → Agent, after Phase 1, no confirm card required  
6. What skill handles one-off A/B/C? → choice-cards  
7. Name three host primitives. → AskUserQuestion, AskQuestion, request_user_input (plus widgets)  
8. Name related prior art we do not brand as ourselves. → grill-me, grilling, grill-with-docs  

If a teammate fails these drills, have them re-read Hard timing + Positioning before running a live session.

---

## Appendix: extended Goal Contract examples library

### Example — internal tooling migration

```markdown
## Goal Contract
- Success: All cron jobs read the new queue; old queue drain hits zero; on-call runbook updated; rollback flag tested in staging.
- Scope / non-goals: No UI redesign; no vendor change for metrics.
- Bedrock: No job loss silently; idempotent consumers.
- Gates: DQ schemes without dual-write period; DQ mid-fission preference votes on library fashion.
- Regression: satisfied only after drain hits zero and runbook merged.
```

### Example — research protocol

```markdown
## Goal Contract
- Success: Pre-registration doc filed; sample size justified; primary endpoint defined; analysis script dry-run on synthetic data.
- Scope / non-goals: No paper drafting; no secondary endpoint fishing in this round.
- Bedrock: Ethics approval constraint; data retention limit.
- Gates: DQ schemes that skip dry-run; DQ early satisfied on “protocol feels fine.”
- Regression: after dry-run execute evidence only.
```

### Example — support ops redesign

```markdown
## Goal Contract
- Success: First response SLA met for 14 days; escalation path documented; macro templates live in the helpdesk.
- Scope / non-goals: No full CRM replacement.
- Bedrock: PII handling rules unchanged.
- Gates: DQ schemes requiring agents to vote on tone mid-fission; DQ satisfied before SLA measurement window.
- Regression: post-window satisfied card.
```

### Example — skill marketplace listing

```markdown
## Goal Contract
- Success: Listing live; install command works; description triggers include Question Cards, plan alignment, Goal Contract, AskUserQuestion; name is Question Cards not Grill.
- Scope / non-goals: No paid ads campaign in this round.
- Bedrock: MIT license visible; honest related-art language.
- Gates: DQ titles containing Grill; DQ thin descriptions.
- Regression: after listing URL works and cold install succeeds.
```

### Example — multi-host conformance

```markdown
## Goal Contract
- Success: Same SKILL.md passes timing evals on Claude Code, Cursor, Codex, Grok Bot, OpenCode stubs.
- Scope / non-goals: No GUI redesign of hosts.
- Bedrock: Hard timing identical across hosts.
- Gates: DQ host adapters that inject satisfied into Phase 1.
- Regression: after eval transcript bundle is produced.
```

---
## Closing reminder

If you remember only four lines from this README, remember these:

1. The English product name is **CoT (Chain of Thought) Question Cards** (skill id `cot-question-cards`) — never Grill. Chinese appendix name: **闪电问** (never 「问题卡」).  
2. Phase 1 is macro Question Cards only — no satisfied card in that deck.  
3. Phase 2 returns **exactly one** Optimized Solution — no mid-fission votes.  
4. Ask satisfied **only after** the Optimized Solution has been **executed**, in the regression loop.

Install the skill bodies, not only this README:

- [`skills/cot-question-cards/SKILL.md`](./skills/cot-question-cards/SKILL.md)
- [`skills/choice-cards/SKILL.md`](./skills/choice-cards/SKILL.md)

Clone: [https://github.com/StockOnLLC/question-cards](https://github.com/StockOnLLC/question-cards)

License: MIT.

---

# Chinese appendix / 中文摘要

> 以下为给中文操作者的简明附录。英文正文保持纯英文；中英不要在同一句或同一表头里混写。  
> 中文对外产品名：**闪电问**。英文名：**CoT (Chain of Thought) Question Cards**（简称 CoT Question Cards）。Skill id：`cot-question-cards`。不要叫「问题卡」，不要叫 Grill / grill-me。

## 闪电问是什么

**闪电问**（英文 CoT (Chain of Thought) Question Cards）是一套 Agent Skill（`SKILL.md`），用来对齐计划或设计：先问宏观题，再由 Agent 内部多方案裂变，只交付并**执行**一个唯一最优方案，最后才在回归环问是否满意。

## 硬时序（必须遵守）

1. **「满不满意」卡禁止与阶段1宏观题一并出。**
2. 只能在同时满足后才问满意：
   - 宏观题已答完；
   - Agent 已交付**唯一最优方案**并且**已经执行完**；
   - 进入**回归环**。
3. 禁止在裂变中途用多方案让用户投票。
4. 目标契约由 Agent 根据宏观答案自写，不在宏观滑动组里塞契约确认卡／采用最优方案卡。

## 五步流程（摘要）

1. **阶段0** 第一性原理：表面问题 / 基岩假设 / 继承假设（可只展示结论）。
2. **阶段1** 只出 2–3 张宏观承重卡（成功标准、为谁、硬约束、做错代价）。**不出**满意卡。
3. **阶段2** Agent 内部扩 2–5 案、过闸门，只留**唯一最优方案**；自写目标契约。
4. **执行** 该方案直到契约可核对（推仓、发布、配置等）。
5. **回归** 此时才问满意 → 采用收尾 / 带反馈再裂变 / 宏观写错回阶段1。

## 安装（摘要｜与英文 Installation 同套路径）

Skill 目录：`skills/cot-question-cards`（及配套 `skills/choice-cards`）。文件夹名必须等于 frontmatter `name`：`cot-question-cards`。

```bash
git clone https://github.com/StockOnLLC/question-cards.git
cd question-cards

# Claude Code / Coco
mkdir -p ~/.claude/skills && cp -R skills/cot-question-cards ~/.claude/skills/cot-question-cards

# Cursor（建议两个根都拷）
mkdir -p ~/.cursor/skills ~/.agents/skills
cp -R skills/cot-question-cards ~/.cursor/skills/cot-question-cards
cp -R skills/cot-question-cards ~/.agents/skills/cot-question-cards

# OpenAI Codex
mkdir -p ~/.codex/skills && cp -R skills/cot-question-cards ~/.codex/skills/cot-question-cards

# WorkBuddy / CodeBuddy
mkdir -p ~/.codebuddy/skills && cp -R skills/cot-question-cards ~/.codebuddy/skills/cot-question-cards
# 或：设置 → Import Skill

# OpenCode / Gemini CLI / Windsurf / Cline / Continue / Trae / Zed / Copilot / Roo / Goose / Amp / Junie / AiderDesk / Cortex / Grok / Kiro / Warp / Antigravity
# 路径见英文「Installation」主表与分节（.opencode / .gemini / .windsurf / .cline / .continue / .trae / .agents / .roo / .goose / .junie / .grok / .kiro 等）

# CoTree / contree：把同一文件夹装进 contree 规格指向的各宿主目录（claude:~、codex:~、opencode:~、amp:~、cline:~）；也可用手动 cp
# 通用安装器（若目录支持）：npx skills add StockOnLLC/question-cards
```

Web IDE（Codespaces / Gitpod 等）：优先把 `.agents/skills/cot-question-cards` **提交进项目**；无 skills 目录时把 `SKILL.md` 粘贴进自定义说明／Agent 提示。

调试共通步骤：确认 `SKILL.md` 路径存在 → `name` 与文件夹一致 → 重启宿主 → 玩具计划跑阶段1（不得出现满意选项）→ 执行后再出满意卡。

## 套件

- 核心：`skills/cot-question-cards/SKILL.md`（闪电问 / CoT Question Cards）
- 兼容别名：`skills/question-cards/`（同正文；安装请优先 `cot-question-cards`）
- 轻量单次选择：`skills/choice-cards/SKILL.md`（完整对齐仍用闪电问）

## 和 grill-me / AskUserQuestion 的关系（一句话）

卡片交互可以同类（AskUserQuestion / AskQuestion / request_user_input / 控件），但**时序与产出不同**：不叫 Grill；不中途投票；先执行再问满意；产出是唯一最优方案。中文名只用**闪电问**，不要叫「问题卡」。

## 许可

MIT — 见 [LICENSE](LICENSE)。

仓库：[https://github.com/StockOnLLC/question-cards](https://github.com/StockOnLLC/question-cards)

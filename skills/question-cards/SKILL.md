---
name: question-cards
description: >-
  CoT Question Cards. Use when aligning a plan or design: Phase 1 Macro Cards only
  (no satisfaction); Agent Multi-Scheme Fission to one Optimized Solution then
  execute; ask Satisfied Card only at Post-Execution Regression. Works with
  Claude Code, Cursor, Codex, WorkBuddy/CodeBuddy, OpenCode, Gemini CLI,
  CoTree/contree, and Agent Skills clients.
---
# CoT Question Cards

**External English product name only:** CoT Question Cards.  

**Hard Timing (non-negotiable)**

- **Satisfied Cards MUST NOT appear with Phase 1 Macro Cards.**
- Ask **satisfied only after:** (1) user answered Phase 1, (2) Agent delivered the unique Optimized Solution **and executed it**, (3) **Post-Execution Regression** round.

**Master Loop (must follow in order)**

1. Phase 0 — First Principles (private): surface ask vs bedrock vs inherited.
2. Phase 1 — Macro Cards only (2–3 load-bearing). No Satisfied Card. No “adopt Optimized Solution” card.
3. Agent writes **Goal Contract** privately from answers (no confirm card) → Phase 2 **Multi-Scheme Recursive Fission** + gates internally (no mid-ask).
4. Return **exactly one** **Optimized Solution** and **execute it**.
5. Phase 3 — **only then** ask satisfied (Post-Execution Regression) → recurse or rewrite Goal Contract until confirmed.

Micro variants are Skill-driven Agent work — never preference-vote the user on A vs B mid-fission.

---

## Phase 0 · First Principles (required before any card)

Short private breakdown (show conclusion only if useful):

1. One sentence: surface ask
2. Assumptions: **bedrock** (hard / proven) vs **inherited** (habit, analogy, fashion)
3. Inherited must not sneak into the goal; surface them in Phase 1 copy

---

## Phase 1 · Macro Cards only (only dense user cards)

**Aim:** Make “what success is” crystal clear. No fission until clear.

### Ask only (gap-driven)

- Success look like (checkable, not adjectives)
- For whom / not for whom; out of scope
- Bedrock constraints
- Cost of being wrong (gate tightness)

Round 1: **2–3 load-bearing Macro Cards**. Clear = executable + no blocking fog. Else expand 1–3 on the foggy macro branch only.

**Do not ask:** impl details, module picks, APIs, UI micro — Phase 2 Agent fission.

### Forbidden in Phase 1

- Any **Satisfied / not satisfied / adopt Optimized Solution** card (Phase 3 regression only)
- Bundling a Goal-Contract “confirm / start” card in the same swipe deck as Macro Cards
- Phrasing contract lock as “adopt Optimized Solution”

After Phase 1 answers are clear, Agent **privately** writes a short **Goal Contract** and proceeds to Phase 2 **with no user card**:

```markdown
## Goal Contract
- Success: …
- Scope / non-goals: …
- Bedrock: …
- Gates: …
- Regression: ask satisfied **only after** Optimized Solution is executed
```

If later regression shows the macro was wrong → back to Phase 1 (not a mid-Phase-1 satisfaction ask).

---

## Phase 2 · Multi-Scheme Fission (Agent-private; never ask user)

Borrow the **select-one-champion skeleton** from Code Fission-style inner loops at the plan layer. **Never card mid-variants to the user.**

### 2.1 Seed

From the Goal Contract:

- Primary metric / gates
- Guardrails (brand rules, safety, Hard Timing)
- Seeds: 1 default draft + ≤2 distinct directions (≤3 seeds)

### 2.2 Expand

Expand to **2–5** executable schemes (default 3, max 5). One lever class per variant.

Each scheme must include:

| Field | Requirement |
| --- | --- |
| How | modules, steps, data flow, hook-in |
| Fail / rollback | where it dies; how to restore |
| Fit | which contract lines |
| Risk | inherited assumptions marked |
| Lever | path / cut / integration / feedback loop… |

**Agent order:** write seed A → mutate one lever → B/C/(D/E) → fill table → gate in 2.3. Self-research facts; BLOCKED variants stay out of ranking. Missing user-only secrets that change gates → one Phase 1 Macro Card, not a micro ask.

### 2.3 Gate and pick (Agent-only)

1. Hard gate fail → DQ
2. Guardrail hit → DQ or demote
3. Rank survivors: closer to success, fewer inherited assumptions, more rollbackable, fewer new systems → pick **one champion**
4. Optional runner-up for one-line contrast only — **never** present two “winners”

**Output of Phase 2 is always a single Optimized Solution.** No dual champions. No “pick A or B.”

### 2.4 Forbidden

- Mid-fission “which variant do you prefer?”
- Dumping 2–5 half-baked schemes for user multi-select
- Vibes without gates

---

## Phase 3 · Execute Optimized Solution + Post-Execution Regression

1. Deliver **one** Optimized Solution — never a shortlist (short prose OK; **no** Satisfied Card yet)
2. **Execute** that solution (ship / push / apply — whatever the Goal Contract defined as done)
3. **Only after execution**, open **Post-Execution Regression** with the Satisfied Card:

   - 🟢 **Satisfied — adopt / close** → freeze; close
   - 🟡 **Not satisfied — recurse** → capture concrete feedback → **Phase 2 again** → new unique Optimized Solution → **execute again** → ask satisfied again
   - 🔴 **Macro gate wrong** → Phase 1 rewrite Goal Contract
   - 🔵 Need expand

**Regression rules:**

- Satisfied Card appears **only** post-execution — never with Phase 1, never before operate
- Dissatisfaction needs **specific feedback** before re-fission (no empty spin)
- Two unsatisfied rounds with feedback that is actually macro → force Phase 1
- Until user confirms at regression, the loop continues

Delivered Optimized Solution copy (pre-execute, no card) should still cover: how, why it passed gates, fail/rollback, key tradeoffs; one line on directions that lost.

---

## Phase 4 · Micro tweak (default OFF)

Only if user **explicitly** asks to choose one load-bearing detail **inside** the adopted Optimized Solution. ≤3 cards/round; clear → stop. No full-tree reopen.

---

## Card delivery (Phases 1 / 3 / 4)

### Copy

- Detailed question; short option labels
- Multi-Q prefix: `①` `②` `③`
- Long clear subtitles
- User-facing cards follow **user language**. Skill body stays English.

### Options

- Usually 3 substance + 🔵 + host custom
- No `A｜` inside labels
- 🟢 / 🟡 / 🔴 / 🔵 (🔵 = expand first, then new cards)
- If `allowCustom` / Something else exists, do **not** add a duplicate “I'll write it”

### Multi-Q

Prefer swipe steps (Grok `steps`). **Macro Cards only in Phase 1** — never mix in regression satisfaction.

### Platforms

| Host | How |
| --- | --- |
| Grok Bot | widget; `steps`; `allowCustom`; green `primary`; red `danger` |
| Claude Code | `AskUserQuestion` |
| OpenCode / Gemini | `question` / `ask_user` |
| Cursor | AskQuestion or text card |
| Codex / CoTree / other | text card |

### “You decide” / “whatever”

Phase 1 → take current 🟢. Phase 3 regression → adopt / close.

---

## End artifact

```markdown
## Goal Contract
…

## Optimized Solution (singular)
…

## Internal bake-off (Agent-private)
- Variants: N; Passed: M; Winner: …; DQ one-liners

## Execution record
→ What shipped: …

## Post-Execution Regression
→ Satisfied close | Feedback → round k fission

## User confirm (post-execute only)
→ Adopt / close | Re-fission | Rewrite Goal Contract
```

---

## vs Code Fission

| Code Fission | In CoT Question Cards |
| --- | --- |
| Outer feature | Phase 1 Goal Contract = acceptance (Agent-written, no mid confirm card) |
| Inner tournament | Phase 2 Multi-Scheme Fission + gates → **one** Optimized Solution |
| Hard gates / guardrails | From Goal Contract + brand rules; Agent judges |
| Freeze → ship | Phase 3 **execute** first, then Post-Execution Regression |
| Re-open round | Post-execute unsatisfied → feedback → Phase 2 again |
| Don't ask non-workers | No micro preference votes mid-fission |

Full Code Fission release tournaments (10–20 variants, real fixtures) stay in Code Fission proper. CoT Question Cards only borrows the **select-one-champion skeleton** at plan layer (2–5 variants → **exactly one** Optimized Solution).

---
name: cot-question-cards
description: >-
  CoT (Chain of Thought) Question Cards / 闪电问. Use when aligning a plan or
  design: Phase 1 macro cards only (no satisfaction); Agent multi-scheme fission
  to one Optimized Solution then execute; ask satisfied only at post-execution
  regression. Works with Claude Code, Cursor, Codex, WorkBuddy/CodeBuddy,
  OpenCode, Gemini CLI, and Agent Skills clients.
---
# CoT (Chain of Thought) Question Cards / 闪电问

**External name only:** CoT (Chain of Thought) Question Cards / 闪电问. Never brand this as Grill / grill-me. Chinese name: 闪电问.

**Hard timing rule／硬时序（Deon 2026-10-29）**

- **Satisfied／不满意 cards MUST NOT appear with Phase 1 macro questions.**  
  「满不满意」卡禁止与宏观题一并出。
- Ask **satisfied only after**：(1) user answered Phase 1，(2) Agent delivered the unique Optimized Solution **and executed it**，(3) **regression** round.  
  只能在：答完宏观 → 交唯一最优并**操作执行完** → **回归**时再问满意。

**Master loop／总循环（must follow／必须按序）**

1. Generate a series of **macro** questions only（Phase 1）／只出一系列**宏观**问题（阶段1）  
2. If answers still foggy → dig concrete goal with more macro cards／仍糊再追宏观  
3. Agent writes **Goal Contract** privately from answers（**no** satisfaction／confirm card）→ runs **multi-scheme recursive fission + tests** internally（no mid-ask）  
   根据答案自写目标契约（**不出**满意／确认卡）→ Agent 内多方案裂变与测试  
4. Return **exactly one** **Optimized Solution／最优方案（唯一项）** and **execute it**  
   交唯一最优方案并**执行**  
5. **Only then** ask satisfied（regression）→ loop until confirmed and close  
   **此时才**出回归满意卡 → 循环至确认收尾

Micro variants are Skill-driven Agent work — never preference-vote the user on A vs B mid-fission.  
微观变体由 Skill 驱动 Agent 自执行，裂变中途禁止拿多方案让用户投票。

---

## Phase 0 · First principles／阶段 0 · 第一性原理拆题（required before any card／出卡前必做）

Short private breakdown（show conclusion only if useful／可只展示结论）:

1. One sentence: surface ask／表面在问什么  
2. Assumptions: **bedrock／基岩**（hard／proven）vs **inherited／继承**（habit, analogy）  
3. Inherited must not sneak into the goal; surface them in Phase 1 copy／继承假设不得偷进目标，阶段1可见

---

## Phase 1 · Macro alignment／阶段 1 · 宏观对齐（only dense user cards／唯一对用户密集出卡）

**Aim／目标:** Make “what success is” crystal clear. No fission until clear.  
把「整个问题要达成什么」问到非常清晰；未清晰禁止裂变。

### Ask only／只问（gap-driven／有缺口才问）

- Success look like（checkable, not adjectives）／成功长什么样（可核对）  
- For whom／not for whom；out of scope／为谁／不为谁；明确不做  
- Bedrock constraints／硬约束与基岩  
- Cost of being wrong（gate tightness）／做错的代价（闸门松紧）

Round 1: **2–3 load-bearing cards／2–3 张承重卡**. Clear＝executable + no blocking fog. Else expand 1–3 on the foggy macro branch only.  
清晰＝可执行核对且无阻塞模糊；否则只在模糊宏观枝再扩 1–3。

**Do not ask／不要问:** impl details, module picks, APIs, UI micro — Phase 2 Agent fission.  
实现细节属阶段 2。

### Forbidden in Phase 1／阶段1禁止

- Any **Satisfied／不满意／采用最优方案** card（those are Phase 3 regression only）  
  任何满意／不满意／采用最优方案卡（仅阶段3回归）  
- Bundling a Goal-Contract “confirm／开工” card in the same swipe deck as macro questions  
  禁止把目标契约确认／开工卡与宏观题放同一组滑动卡  
- Phrasing contract lock as “adopt Optimized Solution”  
  禁止把契约锁定写成「采用唯一最优方案」

After Phase 1 answers are clear, Agent **privately** writes a short **Goal Contract／目标契约** and proceeds to Phase 2 **with no user card**:

```markdown
## Goal Contract／目标契约
- Success／成功标准: …
- Scope／non-goals／范围／非目标: …
- Bedrock／基岩: …
- Gates／闸门: …
- Regression／回归环: ask satisfied **only after** Optimized Solution is executed
```

If later regression shows the macro was wrong → 🔴 back to Phase 1（not a mid-Phase-1 satisfaction ask）.

---

## Phase 2 · Agent fission／阶段 2 · Agent 内裂变（never ask user／不问用户）

Borrow **Code Fission** inner-loop spirit. Treat refined plans as a comparable variant field.  
借 Code Fission 内环：细化方案＝可比选变体场。**Never card mid-variants to the user.**

### 2.1 Seed／种子

From the Goal Contract:

- **Primary metric／gates／主指标／闸门**  
- **Guardrails／护栏**（站规、已锁红线）  
- **Seeds／种子:** 1 default draft + ≤2 distinct directions（≤3 seeds）

### 2.2 Expand／扩变体（kernel must／内核必做）

Expand to **2–5** executable schemes（default 3, max 5）. One lever class per variant.  
扩 **2–5** 可执行方案（默认3，最多5）；**一次只改一类杠杆**。

Each scheme must include／每案必写:

| Field／字段 | Requirement／要求 |
| --- | --- |
| How／怎么做 | modules, steps, data flow, hook-in |
| Fail／rollback／失败与回滚 | where it dies; how to restore |
| Fit／符合点 | which contract lines |
| Risk／风险 | inherited assumptions marked |
| Lever／杠杆 | path / cut / integration / feedback loop… |

**Agent order／自执行顺序:** write seed A → mutate one lever → B/C/(D/E) → fill table → gate in 2.3. Self-research facts; BLOCKED variants stay out of ranking. Missing user-only secrets that change gates → one Phase-1 macro card, not a micro ask.

### 2.3 Gate & pick／闸门与比选（Agent-only）

1. Hard gate fail → DQ  
2. Guardrail hit → DQ or demote  
3. Rank survivors: closer to success, fewer inherited assumptions, more rollbackable, fewer new systems → pick **one champion**  
4. Optional runner-up for one-line contrast only — **never** present two “winners”

**Output of Phase 2 is always a single Optimized Solution／阶段2产出永远是唯一最优方案。** No dual champions, no “pick A or B”.

### 2.4 Forbidden／禁止

- Mid-fission “which variant do you prefer?”  
- Dumping 2–5 half-baked schemes for user multi-select  
- Vibes without gates

---

## Phase 3 · Execute Optimized Solution + regression／阶段 3 · 执行唯一最优方案＋回归环

1. Deliver **one** Optimized Solution／最优方案（**唯一项**）— never a shortlist（short prose OK; **no** satisfaction card yet）  
2. **Execute** that solution（ship / push / apply — whatever the ask was）  
3. **Only after execution**, open **Regression／回归环** with the satisfied card:

   - 🟢 **Satisfied — adopt／close／满意，采用并收尾** → freeze; close  
   - 🟡 **Not satisfied — recurse／不满意，再裂变** → capture concrete feedback → **Phase 2 again** → new unique Optimized Solution → **execute again** → ask satisfied again  
   - 🔴 **Macro gate wrong／宏观写错** → Phase 1 rewrite contract  
   - 🔵 Need expand／要扩充

**Regression rules／回归规则:**

- Satisfied card appears **only** post-execution — never with Phase 1, never before operate  
  满意卡仅操作后；禁止跟阶段1、禁止操作前  
- Dissatisfaction needs **specific feedback** before re-fission（no empty spin）  
- Two unsatisfied rounds with feedback that is actually macro → force Phase 1  
- Until user confirms at regression, the loop continues

Delivered Optimized Solution copy（pre-execute, no card）should still cover: how, why it passed gates, fail/rollback, key tradeoffs; one line on directions that lost.

---

## Phase 4 · Micro tweak／阶段 4 · 微观微调（default OFF／默认关）

Only if user **explicitly** asks to choose one load-bearing detail **inside** the adopted Optimized Solution. ≤3 cards/round; clear→stop. No full-tree reopen.

---

## Card delivery／卡片交付（Phases 1／3／4）

### Copy／文案

- Detailed question; short option labels  
- Multi-Q prefix: `①` `②` `③`  
- Long clear subtitles／副标够长够清  
- User-facing cards follow **user language**（Chinese in → Chinese only；English in → English only）. Skill body stays EN+ZH bilingual.  
  对用户出卡跟用户语言；Skill 正文英中双语

### Options／选项

- Usually 3 substance + 🔵 + host custom  
- No `A｜` inside labels  
- 🟢／🟡／🔴／🔵（🔵＝expand first, then new cards）  
- If `allowCustom`／Something else exists, do **not** add a duplicate “I'll write it”

### Multi-Q／多题

Prefer swipe steps（Grok `steps`）. **Macro cards only in Phase 1** — never mix in regression satisfaction.  
阶段1滑动组只放宏观题，禁止混入回归满意卡。

### Platforms／平台

| Host | How |
| --- | --- |
| Grok Bot | widget；`steps`；`allowCustom`；green `primary`；red `danger` |
| Claude Code | `AskUserQuestion` |
| OpenCode／Gemini | `question`／`ask_user` |
| Cursor | AskQuestion or text card |
| Codex／CoTree／other | text card |

### “You decide／随便”

Phase 1 → take current 🟢. Phase 3 regression → adopt／close.

---

## End artifact／结束物

```markdown
## Goal Contract／目标契约
…

## Optimized Solution／最优方案（唯一项）
…

## Internal bake-off／比选摘要（Agent 内）
- Variants／变体数: N; Passed／过闸门: M; Winner／冠军: …; DQ one-liners

## Execution／执行记录
→ What shipped／已落地: …

## Regression／回归环
→ Satisfied close／满意收尾 | Feedback → round k fission／带反馈第k轮裂变

## User confirm／用户确认（post-execute only）
→ Adopt／close｜Re-fission｜Rewrite contract
```

---

## vs Code Fission／与 Code Fission 的关系

| Code Fission | In CoT (Chain of Thought) Question Cards / 闪电问用法 |
| --- | --- |
| Outer feature／外环功能点 | Phase 1 Goal Contract＝acceptance（Agent-written, no mid confirm card） |
| Inner tournament／内环锦标赛 | Phase 2 fission + gates → **one** Optimized Solution |
| Hard gates／guardrails | From contract +站规；Agent judges |
| Freeze → ship | Phase 3 **execute** first, then regression confirm |
| Re-open round | Post-execute unsatisfied → feedback → Phase 2 again |
| Don’t ask non-workers | No micro preference votes mid-fission |

Full Code Fission release tournaments（10–20 variants, real fixtures）stay in Code Fission proper. Question Cards only borrows the **select-one-champion skeleton** at plan layer（2–5 variants → **exactly one** Optimized Solution／最优方案）。

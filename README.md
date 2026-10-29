# Question Cards／问题卡

**Public Agent Skill** for aligning any plan or design — without mid-flight A/B votes.

**Macro cards → private multi-scheme fission → exactly one Optimized Solution／唯一最优方案 → execute → post-execution regression (satisfied card only then).**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-SKILL.md-black.svg)](#install--安装)
[![Works with](https://img.shields.io/badge/Claude%20Code%20%7C%20Cursor%20%7C%20Codex%20%7C%20Grok%20Bot-compatible-blue.svg)](#install--安装)
[![Bilingual](https://img.shields.io/badge/EN%2FZH-bilingual-informational.svg)](#english--中文)
[![Related](https://img.shields.io/badge/vs-grill--me%20%7C%20AskUserQuestion%20%7C%20grilling-orange.svg)](#vs-grill-me--askuserquestion--grilling)

> **External name only:** **Question Cards／问题卡**. Never brand this as Grill／grill-me／grilling.

---

## TL;DR／一句话

| You get／你得到 | You don't get／你不会得到 |
| --- | --- |
| Clear success criteria via **macro Question Cards** | 3–5 half-baked options dumped for you to vote |
| Agent **internally** expands 2–5 schemes, gates them, keeps **one** champion | Mid-fission “which do you prefer?” |
| **Goal Contract** written from your answers (no confirm card spam) | “Are you happy?” before anything shipped |
| **Satisfied card only after execute** (regression) | Satisfaction glued to the first swipe deck |

---

## Why this exists／为什么要有这个 Skill

Popular interview skills (`grill-me`, `grilling`, Socratic plan interviews) are great at **asking**. Teams still lose time when the agent:

1. Surfaces **many** partial options and asks humans to pick mid-design  
2. Asks **“satisfied?”** before any Optimized Solution is executed  
3. Mixes **macro goal** questions with **micro implementation** votes  
4. Names the flow **Grill**, which confuses product language and SEO

**Question Cards／问题卡** keeps the structured-card UX people already search for (`AskUserQuestion`, `AskQuestion`, `request_user_input`, choice cards) but **reorders the loop**:

```text
Phase 0  First principles (private)     第一性原理拆题
Phase 1  Macro cards only               只出宏观承重卡
         → Agent writes Goal Contract   → 自写目标契约（不问满意）
Phase 2  Multi-scheme fission (private) 内裂变 2–5 案 → 唯一最优
         → Deliver + EXECUTE            → 交付并执行
Phase 3  Regression satisfied card      做完再问满不满意
```

**Hard timing／硬时序:** 「满不满意」**禁止**与阶段1宏观题一并出；只能在答完宏观 → 交唯一最优并**操作执行完** → **回归环**时再出。

---

## SEO / discovery keywords／检索词（请保留）

Use these when searching, starring, or linking this skill:

`question cards` · `问题卡` · `Question Cards` · `agent skill` · `Agent Skills` · `SKILL.md` · `Claude Code skill` · `Cursor skill` · `Codex skill` · `OpenAI Codex` · `Grok Bot skill` · `OpenCode` · `AskUserQuestion` · `AskQuestion` · `request_user_input` · `choice cards` · `choice-cards` · `grill-me` · `grilling` · `grill with docs` · `Socratic interview` · `plan alignment` · `design interview` · `first principles` · `第一性原理` · `Goal Contract` · `目标契约` · `Optimized Solution` · `唯一最优方案` · `最优方案` · `multi-scheme fission` · `多方案裂变` · `recursive planning` · `regression loop` · `回归环` · `decision alignment` · `product discovery` · `spec sharpening` · `bedrock vs inherited assumptions` · `基岩假设` · `agentskills.io` · `npx skills add` · `anthropics/skills` · `terminal skills`

---

## vs grill-me / AskUserQuestion / grilling

| Dimension／维度 | grill-me / grilling (typical) | Question Cards／问题卡 |
| --- | --- | --- |
| Interaction surface | `AskUserQuestion` / `AskQuestion` / `request_user_input` | Same family: **cards** (macro first) |
| Mid-loop options | Often exposes multiple schemes for user pick | **Forbidden** — fission is Agent-private |
| Output shape | Shared understanding / plan text | **Exactly one** Optimized Solution + **execute** |
| “Are you happy?” | Easy to ask early | **Only** post-execution regression |
| Naming | Grill／grill-me | **Question Cards／问题卡** only |
| Companion | — | Lightweight [`choice-cards`](./skills/choice-cards) for pure A/B/C |

Related prior art (inspiration, not forks): [builderio grill-me](https://www.skills.sh/builderio/builder-agent-skills/grill-me), [nicolasgalvez grilling](https://www.skills.sh/nicolasgalvez/skills/grilling), [Anthropic Agent Skills](https://github.com/anthropics/skills), [agentskills.io](https://agentskills.io), Terminal Skills catalogs, Filip Hric’s interactive `SKILL.md` + AskUserQuestion notes.

---

## Install／安装

Compatible with the **Agent Skills** layout (`SKILL.md` + YAML frontmatter) used by Claude Code, Cursor, Codex, and many Grok Bot / OpenCode setups.

### Clone

```bash
git clone https://github.com/StockOnLLC/question-cards.git
cd question-cards
```

### Claude Code

```bash
mkdir -p ~/.claude/skills
cp -R skills/question-cards ~/.claude/skills/question-cards
# optional companion
cp -R skills/choice-cards ~/.claude/skills/choice-cards
# invoke: /question-cards   or ask to “use Question Cards／问题卡”
```

Project-scoped:

```bash
mkdir -p .claude/skills
cp -R skills/question-cards .claude/skills/question-cards
```

### Cursor

```bash
mkdir -p ~/.cursor/skills   # or your agents skills path
cp -R skills/question-cards ~/.cursor/skills/question-cards
```

Or copy into the bot / workspace skill library your Cursor agents already load.

### OpenAI Codex

```bash
mkdir -p ~/.codex/skills
cp -R skills/question-cards ~/.codex/skills/question-cards
```

For interactive picks, Codex users often enable structured input (`request_user_input`); Question Cards still works with prose cards if the tool is off.

### Grok Bot / other Agent Skills hosts

```bash
# example personal skills root
mkdir -p ~/.agents/skills
cp -R skills/question-cards ~/.agents/skills/question-cards
cp -R skills/choice-cards ~/.agents/skills/choice-cards
```

Load skill name **Question Cards** (description triggers on 问题卡 / plan alignment / Goal Contract).

### npx-style catalogs

If you publish via a skills marketplace (`npx skills add …`), point the skill id at `question-cards` in this repo’s `skills/question-cards` folder.

---

## Suite layout／套件目录

```text
question-cards/
├── LICENSE                 # MIT
├── README.md               # this file (SEO + install + comparison)
└── skills/
    ├── question-cards/
    │   └── SKILL.md        # core loop + hard timing
    └── choice-cards/
        └── SKILL.md        # thin A/B/C helper → points here for full alignment
```

| Skill | When to use |
| --- | --- |
| **question-cards** | Plan / design / goal alignment; need one Optimized Solution and execution |
| **choice-cards** | Single lightweight pick only; README points back here for full loops |

---

## Five-step flow／五步流程

### English

1. **Phase 0 — First principles (private)**  
   Surface ask vs **bedrock** vs **inherited** assumptions. Inherited must not sneak into the goal.
2. **Phase 1 — Macro cards only (2–3 load-bearing)**  
   Success (checkable), for whom / not for whom, bedrock constraints, cost of being wrong.  
   **No satisfied card. No “adopt Optimized Solution” card. No Goal-Contract confirm swipe.**
3. **Phase 2 — Agent fission (private)**  
   Expand 2–5 schemes, gate them, keep **one** champion. Write Goal Contract from Phase 1 answers **without asking**. Deliver the unique Optimized Solution and **execute**.
4. **Execute** the champion end-to-end (ship, publish, configure — whatever “done” means in the contract).
5. **Phase 3 — Regression**  
   **Only now** ask satisfied → adopt / re-fission / rewrite Goal Contract until confirmed.

### 中文

1. **阶段 0** 第一性原理拆题（可只展示结论）  
2. **阶段 1** 只出宏观承重卡（2–3 张）。**禁止**与「满不满意」同出；禁止契约确认／采用最优方案卡  
3. **阶段 2** Agent 内扩 2–5 案、过闸门、只留 **唯一最优方案**；根据宏观答案**自写**目标契约；裂变中途禁止摊方案投票  
4. **执行** 该唯一方案直到契约可核对  
5. **回归** 做完后再问满意 → 采用／再裂变／改契约  

---

## Goal Contract template／目标契约模板

Agent writes this **privately** after Phase 1 (no user confirm card):

```markdown
## Goal Contract／目标契约
- Success／成功标准: …
- Scope／non-goals／范围／非目标: …
- Bedrock／基岩: …
- Gates／闸门: …
- Regression／回归环: ask satisfied only after execute
```

---

## Card UX hints／出卡提示（跨工具）

| Host | Structured ask tool (when available) |
| --- | --- |
| Claude Code | `AskUserQuestion` |
| Cursor | `AskQuestion` / `AskUserQuestion` compatible |
| Codex | `request_user_input` (may need interactive flag) |
| Grok Bot | in-chat **Question Cards** / option widgets |

**Phase 1:** 2–3 macro cards per round; recommended option first with `(Recommended)`／`（推荐）` when using choice UIs.  
**Phase 2:** do **not** open a multi-scheme vote.  
**Phase 3:** single satisfied / not-satisfied regression card **after** execution evidence exists.

---

## Example prompts／示例唤起

```text
Use Question Cards／问题卡 to align this launch plan.
用问题卡把这个改版目标问清楚，再给出唯一最优方案并执行。
Don't grill me — run Question Cards with hard timing (satisfied only after ship).
Replace grill-me for this design review; keep AskUserQuestion-style cards but no mid-vote.
```

---

## Who it’s for／适用谁

- Founders / PMs sharpening a **Goal Contract** before build  
- Agent teams replacing noisy `grill-me` mid-votes with **one** Optimized Solution  
- Anyone installing **Claude Code / Cursor / Codex / Grok Bot** skills who still wants card UX (`AskUserQuestion` family)  
- Bilingual EN／ZH product orgs that need the external name **问题卡**

---

## Roadmap-friendly topics／仓库 Topics

`agent-skill` · `question-cards` · `decision` · `first-principles` · `optimized-solution` · `goal-contract` · `choice-cards` · `claude-code` · `cursor` · `codex` · `grill-me` · `askuserquestion` · `grok-bot`

---

## License

MIT © 2026 StockOn — see [LICENSE](LICENSE).

---

## Links

- Skill body: [`skills/question-cards/SKILL.md`](./skills/question-cards/SKILL.md)  
- Companion: [`skills/choice-cards/SKILL.md`](./skills/choice-cards/SKILL.md)  
- Repo: [https://github.com/StockOnLLC/question-cards](https://github.com/StockOnLLC/question-cards)

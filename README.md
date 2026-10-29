# Question Cards／问题卡

**Public Agent Skill** for aligning any plan or design: **macro questions → Agent-internal multi-scheme fission → exactly one Optimized Solution／唯一最优方案 → post-execution regression loop**.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Skill](https://img.shields.io/badge/Agent-Skill-black.svg)](#install)
[![Bilingual](https://img.shields.io/badge/EN%2FZH-bilingual-blue.svg)](#english--中文)

> **External name only:** Question Cards／问题卡. Never call this Grill.

---

## Why this Skill／为什么用

| Pain／痛点 | Fix／解法 |
| --- | --- |
| Agents dump 3–5 half-baked options and ask you to vote | Agent **fissions privately**, returns **one** Optimized Solution |
| Goals stay foggy adjectives | Phase 1 **macro cards only** until success is checkable |
| “Are you happy?” too early | **Satisfied card only after execute** (regression) |
| Skills named Grill／grill-me confuse teams | Canonical name **Question Cards／问题卡** |

**SEO / discovery keywords:** question cards, 问题卡, agent skill, decision alignment, first principles, goal contract, optimized solution, 最优方案, multi-scheme fission, recursive planning, regression loop, choice cards, A/B options, plan alignment, design interview, Claude Code skill, Cursor skill, Codex skill, Grok Bot skill, OpenCode question, AskUserQuestion, first-principles decomposition, bedrock vs inherited assumptions.

---

## English

### Install

```bash
# Clone
git clone https://github.com/StockOnLLC/question-cards.git
cd question-cards

# Cursor / agents that read ~/.agents/skills
mkdir -p ~/.agents/skills
cp -R skills/question-cards ~/.agents/skills/question-cards
# optional lightweight companion
cp -R skills/choice-cards ~/.agents/skills/choice-cards

# Claude Code
mkdir -p ~/.claude/skills
cp -R skills/question-cards ~/.claude/skills/question-cards
```

Or copy `skills/question-cards/SKILL.md` into your bot’s skill library and load **Question Cards**.

### Five-step flow

1. **Phase 0** — First principles (private): surface ask vs bedrock／inherited assumptions  
2. **Phase 1** — Macro cards only (2–3 load-bearing). **No satisfied card here.**  
3. **Phase 2** — Agent expands 2–5 schemes, gates, picks **one** champion — **never** mid-vote the user  
4. **Execute** the unique Optimized Solution  
5. **Regression** — only now ask satisfied → adopt / re-fission / rewrite Goal Contract  

### Suite layout

```
skills/
  question-cards/SKILL.md   # core: macro → fission → unique Optimized Solution → regression
  choice-cards/SKILL.md     # lightweight A/B/C single pick; points here for full alignment
```

`choice-cards` stays a thin single-pick helper. Full plan/design alignment uses **Question Cards**.

### Goal Contract template

```markdown
## Goal Contract／目标契约
- Success／成功标准: …
- Scope／non-goals／范围／非目标: …
- Bedrock／基岩: …
- Gates／闸门: …
- Regression／回归环: ask satisfied only after execute
```

---

## 中文

### 安装

```bash
git clone https://github.com/StockOnLLC/question-cards.git
cd question-cards
mkdir -p ~/.agents/skills ~/.claude/skills
cp -R skills/question-cards ~/.agents/skills/question-cards
cp -R skills/question-cards ~/.claude/skills/question-cards
# 可选
cp -R skills/choice-cards ~/.agents/skills/choice-cards
```

### 五步流程

1. **阶段 0** 第一性原理拆题（可只展示结论）  
2. **阶段 1** 只出宏观承重卡（2–3 张）。**禁止**与「满不满意」同出  
3. **阶段 2** Agent 内扩 2–5 案、过闸门、只留 **唯一最优方案**；裂变中途禁止摊方案投票  
4. **执行** 该唯一方案  
5. **回归** 做完后再问满意 → 采用／再裂变／改契约  

### 套件目录

- `skills/question-cards` — 问题对齐＋内裂变＋唯一最优＋回归环  
- `skills/choice-cards` — 轻量单选；完整对齐请用本仓 Question Cards  

---

## License

MIT © 2026 StockOn — see [LICENSE](LICENSE).

## Topics

`agent-skill` · `question-cards` · `问题卡` · `decision` · `first-principles` · `optimized-solution` · `goal-contract` · `choice-cards` · `claude-code` · `cursor` · `grok-bot`

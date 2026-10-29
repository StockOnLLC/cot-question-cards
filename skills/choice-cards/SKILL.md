---
name: choice-cards
description: >-
  Lightweight A/B/C option cards for a single pick. For plan/design alignment
  with a decision tree, use Question Cards（问题卡） / CoT Question Cards instead.
---
# choice-cards

**Prefer [CoT Question Cards / Question Cards](../question-cards/SKILL.md)（问题卡）** whenever you are aligning a plan or design through multiple decisions.

Use this skill only for a **one-off** pick (2–4 options, no decision tree).

## Rules

1. One question per turn (or swipe steps if several independent one-offs).
2. Short option titles; put a **long** subtitle in `description`（选这个等于什么／会怎样，至少一句完整后果；禁止口号词）.
3. Do not prefix labels with `A｜` when the host already shows letters.
4. Color marks define meaning only（不限个数／配比）: 🟢 best／推荐 (`primary`), 🟡 ok／可接受, 🔴 risky／不建议 (`danger`), 🔵 need more detail → explain then re-ask. Same question may have multiple 🟢.
5. Do **not** number questions with `①` `②` `③` or Q1（美观）.
6. Do **not** put `❓` `❗` `🚨` (or similar) before the question text.
7. If the host has Something else / `allowCustom`, do **not** add a duplicate「我自己写」option.
8. Grok Bot: **must** `type:widget`（never markdown bullets as fake cards）. Claude: `AskUserQuestion`. Cursor: `AskQuestion`. Codex: `request_user_input`. OpenCode: `question`. Gemini: `ask_user`. CoTree: use target host primitive. Fallback text only when primitive missing, and label it 非可点.
9. Grok mobile title-only／blank options = client bug; ask desktop or typed reply — do not fake buttons in text.

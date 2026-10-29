---
name: choice-cards
description: >-
  Lightweight A/B/C option cards for a single pick. For plan or design alignment
  with a decision tree, use Question Cards (skills/question-cards) instead.
---
# choice-cards

**Prefer [Question Cards](../question-cards/SKILL.md)** whenever you are aligning a plan or design through multiple decisions.

Use this skill only for a **one-off** pick (2–4 options, no decision tree).

## Rules

1. One question per turn (or swipe steps if several independent one-offs).
2. Short option titles; put detail in `description`.
3. Do not prefix labels with `A｜` when the host already shows letters.
4. Color marks: 🟢 best first (`primary`), 🟡 ok, 🔴 risky (`danger`), 🔵 need more detail → explain then re-ask.
5. If the host has Something else / `allowCustom`, do **not** add a duplicate "I'll write it" option.
6. Grok Bot: widget. Claude: AskUserQuestion. Codex / CoTree / other: plain text with the same marks.

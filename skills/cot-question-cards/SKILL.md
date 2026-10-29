---
name: cot-question-cards
description: >-
  Compatibility alias for CoT Question Cards V2. Prefer skills/question-cards
  (frontmatter name: question-cards). V2 Master Loop: fuzzy goal + samples →
  concrete macros → agent fission → micro structure → satisfied loop
  (unsatisfied → re-macro → micro).
---
# cot-question-cards (compat alias)

**Canonical skill:** [`../question-cards/SKILL.md`](../question-cards/SKILL.md)

**English product name:** CoT Question Cards  
**Chinese product name:** 闪电问  
**Skill id (canonical):** `question-cards`  
**Version:** V2（糊目标＋样本 → 具象宏观 → Agent 内裂变 → 微观结构 → 满意循环）

This folder exists so older paths and `npx skills add …/skills/cot-question-cards` still resolve.
**New installs must copy `skills/question-cards`** (folder name = frontmatter `name: question-cards`).

Load and obey the full V2 Master Loop in the canonical skill. Do not duplicate the loop here.

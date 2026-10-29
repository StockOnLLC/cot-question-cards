---
name: question-cards
description: >-
  Use when aligning a plan or design through Question Cards／问题卡: bilingual EN+ZH
  — fuzzy goal + samples/research first, then concrete macros, agent fission,
  micro structure cards, then satisfied loop (unsatisfied → re-macro → micro).
  Color marks define meaning only (multiple greens OK); never number questions.
---
# Question Cards／问题卡

**English product name:** CoT Question Cards (repo `StockOnLLC/cot-question-cards`).  
**Chinese product name (appendix):** 闪电问.  
**Skill id / folder:** `question-cards` (compat alias `cot-question-cards`).  
**External name only:** Question Cards／问题卡. Never call this Grill.

## Master loop／总循环（Deon 2026-10-29 V2）

Must follow／必须按序:

1. **糊目标＋样本／调研**（第一轮）— rough effect + samples or research analogs  
2. **具象宏观** — cover aspects (product surface, cadence, granularity, scope, bedrock…)  
3. **Agent 内裂变自测** — combine variants, test effects, pick one champion draft  
4. **微观结构卡** — refine the champion with user on load-bearing micro structure  
5. **满意卡** — if unsatisfied → back to **更宏观** re-ask → micro again → loop until fully satisfied  

Plain／白话: 先糊 → 样本或调研 → 面面宏观 → 自己裂变测 → 再问微观 → 满意；不满就宏观重问再微观，轮询到满意。

**Hard rules still in force／仍硬:**

- 满意卡 **never** mixed into the first fuzzy／macro decks；它只出现在「有产出之后」  
- 裂变中途 **禁止** 拿半成品多方案让用户投票（裂变＝Agent 内；微观卡＝裂变出冠军草案之后）  
- Cards follow **user language**；Skill body EN+ZH  
- 题目前 **不加** `①` `②` `③`／Q1（美观）  
- 题目前 **禁止** `❓` `❗` `🚨` 等问号／警示 emoji（只写问题句）  
- 🟢🟡🔴🔵 **只定义含义，不限个数／配比**（可三绿）  
- Grok **必须**原生 `type:widget`；**禁止**用 markdown 子弹冒充可点卡

---

## Phase F · Fuzzy goal + samples／阶段 F · 糊目标＋样本（always first／永远第一轮）

**Aim:** Lock a *rough* effect — “大概在做什么／想达到什么感觉”，不要一上来就拆模块。

### Always ask／必问

- Rough success feeling（可含糊，但要能复述）／大致想达到什么效果  
- **Samples／具象样本:**
  - 用户有没有类似工具／产品／流程可参照？  
  - **或** Agent 先调研类似物，整理候选让用户选（可同一轮出「我有样本」vs「你去调研」）

### Research fork／调研叉

If the fuzzy goal mixes multiple tool-kinds（例：多 Agent 前端 + 设计后端内核）→ **research before** dense macros:

1. Agent researches public analogs（短列表＋各一句差异）  
2. Card: user picks which analogs to lean on（可多绿）  
3. Only then enter Phase 1 concrete macros  

If user already pasted samples → skip research；carry samples into Phase 1.

### Forbidden in Phase F／阶段 F 禁止

- 满意卡  
- 细到 API／组件／颜色 token  
- 假装糊目标已经是验收标准  

After F answers: Agent privately writes a **Fuzzy Brief／糊目标简报**（1 小段 + samples／analogs 列表），**不出确认卡**，进入 Phase 1。

---

## Phase 1 · Concrete macros／阶段 1 · 具象宏观

**Aim:** 把糊目标问到「面面都盖到」——前端／交互、周期性／节奏、目标颗粒度、为谁／不为谁、硬约束、做错代价等。有缺口才问。

Round size: **2–5** load-bearing cards（可左右滑）。Clear＝可执行核对 + 无阻塞模糊；否则只在模糊枝再扩。

**Do not ask yet／此时仍不问:** 微观实现细节（具体组件树、字段名）— 留给 Phase 3。

After all Phase 1 answers: Agent privately writes **Goal Contract／目标契约**（成功标准／范围／基岩／闸门／参照样本），**无用户确认卡** → Phase 2。

---

## Phase 2 · Agent fission／阶段 2 · Agent 内裂变自测（不问用户）

From Goal Contract + samples:

1. Seeds ≤3 → expand **2–5** schemes（一次改一类杠杆）  
2. Each scheme: How／Fail-rollback／Fit／Risk／Lever  
3. **Self-test** combinations／effects against gates（能跑通的留下）  
4. Pick **one champion draft**（唯一草案）  

**Forbidden:** mid-fission “你更喜欢 A 还是 B？”；禁止甩 2–5 个半成品给用户多选。

Output: **Champion Draft／冠军草案**（还不是最终收尾）→ Phase 3。

---

## Phase 3 · Micro structure／阶段 3 · 微观结构（对用户出卡）

Only **after** a Champion Draft exists. Ask load-bearing micro structure that changes the draft（例：信息架构块、节奏触发、颗粒度档、关键状态机）— **≤3 cards／轮**；清晰即停。

Not preference-voting random cosmetics. If micro answers contradict Goal Contract → 🔴 jump back to Phase 1 macros.

After micro answers: Agent **revises** champion → produce **Optimized Solution／最优方案（唯一项）** and **execute／落地** what can be shipped now → Phase S.

---

## Phase S · Satisfied loop／阶段 S · 满意循环（最后才出）

Only after Optimized Solution is delivered／executed:

- 🟢 满意，采用并收尾  
- 🟡 不满意——请说具体哪里不对 → Agent 回到 **Phase 1 更宏观** 再问 → Phase 2 → Phase 3 → 再满意  
- 🔴 宏观写错／样本选错 → 回 Phase F 或 Phase 1  
- 🔵 要扩充  

**Loop until fully satisfied.** Never assume done without this card. Two unsatisfied rounds that are actually fuzzy-goal wrong → force Phase F.

---

## Card delivery／卡片交付

### Copy／文案

- Detailed question; option **labels** stay short（一行可点）  
- Option **subtitles／副标** must be long enough to answer「选这个等于什么／会怎样」——至少一句完整后果或边界，禁止只剩口号词  
- On Grok: put the long subtitle in each option's `description`（宿主显示在 label 下）  
- **No question numbering**（禁止 `①` `②` `③`、第一题／Q1）  
- **No leading question-mark emoji**（禁止题目前 `❓` `❗` `🚨`）  
- User language only on cards  

### Options／色义（只定含义，不限配比）

| Mark | Meaning |
| --- | --- |
| 🟢 | Best／推荐／可放心选 |
| 🟡 | Acceptable／可以做／有代价但可接受 |
| 🔴 | Risky／不建议／偏重或有风险 |
| 🔵 | Need expand／先深入解释，再给更多题 |

同一题可多个🟢；禁止「必须一绿一黄一红」。Usually 3–5 substance + 🔵 when useful + host `allowCustom`. No `A｜` in labels.

### Multi-Q／多题

Prefer swipe `steps`. Keep Phase F／1／3／S in **separate decks／turns** — 不要把满意卡塞进糊目标或宏观滑组。

### Platforms／平台

**Hard UX／硬交互**

- 题目前 **禁止** `❓` `❗` `🚨` 等问号／警示 emoji（只写问题句）。  
- Grok Bot **必须** `SendToUser type:widget`（`prompt` + `options`；🟢→`style:primary`；🔴→`style:danger`；`allowCustom`）。**禁止**用 markdown 子弹冒充可点卡。  
- 电脑与手机 **同一套** widget API；无「手机另一套调用」。  
- 外频道（Slack 等）无 widget → 编号列表 + 请用户回选项原文（诚实降级，不叫「卡」）。

| Host | Primitive／原语 |
| --- | --- |
| Grok Bot（in-app 桌面） | `type:widget`；多题 `steps`／分条；`allowCustom` |
| Grok Bot（iOS／Android） | **同一** widget API；若只有标题条、选项体空白＝**客户端渲染 bug**（勿改 markdown）→ 请用户改桌面打开同一聊，或打字回选项原文 |
| Claude Code | `AskUserQuestion` |
| Cursor | `AskQuestion`（会话有则必须用） |
| Codex | `request_user_input` |
| OpenCode | `question` |
| Gemini CLI | `ask_user` |
| CoTree | 装进目标宿主后用**该宿主**原语（CoTree 本身不出卡） |
| 其他／原语缺失 | text card（色标）+ 明确写「非可点」 |

### “You decide／随便”

Phase F／1 → take a current 🟢. Phase S → adopt／close.

---

## End artifact／结束物

```markdown
## Fuzzy Brief／糊目标简报
- Rough effect: …
- Samples／analogs: …

## Goal Contract／目标契约
- Success／Scope／Bedrock／Gates: …

## Optimized Solution／最优方案（唯一项）
…

## Internal bake-off／比选摘要
- Variants: N; Passed: M; Winner: …

## Micro refinements／微观修订
…

## Execution／执行记录
→ What shipped: …

## Regression／满意循环
→ Satisfied close | Feedback → re-macro round k
```

---

## vs old V1 timing／相对旧版

| Old V1 | V2 |
| --- | --- |
| Start at dense macros | Start at **fuzzy + samples／research** |
| Micro never asked | Micro asked **after** champion draft |
| Satisfied only post-execute once | Satisfied **loops**：不满 → 宏观重问 → 微观 → 再满意 |
| No explicit research fork | Research when fuzzy goal mixes tool-kinds |

Color／no-numbering rules from the same day stay.

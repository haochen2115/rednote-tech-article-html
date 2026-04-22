# Voice Guide — Calm Academic Tone

This is the most important reference in the skill. The visual design will fail if the copy is promotional. A reader in the target audience (AI/ML engineers, researchers) reacts strongly to "oily" copy — it makes the whole post feel like content marketing even when the underlying analysis is good.

## The core principle

**Describe, don't sell.** The reader is your peer, not your audience. You are not trying to make them feel anything. You are trying to help them understand something. If the content is genuinely interesting, the prose doesn't need to announce that.

A useful mental model: write as if the reader is one of your senior colleagues who already respects your technical judgment. You wouldn't slap "SHOCKING FINDING" on a Slack message to them. The HTML card should read the same way.

## Rhetorical moves to avoid

### 1. Count-based teasers

The pattern of "N个X" where the count is the hook.

| Oily | Calm |
|---|---|
| 六个反常识 | 机制与边界 |
| 三个你必须知道的 trick | 三种常见策略 |
| 五个细节 | 几个细节 / 主要细节 |
| 十条 insight | (just drop the count) |

The count framing implies the value is in the enumeration itself, which is the Medium-article / listicle move. Academic writing counts when counting is substantive ("three conditions are necessary") and avoids it when it's just packaging.

### 2. Reader-directed commands

Telling the reader what to do, feel, or believe.

| Oily | Calm |
|---|---|
| 如果只能记住三件事 | 整体观察 / Summary |
| 必读 / 一定要看 | (remove entirely) |
| 彻底改变 X | (describe what changes, without "彻底") |
| 你肯定想不到 | (describe what happened) |
| 看完之后你会 | (describe the content instead) |
| 看完这篇就够了 | (remove; sounds desperate) |

### 3. Self-promoting framing of the content

Describing findings as if they're inherently surprising to justify reading on.

| Oily | Calm |
|---|---|
| 最颠覆认知的发现 | (just state the finding) |
| 最深的洞察 | (just state it) |
| 反直觉的结果是 | 实验结果显示 |
| 震惊！/ 意外的是 | (usually can be deleted) |
| 最关键的一点 | 核心机制 / 主要条件 |

### 4. Action-bait language

Words that read as "sales copy."

| Oily | Calm |
|---|---|
| 可以直接抄的 recipe | 两种干预策略 / 两个 recipe |
| 救场 / 救命 | 修复 / 缓解 |
| 神器 / 骚操作 | (describe the technique) |
| 吊打 / 秒杀 | 优于 / 显著超过 |
| 香爆了 / 绝了 | (remove) |
| 冲！/ 速看 | (remove) |

### 5. Rhetorical questions aimed at the reader

| Oily | Calm |
|---|---|
| 你有没有想过 X？ | 关于 X，有一个常见问题 |
| 到底 X 还是 Y？ | X 与 Y 的对比 |
| 为什么 X 这么重要？ | X 的作用是 |

Rhetorical questions in titles are OK when they're genuine — i.e., when the answer is non-obvious and the post actually explores it. They're not OK when they're hooks with predetermined answers.

## Punctuation and emphasis

- **Exclamation marks** — default to zero. One or two can appear in dialog or quoted reactions; none should appear in titles or body prose.
- **Bold** — reserve for terms being introduced, proper nouns in claims, and numerical results. Don't bold entire clauses for emphasis.
- **Emoji** — avoid in titles entirely. In body, use only as category markers in small text (📄 for paper citations, 📊 for data points) where they function like icons rather than expression.
- **Ellipsis (...)** — avoid. They read as uncertain or coy. State things directly.
- **Em dashes** — use freely for parenthetical clauses, especially in English terms embedded in Chinese prose ("per-token advantage — 即使在 deep prefix 上").

## Sentence structure

**Prefer declarative statements over claim-plus-explanation.** When you write "X is important because Y," the "important" is usually redundant. Just explain Y, and importance is implicit.

Example:

- Oily: "Teacher 的选择非常关键，因为它直接决定了蒸馏效果。"
- Calm: "Teacher 的选择决定蒸馏效果。"

**Prefer passive or impersonal constructions for empirical claims.** Not because passive voice is better in general, but because it signals scientific register.

- Oily: "我们发现 Teacher scale 不 transfer，让人很意外！"
- Calm: "实验显示 teacher scale 不 transfer。"

**English terms are fine** when they're standard in the field (OPD, RL, KL, logit, rollout, pipeline, overlap, teacher/student). Don't translate these into Chinese — the target audience reads them as English. But do translate truly general terms (不要写 "capability" when "能力" is fine).

## The title-label system

This skill uses a specific pattern for card labels and titles that avoids most oiliness issues.

**Card labels** are short English or Chinese category markers, not teasers:

✓ `Phenomenology` / `Mechanism` / `Token-Level Mechanism` / `Length Limit` / `Local Geometry` / `Recipes`
✓ `现象` / `机制` / `局限` / `缓解`
✗ `震撼发现` / `最重要的一点` / `别忽略`

**Card titles** are declarative statements of what the card is about, not questions aimed at the reader:

✓ "Benchmark 分数不能预测蒸馏效果"
✓ "优化信号集中在 overlap tokens 上"
✓ "长序列上的失效模式"

✗ "你知道 Benchmark 其实没用吗？"
✗ "为什么 97% 的 token 才是关键？"
✗ "长序列蒸馏翻车了怎么办？"

## Tone calibration for different content types

### Paper notes
Most formal. English technical terms preserved. Citations like "§3.3" and "arXiv:..." included. Summary card is observational ("整体观察" not "结论").

### Concept explainers
Slightly warmer. Can use analogies and comparisons more freely. Still avoids "你" second-person and action-bait framing.

### Industry observations
Formal register. Include dates, sources, measurable claims. Avoid speculation framed as insight ("the real reason X is happening" is usually speculation; "one factor is X" is honest). When describing trajectories, prefer past-and-present observations over predictions.

## Common repair patterns

When reviewing a draft, look for these patterns and replace:

1. **Any title starting with a number** ("6个 X", "3 种 Y") → rewrite to lead with what the cards are *about*
2. **Any summary card titled "三句话总结" / "如果只能记住"** → rewrite to "整体观察" / "Summary" / "Key points"
3. **Any card label containing emotional vocabulary** (反常识, 颠覆, 最深) → rewrite to neutral technical vocabulary
4. **Any "工程含义" or "操作建议" label that uses command verbs** ("你应该", "必须") → rewrite as a statement about what the finding implies
5. **Any closing italic line that tries to motivate** ("去试试吧！") → rewrite as observational ("这一框架下 X 比 Y 更关键") or remove

## Self-check questions

Before finalizing, read the draft with these questions:

1. Would a senior technical colleague find this embarrassing to receive as a Slack link? If yes, it's too oily.
2. Are any card titles trying to hook rather than describe? Rewrite them.
3. Does any bolded phrase need the bold, or am I just trying to look emphatic?
4. Is the summary card observing or preaching? Observation only.
5. If I removed every adjective about "how important" something is, would the content still work? If yes, remove them.

The target is: a reader skims the cards, thinks "oh that's a clean summary of the finding," and saves it. Not: "oh what a hype post."

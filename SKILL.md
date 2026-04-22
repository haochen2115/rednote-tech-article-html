---
name: rednote-tech-article-html
description: Create visually refined single-file HTML cards for technical content — paper deep-dives, concept explainers, and industry observations — in a calm, academic-notebook aesthetic. Use this skill whenever the user wants to make a 小红书 / RedNote / Xiaohongshu post about a paper, an AI/ML concept, or a technical topic, or when they ask for an "HTML card" / "技术卡片" / "小红书配图" / "paper reading notes" in card form. Produces mobile-width (420px) layouts with warm paper background, Noto Serif SC headings, four-color semantic labels, and structured evidence/insight/takeaway components — explicitly avoiding the generic "AI tech card" look (gradient purple, neon cyan, heavy emoji, clickbait copy).
---

# RedNote Tech Article HTML

Create visually refined single-file HTML cards for technical content in a calm, academic-notebook aesthetic. The output is designed for screenshotting at mobile width (420px) to publish on RedNote / 小红书 or similar platforms.

## What this skill is for

This skill targets technically literate readers — researchers, engineers, grad students. The aesthetic signals "I read this carefully and thought about it" rather than "I'm hyping this for engagement." Three content types this skill supports:

1. **Paper deep-dive notes** (精读笔记) — structured takes on a specific paper, with citations and evidence blocks
2. **Technical concept explainers** — original-vs-variant comparisons, principle breakdowns, framework introductions
3. **Industry observations** — trend analysis, benchmark roundups, ecosystem commentary

It is NOT for: marketing copy, listicles aimed at general audiences, lifestyle content, or anything where the goal is clickbait optimization. If the user's request leans toward those, this skill is the wrong choice.

## The core aesthetic (read this first)

The single most important thing: **this design fights against the generic "AI tech card" look**. That look has:

- Dark gradients (purple-to-blue, cyan neon accents)
- Heavy emoji usage in titles (🚀💡🔥)
- Clickbait headlines ("震撼！")
- Glassmorphism / excessive blur effects
- Stock-photo feel

Instead, this skill produces:

- **Warm paper background** (#f5f0e8, the color of aged book paper)
- **Serif headings** in Noto Serif SC, clearly distinct from body sans-serif
- **Four muted semantic colors** (brick red, forest green, navy blue, dark gold) used as small labels, not dominant fills
- **One dark card at the end** for the summary — the only dark element in the whole layout, which makes it feel like a closing statement rather than a hook
- **Monospace only for evidence blocks and formulas** — technical precision markers, not decoration

The result reads like a well-designed paper notebook or a Markdown-rendered academic blog, not a social media graphic.

This skill intentionally supports **only one visual style** (warm paper). If a user asks for a dark/neon/glassmorphism variant, explain that this skill is specifically tuned for the paper aesthetic and suggest they use a different tool for that.

## Voice: calm and declarative, not promotional

The visual design fails completely if paired with promotional copy. Always consult `references/voice-guide.md` before writing the text — this is non-negotiable because the failure mode here is subtle (the text *looks* fine to a general reader but feels "oily" / 油腻 to the target audience).

Key principle: **state what is, do not tell the reader what to feel or do**.

| Avoid | Prefer |
|---|---|
| "六个反常识" | "机制与边界" |
| "彻底改变你的认知" | "关于何时有效、何时失效" |
| "如果只能记住三件事" | "整体观察" / "Summary" |
| "可以直接抄的 recipe" | "两个缓解策略" |
| "救场" | "干预方式" |
| "最颠覆认知的发现" | — (just describe the finding) |
| "必须" / "一定要" | "通常" / "可以考虑" |
| exclamation marks | periods |

If you find yourself writing copy that would fit in a mobile-game ad, stop and rewrite. See `references/voice-guide.md` for full guidance.

## Workflow

1. **Understand the content first.** Before writing any HTML, make sure the technical substance is solid. If the user is asking you to turn a conversation into a card, extract the actual claims, evidence, and structure from that conversation. Don't invent data.

2. **Read the references.** Always consult:
   - `references/design-system.md` — colors, typography, spacing, component CSS
   - `references/voice-guide.md` — copy principles and phrase-level dos/don'ts

3. **Start from the template.** Copy `assets/template.html` and modify it. Do not generate HTML from scratch — the template encodes many small decisions (font imports, CSS variables, responsive tweaks) that are tedious to reproduce correctly.

4. **Choose components, not colors.** The design has a small set of semantic components (evidence block, insight box, takeaway box, compare columns, etc.). Pick components based on what the content *is*, not based on visual variety. See `references/design-system.md` for the component catalog.

5. **Default to 5-7 content cards plus one dark summary card.** Fewer cards for short content, never more than 8 (at that point the reader tunes out). Each card gets exactly one semantic label color — don't rainbow them.

6. **Save the final HTML** to `/mnt/user-data/outputs/` with a descriptive filename (e.g., `opd_notes.html`, not `card.html`), then present it.

## Structural conventions

**Header**
- Small uppercase tag (e.g., "Paper Notes · 精读笔记")
- H1 title in serif, two lines, with the second line in accent red
- One-line subtitle in muted gray
- Optional arxiv ID / date / source in monospace blue

**Content cards** (5-7 of them)
- Each has: card number (decorative, large serif, low opacity top-right), color label (one of red/green/blue/gold), serif H2 title, body prose, and one or two structured components

**Final dark card (summary)**
- Gradient dark background (near-black)
- Serif H2
- Three numbered points using the `.hl` highlight span
- Optional italic closing line at reduced opacity — observational, not motivational

**Tags and footer**
- Small gray pills for topic tags
- Footer with source citation and signature line

## Component selection guide

| If the content is... | Use... |
|---|---|
| A quoted experimental result with numbers | `.evidence` block (monospace, gray background) |
| A key takeaway or interpretation | `.insight` box (left-border accent, cream background) |
| A practical implication from a finding | `.takeaway` box (gold left-border, "应用" label) |
| Two sides of a contrast (A vs B) | `.compare` columns (red left, green right) |
| A mathematical definition | `.formula` box (dashed gold border, monospace) |
| A percentage / ratio worth visualizing | `.ratio-viz` horizontal bar |
| A sweet-spot / curve pattern | `.length-viz` small bar chart |
| Two or three options / strategies | `.dir-box` rows (green/yellow/red by valence) |

If a component doesn't fit, prefer plain prose over inventing new visuals. Restraint is part of the aesthetic.

## Content-type specific guidance

**Paper deep-dives (精读笔记):**
- Lead with phenomenon or core finding (red card)
- Follow with mechanism (green)
- Include at least one evidence block with section reference (§X.X) and numbers
- Most formal voice register — preserve English technical terms

**Technical concept explainers:**
- Often built around a contrast or decomposition
- `.compare` columns are especially useful here
- Can use analogies more freely than in paper notes
- Still avoids second-person "你" and action-bait framing

**Industry observations / trend analysis:**
- Lead with a measurable claim or benchmark result
- Include dates and sources in every evidence block
- Avoid speculation framed as insight ("the real reason X is happening" is speculation; "one factor is X" is honest)
- Summary card should synthesize trajectories, not predict futures

## Common failure modes

**Too much color.** Using all four label colors in one post feels cluttered. Pick 2-3 per post. Red is the "opening" / warning color, green is "mechanism" / resolution, blue is "technical" / measurement, gold is "insight" / emphasis. Use them semantically.

**Over-formatting the body.** Don't bold every third word. Bold is for genuine emphasis — terms being introduced, key nouns in a claim. Most body text should be unbolded.

**Inventing numbers.** If the user didn't provide specific numbers from the source, don't make them up to fill evidence blocks. Use the evidence block for qualitative observations or skip it.

**Using the dark summary for early cards.** The dark card is load-bearing — it signals "we're done, here's the synthesis." If you put dark cards mid-flow, the summary card loses its punch.

**Emoji in titles.** Don't. The subtitle and a few specific places (e.g., `📄` / `📊` in evidence block labels) are fine because they function as category markers, but titles stay clean.

**Generating a skill-less fallback.** If the user asks for a "technical HTML card" and this skill is available, use it. Do not fall back to a generic Tailwind/gradient design because that will produce exactly the look this skill exists to avoid.

## Output format

Single self-contained HTML file, no external assets beyond Google Fonts (which is loaded via `<link>` in the template). The file renders correctly when opened directly in a browser at mobile width. Users will typically screenshot sections of it to post — so each card should look complete when cropped individually.

## Additional references

- `references/design-system.md` — full design token reference and component CSS
- `references/voice-guide.md` — copy principles, phrase-level guidance, before/after examples
- `assets/template.html` — starting point for new cards
- `assets/components.html` — every component rendered in isolation, useful for visual reference

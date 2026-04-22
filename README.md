# rednote-tech-article-html

A Claude skill for producing visually refined HTML cards for technical content — paper deep-dives, concept explainers, and industry observations — in a calm academic-notebook aesthetic.

![skill category](https://img.shields.io/badge/skill-design-c23b22) ![platform](https://img.shields.io/badge/platform-Claude.ai-1a5276) ![language](https://img.shields.io/badge/content-zh%2Fen-2d5a27) ![style](https://img.shields.io/badge/style-warm%20paper-b8860b)

## What it does

Turn technical conversations, papers, or trend analyses into mobile-width (420px) HTML cards suitable for screenshotting and posting to 小红书 / RedNote or similar platforms.

The output is designed to read like a well-designed paper notebook or academic blog, **not** like a social-media graphic.

## What it fights against

The generic "AI tech card" look that most LLMs default to produces:

- Dark purple-to-cyan gradients
- Heavy emoji usage in titles (🚀💡🔥)
- Clickbait headlines ("六个你必须知道的...")
- Glassmorphism, excessive blur, neon accents
- Promotional copy tone ("彻底改变", "可以直接抄", "救场")

This skill produces the opposite:

- Warm paper background (#f5f0e8), Noto Serif SC headings
- Four muted semantic colors used as small labels
- Declarative, observational copy — written for technical peers
- A single dark card at the end as the summary, everything else on paper

## Why only one style?

This skill ships with **exactly one visual theme** — warm paper. This is deliberate. The skill's value is not flexibility but *opinionated consistency*: every decision (color, typography, spacing, component vocabulary) is tuned for this specific aesthetic.

If you want a different look (dark mode, neon, editorial magazine, etc.), fork the skill and modify. Don't bolt variants onto this one.

## Design sample

A card post made with this skill typically looks like:

```
[ Header with serif H1 and small uppercase category tag ]

[ Card 01 · red label · "Phenomenology" ]
  declarative title
  body prose
  evidence block (monospace)
  insight box (cream, left-border accent)

[ Card 02 · green label · "Mechanism" ]
  ...

[ Card 03 · blue label · "Token-Level Detail" ]
  ...

[ Dark summary card — the only dark element ]
  three observational points

[ tag pills, footer citation ]
```

## Installation

### For Claude.ai

Download the `.skill` file from releases and upload it via the skills interface.

### For Claude Code

Clone this repo into your skills directory:

```bash
git clone https://github.com/haochen2115/rednote-tech-article-html.git ~/.claude/skills/rednote-tech-article-html
```

### For manual inspection

Just browse the repo. Each file is designed to be readable on its own:

- `SKILL.md` — main skill instructions
- `references/design-system.md` — colors, typography, component catalog
- `references/voice-guide.md` — copy principles (this is the most important one)
- `assets/template.html` — starting point for new cards
- `assets/components.html` — every component rendered in isolation

## Usage

Once the skill is installed, trigger it by asking Claude to produce a card-style HTML post for technical content:

- "把我们刚才聊的 OPD 做成一个小红书 HTML"
- "turn this paper summary into a card-style HTML post"
- "给我做一个关于 [X] 的技术卡片"

The skill will:

1. Read the references (design system, voice guide)
2. Extract technical substance from the conversation or source
3. Choose appropriate semantic components (evidence blocks, insight boxes, compare columns)
4. Produce a single-file HTML with embedded CSS and Google Fonts
5. Save to outputs for preview

## When to use it

Good fits:

- Paper reading notes (精读笔记) for AI/ML/systems papers
- Technical concept explainers — contrasts, principle breakdowns, framework introductions
- Industry observations — trend analysis, benchmark roundups, ecosystem commentary

Bad fits:

- Marketing copy or product announcements
- General-audience explainers aimed at non-technical readers
- Lifestyle content or reviews
- Anything where engagement-optimization is the goal

If you want clickbait, this skill is the wrong choice.

## Design philosophy

Three principles the whole skill tries to encode:

### 1. Paper over screen

The warm off-white background (#f5f0e8) and serif headings make the design feel like a physical notebook page. Readers treat it differently than a typical social-media card — less "scroll past," more "read carefully."

### 2. Restraint signals confidence

The four-color palette is muted on purpose. Using all four colors in one post feels cluttered; picking 2-3 with one dominant feels composed. This is the opposite of the "more color means more value" instinct that most card designs fall into.

### 3. Voice is load-bearing

The visual design fails completely if paired with promotional copy. A single "震撼" in a title can make the whole post feel like an ad even when the aesthetic is otherwise clean. `references/voice-guide.md` enumerates specific phrases to avoid and why.

## Customization

If you want a variant, the cleanest path is to fork and edit `assets/template.html`. Keep the structural components (evidence block, insight box, dark summary card) intact — they're what give the design its identity.

Do not:

- Add new base colors (the palette is small on purpose)
- Replace Noto Serif SC with a display serif (headings become too loud)
- Add gradient backgrounds to content cards (only the summary card has a gradient)
- Use border-radius > 12px (corners stay "papery")

## License

MIT — use freely, fork freely, no attribution required (but appreciated).

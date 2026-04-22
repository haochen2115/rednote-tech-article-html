# Design System — Tech Paper Card

Complete reference for visual tokens and components. Use this when you need to build a custom variation or verify you're staying consistent with the system.

## Design principles

1. **Paper over screen** — the warm background color (#f5f0e8) and serif headings make the card feel like a physical notebook page rather than a screen UI.
2. **Muted semantic color** — four colors (red, green, blue, gold) are used as small labels and accent borders, never as dominant fills. This is the opposite of the "gradient purple hero section" approach.
3. **Typographic contrast carries hierarchy** — serif for headings, sans for body, monospace for evidence/code. The contrast between these three families does most of the visual work; you rarely need dramatic size or weight differences.
4. **One dark card only** — the final summary card is dark. Everything else is on paper. This gives the summary weight without requiring louder typography.
5. **Mobile-first, screenshot-friendly** — container is fixed at 420px max-width. Each card should look complete when cropped alone, because users screenshot individual cards to post.

## Color tokens

```css
:root {
  --ink: #1a1a1a;         /* primary text */
  --paper: #f5f0e8;       /* page background, warm off-white */
  --accent: #c23b22;      /* brick red */
  --accent2: #2d5a27;     /* forest green */
  --accent3: #1a5276;     /* navy blue */
  --muted: #8c7b6b;       /* muted tan — secondary text */
  --card-bg: #fffdf7;     /* card background, lighter than paper */
  --shadow: rgba(60,40,20,0.12);  /* warm shadow */
  --gold: #b8860b;        /* dark gold */
}
```

### Semantic color usage

| Color | Semantic | When to use |
|---|---|---|
| `--accent` (red) | Phenomenon / warning / limitation | First card, failure modes, things that go against expectation |
| `--accent2` (green) | Mechanism / working / resolution | Explanations of how things work, conditions for success |
| `--accent3` (blue) | Technical / measurement / citation | Token-level details, evidence block headers, citations |
| `--gold` | Insight / synthesis / emphasis | Deep observations, takeaway boxes, the "why" behind a finding |

Don't use all four in one post. Aim for 2-3 colors with one dominant. Typical assignment:
- Paper notes: red (opening/limits), green (mechanism), blue (evidence), gold (insight)
- Concept explainer: red/green pair for contrasts, blue for citations

## Typography

```html
<!-- Load in <head> -->
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+SC:wght@400;700;900&family=Noto+Sans+SC:wght@300;400;500;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
```

| Font | Usage |
|---|---|
| **Noto Serif SC** | H1 (900), H2 (700), card numbers (900) |
| **Noto Sans SC** | Body text (300-400), subtitles (300), labels (500) |
| **JetBrains Mono** | Evidence blocks, formulas, arxiv IDs, numerical data |

The body weight defaults to `300` (light) which gives the prose a thin, readable feel on warm paper. Bold in body = `700`, skipping medium intermediate weights keeps the contrast sharp.

## Layout

```css
.container {
  max-width: 420px;      /* mobile-width, this is deliberate */
  margin: 0 auto;
  padding: 20px 16px 60px;
}
```

Do not change the 420px width. Many design decisions (font sizes, padding, line heights) are tuned for this width. If a user wants a wider version, tell them the aesthetic is specifically tuned for mobile screenshot use.

## Component catalog

### Header

```html
<div class="header">
  <div class="tag">Paper Notes · 精读笔记</div>
  <h1>Main Title Here<br><span class="em">Accent Second Line</span></h1>
  <div class="subtitle">One-line observational subtitle</div>
  <div class="arxiv">arXiv: XXXX.XXXXX · Institution · Year</div>
</div>
```

Used once at the top. The `<br>` between H1 lines is intentional — it forces a visual beat. The accent color applies only to the second line.

### Content card (the workhorse)

```html
<div class="card">
  <div class="card-number">01</div>
  <span class="card-label red">Category Label</span>
  <h2>Card title as a declarative statement</h2>
  <p>Body paragraph. Plain prose, minimal bold.</p>
  <!-- one or two structured components -->
</div>
```

`card-number` is decorative — large serif numeral at top-right with 3.5% opacity. Don't raise the opacity; it should be barely visible.

`card-label` takes one of four classes: `red`, `green`, `blue`, `gold`. The label text is UPPERCASE tracking-wide, max 3 words.

### Evidence block

For quoted experimental data, numerical results, or direct findings from a source.

```html
<div class="evidence">
  <span class="paper">§3.3 · Reverse Distillation</span>
  teacher = R1-Distill-7B → <span class="hot">student 退化至 pre-RL</span><br>
  teacher = R1-Distill-1.5B → <span class="hot">退化路径几乎一致</span><br><br>
  两个 teacher 从 student 视角<br>
  <span class="neutral">distributionally indistinguishable</span>
</div>
```

Classes inside:
- `.paper` — source label (blue, small, not monospace)
- `.hot` — red highlight for negative/warning numbers
- `.good` — green highlight for positive/successful numbers
- `.neutral` — black bold for neutral technical terms

Monospace body inside the block. Use `<br>` for line breaks rather than `<p>` — the block is semantically a quote, not flowing prose.

### Insight box

For interpretations, takeaways, or synthesis of the preceding evidence.

```html
<div class="insight">
  <p>Interpretive statement about what the evidence means.</p>
</div>
```

Optional variants: `.insight.green`, `.insight.blue`, `.insight.gold` — use the color that matches the card's semantic.

### Takeaway box (engineering implications)

For practical implications distinct from interpretation.

```html
<div class="takeaway">
  <strong>Key principle</strong> and practical consequence.
</div>
```

This has a `::before` pseudo-element that automatically displays "应用" as the label. If you want a different label (e.g., "工程含义", "Action"), edit the CSS.

### Compare columns

For two-sided contrasts.

```html
<div class="compare">
  <div class="compare-col left">
    <h4>A · First Side</h4>
    <p>Short description.</p>
  </div>
  <div class="compare-col right">
    <h4>B · Second Side</h4>
    <p>Short description.</p>
  </div>
</div>
```

Left is red-tinted (problematic/before), right is green-tinted (correct/after). If your contrast doesn't have this valence, just use two neutral `<p>` paragraphs instead.

### Direction boxes

For options, strategies, or enumerated approaches.

```html
<div class="dir-box pos">
  <span class="icon">i</span>
  <span class="text"><strong>Strategy name</strong><br>Description of the strategy.</span>
</div>
```

Variants: `.pos` (green, preferred/working), `.cond` (yellow, conditional/caveat), `.neg` (red, avoid).

Icons are text (i, ii, ✓, ✗) in monospace — don't use emoji here.

### Formula box

For mathematical definitions.

```html
<div class="formula">
  GRR = (Acc<sub>after</sub> − Acc<sub>before</sub>) / (Acc<sub>teacher</sub> − Acc<sub>before</sub>)
  <div class="desc">gap recovery rate · brief explanation</div>
</div>
```

Dashed gold border signals "this is a definition." Use sparingly — one per post maximum.

### Ratio visualization

For one-dimensional proportions (e.g., "97% of X").

```html
<div class="ratio-viz">
  <div class="overlap">MAIN CATEGORY · 97%+</div>
  <div class="rest">其他</div>
</div>
```

The flex values inside the CSS (`flex: 97` and `flex: 3`) are the actual ratios. Adjust them to match the real data.

### Length/curve visualization

For showing patterns across a range (sweet spots, curves).

```html
<div class="length-caption">x-axis description</div>
<div class="length-viz">
  <div class="bar weak" style="height:25%"><span class="bar-label">low</span></div>
  <div class="bar best" style="height:90%"><span class="bar-label">best</span></div>
  <div class="bar bad" style="height:35%"><span class="bar-label">bad</span></div>
</div>
```

Heights in percentage map to bar size. Classes: `.weak` (gray, low/marginal), `.best` (green, optimal), `.bad` (red, failure zone).

### Separator

Between cards, a subtle dot pattern:

```html
<div class="sep">· · ·</div>
```

### Dark summary card (verdict)

Used exactly once, at the end.

```html
<div class="verdict">
  <span class="card-label red">Summary</span>
  <h2>整体观察</h2>
  <p><span class="hl">i</span> First key observation.</p>
  <p><span class="hl">ii</span> Second key observation.</p>
  <p><span class="hl">iii</span> Third key observation.</p>
  <p style="margin-top:16px; font-size:12px; opacity:0.5;">
    Optional italic closing line.<br>Observational, not motivational.
  </p>
</div>
```

The `.hl` span gives a red background to the list numeral. The closing line at 50% opacity is for a meta-observation about the topic itself (e.g., "OPD 不是注入，而是重组") — it should not be a call to action.

### Tags and footer

```html
<div class="pills">
  <span class="pill">#Topic1</span>
  <span class="pill">#Topic2</span>
</div>

<div class="footer">
  Source citation · Institution · Year<br>
  Author note · Handle · Date
</div>
```

Tags are for search discoverability on Xiaohongshu. 5-7 tags typical, mixing English technical terms and Chinese keywords.

## Spacing and rhythm

The whole design uses multiples of 4px for spacing. Don't introduce arbitrary values.

- Card to card: `margin-bottom: 16px` on `.card`, separator between
- Inside card: `padding: 28px 24px`
- Paragraph spacing: `margin-bottom: 12px`
- Line height: 1.75 for body, 1.45 for headings

## What not to do

- **Don't add new colors.** The palette is deliberately small. If you need to distinguish something, use structural differences (border-left, background variant) rather than introducing new hues.
- **Don't use CSS gradients for card backgrounds.** The only gradient is the dark summary card's very subtle `#1a1a1a → #2d2d2d`. Anywhere else, solid fills.
- **Don't use box-shadow for drama.** The existing shadow (`0 2px 12px rgba(60,40,20,0.12)`) is warm and subtle. Don't replace it with colored shadows or glow effects.
- **Don't use border-radius above 12px.** The cards feel "papery" partly because the corners are moderate. Large radius makes them feel like app UI.
- **Don't increase font sizes to emphasize.** If something needs more weight, use bold or color, not size. The size hierarchy is already set.

## Testing the output

After rendering, quickly verify:

1. Paper color is warm (if it looks gray, something overrode the CSS)
2. H1 is serif, body is sans — visible contrast
3. Card labels are small and uppercase, not dominating the card
4. Evidence blocks render in monospace
5. Dark summary card is the only dark element, appearing last
6. No emoji in card titles
7. No exclamation marks in body text

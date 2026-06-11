# Fallback Theme

Use this only when `source-style.md` cannot find a project, product, brand, app, docs, or design-system style to inherit. This is the default visual language for unbranded `make-html` artifacts.

The theme should feel like an editorial HTML artifact: paper-like, high contrast, restrained, and built around strong hierarchy, useful examples, and navigable sections. Use a light plum accent instead of orange/clay.

## Tokens

Use these as the starting point, then adjust for the artifact's content:

```css
:root {
  --mh-ivory: #FAF9F5;
  --mh-paper: #FFFFFF;
  --mh-slate: #141413;
  --mh-muted: #67665F;
  --mh-faint: #F0EEE6;
  --mh-line: #D8D4C8;
  --mh-oat: #E3DACC;
  --mh-olive: #788C5D;
  --mh-plum: #A678D6;
  --mh-plum-dark: #7B55B6;
  --mh-plum-soft: rgba(166, 120, 214, 0.16);
  --mh-rust: #A84F3D;
  --mh-serif: ui-serif, Georgia, Cambria, "Times New Roman", Times, serif;
  --mh-sans: ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  --mh-mono: ui-monospace, SFMono-Regular, Menlo, Consolas, "Liberation Mono", monospace;
}
```

Rules:

- Plum is the primary accent for active states, links, key rules, highlight text, selected tabs, and section markers.
- Use olive for positive/safe semantic states and rust only for destructive or removed diff lines.
- Do not use Claude/Anthropic orange, clay, amber, or tan as the primary accent.
- Keep the base mostly ivory, paper, slate, muted gray, and oat borders. Avoid a one-note purple page.

## Page Shape

- Use a centered `.wrap` around 1080-1160px wide with generous side padding.
- Start with a masthead: mono eyebrow, serif H1, short deck, and optional compact meta row.
- Add a table-of-contents row when there are three or more sections. It must use `display:flex; flex-wrap:wrap;` and must not horizontally scroll.
- Structure sections with a small mono index or label, a serif `h2`, and compact supporting copy.
- Use paper cards with 1-2px borders, 10-14px radius, and subtle hover/focus motion only when cards are interactive.
- Prefer visible borders and typographic contrast over gradients or decorative backgrounds.

## Type

- Body: system sans, 15-17px, line-height around 1.55.
- Page H1/H2: serif, medium weight, no negative letter spacing.
- Eyebrows, labels, line numbers, tabs, and file paths: mono, small, uppercase only when useful.
- Inline code: mono with faint background, border, and wrapping for long identifiers.

## Components

Navigation and chips:

- Use pill links/buttons with paper background, slate text, oat border, and plum active/focus state.
- Rows of chips, filters, badges, legends, and segmented controls must wrap.
- Active chips can invert to slate text on paper or paper text on slate; add a plum underline, dot, or border so the state is not only dark fill.
- Active styling must be state-driven: use selectors such as `[aria-current="true"]`, `[aria-pressed="true"]`, `[aria-selected="true"]`, or `.is-active` that JavaScript updates. Do not use `:first-child` as a fake selected state.

Callouts:

- Use paper background, oat border, 10-12px radius, and a 3-4px plum left rule.
- Keep callout headings mono or compact serif, with direct body copy.

Cards:

- Use flat paper surfaces, thin borders, and dense content. Do not nest cards inside cards.
- Use small top labels and compact metadata rows to improve scan speed.

Diagrams:

- Use the same tokens in SVG: slate ink, oat lanes, paper nodes, plum highlights, olive/rust semantic states.
- Keep diagrams lane-based or layered with routed arrows. Do not accept crossing arrows in the fallback theme.

## Code Examples

Code examples are part of the artifact design, not an afterthought.

Use one of these patterns:

- **Tabbed examples** for related variants such as HTML/CSS/JS, before/after, providers, or approaches.
- **Collapsible details** for long examples that support a skim-first page.
- **Annotated code** when explaining specific lines.
- **Diff blocks** when reviewing or proposing changes.

Tabbed example baseline:

```css
.code-tabs {
  border: 1.5px solid var(--mh-line);
  border-radius: 12px;
  background: var(--mh-paper);
  overflow: hidden;
}
.tabbar {
  display: flex;
  flex-wrap: wrap;
  border-bottom: 1.5px solid var(--mh-line);
  background: var(--mh-faint);
}
.tabbar button {
  font-family: var(--mh-mono);
  font-size: 12px;
  border: 0;
  border-right: 1px solid var(--mh-line);
  background: transparent;
  color: var(--mh-muted);
  padding: 10px 14px;
}
.tabbar button.is-active {
  background: var(--mh-paper);
  color: var(--mh-slate);
  box-shadow: inset 0 -3px 0 var(--mh-plum);
}
.code-panel {
  display: none;
  margin: 0;
  padding: 16px 18px;
  overflow-x: auto;
  font-family: var(--mh-mono);
  font-size: 12.5px;
  line-height: 1.65;
}
.code-panel.is-active { display: block; }
```

Code block rules:

- Horizontal scrolling is acceptable inside `pre`, `.diff`, and dense tables only. It is not acceptable for chip-like controls.
- Add a small code header with file name, language, or purpose when useful.
- Highlight important tokens with plum; keep comments muted.
- For annotated examples, use a grid with stable line-number and code columns.
- For diffs, use a dark slate background, muted line numbers, olive additions, rust deletions, and plum for the currently discussed line or annotation.
- Include copy buttons for code, CSS, JSON, prompts, or diffs when the user will reuse the content.

## Responsive Rules

- No page-level horizontal scrolling at mobile widths.
- Let cards stack, let table-like comparisons become rows, and let nav/chip rows wrap.
- Keep sidebars optional. If a sticky side nav would crowd mobile, convert it into a wrapping top nav.
- Do not scale font sizes with viewport units. Use explicit breakpoints.

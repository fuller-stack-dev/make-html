# Source Style

When an artifact explains or represents an existing project, product, app, docs site, or brand, inspect that source's styling before designing the page.

## What To Inspect

Look for these files first, using the names that fit the project:

- `styles.css`, `globals.css`, `global.css`, `base.css`, `components.css`
- `tailwind.config.*`, theme config, token JSON, design token files
- UI component source for buttons, chips, cards, tabs, nav, tables, and status badges
- docs custom CSS
- existing screenshots or product pages if available locally

Search terms that usually find the useful pieces:

- `--accent`, `--primary`, `--bg`, `--card`, `--border`, `--muted`, `--radius`, `--shadow`
- `chip`, `pill`, `badge`, `btn`, `card`, `nav`, `toolbar`, `status`
- `font-family`, `color-scheme`, `theme`, `data-theme`

## How To Apply It

- Reuse the product's tokens where possible instead of inventing a new palette.
- Match the product's density. Operational dashboards should feel compact and work-focused; docs pages can be more spacious; marketing pages can be more expressive.
- Preserve recognizability: accent color, secondary accent, surface depth, radius, borders, focus treatment, button/chip style, typography, and motion.
- Avoid blindly copying a whole app shell when the artifact is a standalone report. Borrow the flavor and components, then design the artifact for its job.
- If the project has multiple themes, choose the one most recognizable or relevant to the artifact and note the source.
- Include style evidence in the artifact when the styling is a meaningful requirement: token names, file paths, and a short explanation of what was reused.

## Common Misses

- Creating a neutral gray dashboard when the source app has strong theme tokens.
- Using horizontal scrolling for chip-like controls because the source app has dense controls elsewhere.
- Copying colors but missing the source density, borders, radius, and button states.
- Adding every possible relationship to a diagram even when the source project favors compact, readable operational UI.

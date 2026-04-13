# Récré & Réussite — Project Guidelines

## Project Overview

Static website for **Récré & Réussite**, a childcare service business.
Domain: `recre-reussite.fr`

## Tech Stack

- **Framework:** [Astro](https://astro.build/) — static site generator
- **Styling:** Tailwind CSS v4
- **Icons:** Lucide Icons
- **Fonts:** Nunito + Lilita One (Google Fonts)
- **Deployment:** GitHub Pages via GitHub Actions
- **Output:** 100% static HTML/CSS/JS — no server-side runtime

## Language

- **Code, comments, variable names, commit messages in English.**
- Website content in **French** (formal "vous").

## Design

See `DESIGN.md` for colors and brand identity. Design tokens live in `src/styles/global.css` via Tailwind v4 `@theme`.

## Development

```bash
npm install          # Install dependencies
npm run dev          # Start dev server (localhost:4321)
npm run build        # Build static site to ./dist
npm run preview      # Preview production build locally
```

## Conventions

- Astro components (`.astro` files)
- Semantic HTML, responsive, accessible
- Design tokens in Tailwind config, not hardcoded hex in templates

## Price Simulator (`src/pages/prix.astro`)

Client-side price simulator for garde à domicile (childcare at the family's home).

### Configurable constants (top of `<script>`)

| Constant | Default | Description |
|----------|---------|-------------|
| `BASE_HOURLY_RATE` | 12.00 | Julie's base hourly rate (€) |
| `EXTRA_CHILD_RATE_INCREASE` | 0.20 | +20% per child from the 3rd |
| `FREE_CHILDREN_THRESHOLD` | 2 | No surcharge for first N children |

### Calculation flow

1. **Effective hourly rate** = `BASE_HOURLY_RATE × (1 + max(0, children - 2) × 0.20)`
2. **Gross monthly cost** = hourly rate × weekly hours × 52/12
3. **CMG aid** (post-September 2025 reform): `gross × (1 - monthlyIncome × tauxEffort / 10.38)`. Per household (not per child). Eligible if at least one child under 6 (under 12 for single parents).
4. **Tax credit** = 50% of (gross − CMG), capped at (12,000 + 1,500/child)/12 per month, max 15,000/year
5. **Reste à charge** = gross − CMG − tax credit

### CMG taux d'effort (garde à domicile)

| Children | Rate |
|----------|------|
| 1 | 0.1238% |
| 2 | 0.1032% |
| 3 | 0.0826% |
| 4+ | 0.0620% |

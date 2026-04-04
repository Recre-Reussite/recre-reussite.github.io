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

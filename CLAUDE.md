# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Static one-page site dedicated to Carlo Chiavegato ("Carolus", 1923–2015), painter and photographer. Italian-language (`lang="it"`). Archive/portfolio: painting, photography, biography, critique, contacts.

## Run locally

```
serve.bat
```

Wraps `python -m http.server 8000` from the `site/` directory and opens the browser. On macOS use `python3 -m http.server 8000` inside `site/`.

No build step, no package manager, no tests, no linter. Edits to `site/index.html` are live on reload.

`?dev=1` query param activates an inline tweaks panel (lazy-loaded React + Babel from CDN) that lets you preview font / color / spacing / animation variants without editing CSS. Defaults live in the `TWEAK_DEFAULTS` object at the bottom of `site/index.html`. Production loads zero panel code.

## Architecture

Everything lives in a single file: `site/index.html` (~2400 lines). It contains the full HTML, an inline `<style>` block (design tokens + all CSS), and inline `<script>` blocks for interactivity. Images are in `site/assets/`. Source / unprocessed photos live in `FOTO-SITO NONNO/` at the repo root (not served).

Page sections (anchors used by the nav, in order):
- `#home` — hero
- `#pittura` — paintings gallery (tabs: figure, natura morta, paesaggi, astratto)
- `#fotografia` — photography gallery (tabs: realismo, astratta)
- `#biografia` — biography
- `#critica` — critical texts
- `#contatti` — contact form (HTML5 validation, no backend wired up)

### Design system

CSS custom properties on `:root`: palette in `oklch`, `--terra` accent (a soft blue, not terracotta despite the name), `--white` / `--shadow-*` / `--overlay-*` tokens. Display font is `Cormorant Garamond` (italic for emphasis); body is `Josefin Sans`; both from Google Fonts. The italic `<em>` inside section titles and `Ca<em>ro</em>lus` in the hero is the brand's signature beat.

### Motion system

Three layers, all suppressed by `prefers-reduced-motion`:

1. **Hero entrance** — `body.hero-ready` is added when the preloader hides (~700 ms post-load). Triggers an orchestrated cascade: overline → title (clip-path wipe + blur clearing) → subtitle → CTA → scroll indicator. The hero image starts at `opacity: 0` and fades in alongside the cascade; a 32 s Ken Burns animation runs continuously underneath.
2. **Scroll reveals** — elements with `data-anim="fade|slide-left|slide-right|scale|flip"` and optional `data-anim-delay="1..5"`. An IntersectionObserver flips `anim-done` once at threshold 0.1.
3. **Per-item gallery stagger** — every `.gi` and `.photo-item` starts at `opacity: 0` + lifted/scaled. A separate observer flips `.in-view` per item; JS assigns `transition-delay = min(i, 8) × 70 ms` so each grid reveals as a wave. **Tab switches bypass the stagger** (newly active panel items get delay 0 + `.in-view` immediately) — this matters when adding new tab logic.

The fixed `<nav id="main-nav">` toggles a `.scrolled` class past 60 px scroll.

### Lightbox

Click or Enter on any `.gi` / `.photo-item` opens `#lightbox` (`role="dialog"`, `aria-modal`). Arrow keys navigate; Esc closes. The list is built once from DOM order, so adding a new gallery item just requires `data-img` and `data-caption` attributes.

## Conventions

- **Filenames**: lowercase-hyphenated for new images. Some legacy uppercase names (`PAPER1.jpg`, `NM1.jpg`, `DSC-*.jpg`) exist — don't rename without updating references in `index.html`.
- **Alt text**: include medium and year where known (e.g. `alt="Anziano con carrozza, 1960"`), not just the title.
- **Copy**: no em dashes (`—`) in user-facing text; use `:`, `,`, `;`, parentheses, or `·`. The site has been swept; keep it that way. CSS/JS comments are exempt.
- **Tokens**: use `var(--white)` / `var(--terra)` etc. rather than hex or `white`/`black` keywords.
- **Anchors**: section IDs are Italian (`#pittura`, `#fotografia`, `#biografia`, `#critica`, `#contatti`). The nav links and `data-panel` tab attributes depend on these.

# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
pnpm dev        # Start dev server
pnpm build      # Production build
pnpm preview    # Preview production build
```

## Architecture

Single-page portfolio site built with Astro 5 + Tailwind CSS 4. No routing beyond `src/pages/index.astro` — the entire site is one page with anchor-based navigation.

**i18n system:** Translations are handled client-side via `data-i18n-es` / `data-i18n-en` attributes on HTML elements. The `applyLang()` function in `Layout.astro`'s inline `<script>` reads these attributes and sets `textContent` accordingly. Language preference is persisted in `localStorage`. To add a translatable string, add both `data-i18n-es="..."` and `data-i18n-en="..."` attributes to the element — no separate translation files exist.

**Content is hardcoded in components:** Projects, experience, and certifications are defined as typed arrays/objects at the top of their respective `.astro` files (`Projects.astro`, `Experience.astro`, `Certifications.astro`). Adding new entries means editing those arrays directly.

**Icons** live in `src/components/icons/` as individual `.astro` files. Each icon accepts a `class` prop for sizing (used with Tailwind `size-*` utilities).

**Styling:** Tailwind CSS 4 (Vite plugin, not PostCSS). Global styles and the scroll-driven header blur animation are in `Layout.astro`'s `<style is:global>` block. `src/styles/global.css` is also imported there.

**Font:** Onest Variable from `@fontsource-variable/onest`.

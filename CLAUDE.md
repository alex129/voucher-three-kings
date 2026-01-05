# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Interactive gift voucher web application for Three Kings Day (Día de Reyes), featuring a star-catching game that reveals a Michelin star restaurant voucher. Built with Astro 5 + TypeScript + Tailwind CSS 4 + GSAP.

## Commands

```bash
npm run dev      # Start dev server at localhost:4321
npm run build    # Production build to dist/
npm run preview  # Preview production build
```

## Architecture

Single-page Astro application with client-side game logic:

```
src/
├── pages/index.astro       # Entry point
├── layouts/Layout.astro    # Base HTML with fonts
├── components/
│   ├── StarCatcher.astro   # Main game logic (spawns stars/bombs, tracks score)
│   ├── Envelope.astro      # Opening animation, exposes openEnvelope() globally
│   └── VoucherCard.astro   # Final voucher display
└── styles/global.css       # Theme colors, custom fonts, base styles
```

**Component Flow:**
1. `StarCatcher` manages falling stars game (catch 5 stars, avoid bombs)
2. On win, hides game UI and reveals `Envelope`
3. `Envelope.openEnvelope()` animates flap opening
4. `VoucherCard` reveals with restaurant details

**Global Function:** `window.openEnvelope` is set by Envelope.astro for cross-component communication.

## Theme System

Custom Tailwind 4 theme in `global.css`:
- Colors: `desert-sand`, `golden`, `royal-gold`, `bronze`, `deep-amber`, `midnight-blue`, `rich-purple`, `crimson`, `sapphire`
- Fonts: `--font-ornate` (Playfair Display), `--font-body` (Lato)

## Customization Points

- **Recipient/Restaurant**: Edit constants in `VoucherCard.astro` (lines 2-3)
- **Stars required**: Change `totalStars` in `StarCatcher.astro` (line 158)
- **Game difficulty**: Adjust spawn intervals in `startGame()` function

## Accessibility

WCAG 2.2 Level AA compliant:
- All stars are keyboard-navigable buttons
- `aria-live` regions announce score changes
- `prefers-reduced-motion` support throughout
- Screen reader announcements for game events

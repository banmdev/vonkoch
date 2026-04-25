# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Single-page marketing site for **Dr. Katharina von Koch** — private holistic dentistry practice in Halle (Saale), Germany. Content is in German (`<html lang="de">`).

## Structure

The entire site is one self-contained file: `index.html` (~1335 lines). There is no build system, no package manifest, no tests, and no dependencies installed locally.

- **CSS**: inline in a single `<style>` block (roughly lines 10–871).
- **JS**: inline in a single `<script>` block at the end (~lines 1313–1331). Two behaviors: an `IntersectionObserver` that toggles `.visible` on `.reveal` elements, and a scroll listener that shrinks the nav padding past 40px.
- **External assets**: Google Fonts only (`Fraunces`, `DM Sans`). No bundler, no JS framework.

## Running / previewing

Open `index.html` directly in a browser, or serve the directory with any static server (e.g. `python -m http.server`). There is nothing to build, lint, or test.

## Working in the file

- The page is structured as `<nav>` + sections with stable IDs used by the in-page nav links: `#praxis`, `#leistungen`, `#netzwerk`, `#vita`, `#kontakt`. Don't rename these without updating the `<nav>` anchors.
- The design system lives in CSS custom properties on `:root` (cream/petrol/rose/gold palette, `--ink`, `--line`). Prefer adjusting those tokens over hardcoding new colors.
- Animated entrances rely on the `.reveal` class — any new element that should fade in on scroll needs that class so the `IntersectionObserver` picks it up.
- Decorative `.blob` elements and the `body::before` SVG-noise overlay are intentional; don't remove them when refactoring sections.
- All copy is German. Keep new text in German and match the existing voice (warm, holistic, lowercase-leaning, em-dashes, `✦` and italic accents).

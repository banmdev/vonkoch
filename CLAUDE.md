# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Single-page marketing site for **Dr. Katharina von Koch** — private holistic dentistry practice in Halle (Saale), Germany. Content is in German (`<html lang="de">`).

## Structure

The entire site is one self-contained file: `index.html` (~1335 lines). There is no build system, no package manifest, no tests, and no dependencies installed locally.

- **CSS**: inline in a single `<style>` block (roughly lines 10–871).
- **JS**: inline in a single `<script>` block at the end (~lines 1313–1331). Two behaviors: an `IntersectionObserver` that toggles `.visible` on `.reveal` elements, and a scroll listener that shrinks the nav padding past 40px.
- **Fonts**: served locally. `fonts.css` declares the `@font-face` rules and points at `fonts/*.woff2` (Fraunces variable + DM Sans, fetched from Google Fonts and committed). No external font request at runtime.
- **No bundler, no JS framework, no external assets at runtime.**

## Running / previewing

Open `index.html` directly in a browser, or serve the directory with any static server (e.g. `python -m http.server`). There is nothing to build, lint, or test.

## Working in the file

- The page is structured as `<nav>` + sections with stable IDs used by the in-page nav links: `#praxis`, `#leistungen`, `#netzwerk`, `#vita`, `#kontakt`. Don't rename these without updating the `<nav>` anchors.
- The design system lives in CSS custom properties on `:root` (cream/petrol/rose/gold palette, `--ink`, `--line`). Prefer adjusting those tokens over hardcoding new colors.
- Animated entrances rely on the `.reveal` class — any new element that should fade in on scroll needs that class so the `IntersectionObserver` picks it up.
- Decorative `.blob` elements and the `body::before` SVG-noise overlay are intentional; don't remove them when refactoring sections.
- All copy is German. Keep new text in German and match the existing voice (warm, holistic, lowercase-leaning, em-dashes, `✦` and italic accents).

## Konzept (aus konzept.txt)

Die inhaltliche und gestalterische Linie orientiert sich an einem mit der Praxis abgestimmten Konzept. Die Eckpunkte:

### Visuelle Referenzen
- **Farbgrundlage**: helles Petrol, Altrosa, ein gedämpftes Blau — _weniger intensiv_ als die Referenzseite https://www.clinic334.co.uk/. Sättigung bewusst zurückgenommen, viel Weißraum.
- **Stilvorbild der Ausbilderin**: https://www.zahnarzt-gruenebach.de/dentosophie — ruhige, warme Tonalität, Fotografie statt klinischer Stockbilder.
- **Inhaltliches Vorbild (reine Dentosophie-Privatpraxis)**: https://www.dentosophiekiel.de/ — wir adaptieren die inhaltliche Konsequenz, nicht das Layout.

### Inhaltsstruktur
1. **Hero**: Zitat („Die Mundhöhle erzählt Geschichten des Körpers — wer genau hinsieht, erkennt die Krankheit, bevor sie spricht."), Headline „Integrativ. Non-invasiv. Ganzheitlich.", Subline „Zahnärztin in Halle Dr. med. dent. Katharina von Koch".
2. **Über mich (Praxis)**: Vier Bausteine — Ursache statt Reparatur, Aktiv statt Passiv (Dentosophie / Balancer), Sicherheit durch Kinesiologie, Interdisziplinäres Backup. Schließt mit dem Patienten-Benefit.
3. **Leistungen — drei Säulen**: Dentosophie, Kinesiologie, Umweltzahnmedizin. Jede Säule mit kurzem Tagline und ausführlichem Text (sichtbar ausgeklappt, kein Click-State).
4. **Netzwerk**: Headline „Gesundheit braucht Zusammenarbeit." mit interdisziplinärem Fokus (Osteopath:innen, Therapeut:innen).
5. **CTA**: „Lassen Sie uns gemeinsam hinsehen — Termin vereinbaren."

### Behaltene Stilelemente aus dem bisherigen Entwurf
- Die Headline „Was der Körper schon weiß — wenn man zuhört." wird beibehalten.
- Der Satz „Welche davon zu Ihnen gehört, zeigt sich im Gespräch — nie in einem Formular." wird beibehalten (auf drei Säulen umgemünzt: „Drei Säulen. Ein Mensch.").

### Domain-Ideen (Notiz, noch offen)
oralbalance.de · mundraum-halle.de · biozahn-halle.de

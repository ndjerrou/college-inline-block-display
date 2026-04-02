# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-file interactive CSS teaching tool (`cours_css_atlas.html`) for French-speaking middle school students. It teaches CSS block/inline display and positioning concepts through 5 progressive exercises themed around Moroccan football (FC Atlas Academy).

## Architecture

The entire app lives in one HTML file with embedded CSS and JavaScript:

- **CSS (lines 8–343)**: Custom design system using CSS variables (`--navy`, `--gold`, `--terra`, `--cream`, etc.), Cinzel/Nunito/Fira Code fonts. No framework — all hand-written.
- **HTML (lines 345–365)**: Minimal shell — header, empty `#exNav` and `#exPages` containers, footer. All content is JS-rendered.
- **JavaScript (lines 367–end)**: Contains:
  - `SC` constant: shared CSS injected into every exercise iframe
  - `EX` array: data for all 5 exercises (id, concept explanation, before/after HTML, step-by-step guide)
  - Rendering logic that builds tab navigation and exercise pages from the `EX` data
  - Before/After iframe viewer toggling

Each exercise has a "before" (broken) and "after" (fixed) HTML rendered in iframes via `srcdoc`. Exercises progress: block vs inline → inline-block → position relative → position absolute → challenge (no guide).

## Development

No build tools, no dependencies. Open `cours_css_atlas.html` directly in a browser.

## Language

All user-facing content is in **French**. The pedagogical theme uses Moroccan football analogies (players, FIFA cards, stadium metaphors) to explain CSS concepts.

## Key Patterns

- Exercise data is defined declaratively in the `EX` array — add new exercises by appending objects matching the existing shape
- The `SC` template literal provides consistent base styles across all exercise iframes
- Before/After comparison uses `srcdoc` iframes with inline `<style>` tags
- Exercises 1–4 have step-by-step guides; exercise 5 is a self-directed challenge (`hasGuide: false`)

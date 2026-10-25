---
doc: spec
status: draft
---

# Scope Cutter — Technical Spec

> **Process note:** The stack and structure were chosen by Claude at the learner's request to delegate decisions. The learner should read this and confirm or change it.

## How This Works, In Plain Language
Scope Cutter is one web page. You type your features in; the page turns each line into a card. It checks each line for risky words (like "login" or "payment") and guesses how long it would take. You sort the cards; the page adds up the hours you kept and compares them with your budget. At the end it scores your choices and writes a short Markdown summary you can copy. Everything happens inside your browser. There is no server and no database, because a proof of concept does not need one.

## The Core Journey Through the System
PRD ref: `prd.md > The Core Journey`.
1. You press **Start cutting** → the form text is split into lines and cleaned → each line becomes a feature object with its traps and effort guess.
2. You swipe or press a key → one decision handler records the choice and the card flies off → counters and the budget bar redraw.
3. The last card is sorted → the app checks: nothing kept (Empty), over budget (Trim), or fine (Kernel).
4. You pick a kernel → the score is computed from the feature list → the result screen and the Markdown are generated from the same data.

## Stack
- Plain HTML, CSS and JavaScript in one file (`index.html`). No framework, no build step, no dependencies — it opens by double-clicking and keeps the repo reviewable.
- Google Fonts (Bricolage Grotesque, JetBrains Mono) loaded from a CDN. If offline, the page falls back to system fonts.
- Browser APIs: Pointer Events (dragging), Clipboard API, Blob download, `localStorage`.

## Where It Runs and How Someone Tries It
Runs in any modern browser. No keys, no install.
- Open `index.html` directly, or from the project folder run `python3 -m http.server 8000` and visit `http://localhost:8000`.
- For the demo video: click "Try a sample idea", sort all cards, trim if prompted, choose a kernel, then press "Copy as Markdown".
- Submission needs a short demo video and a public repository. Hosting is optional (any static host, such as GitHub Pages, would work).

## Look and Feel
Carried from `prd.md > Look and Feel`: warm paper background, ink outlines with hard offset shadows, vermilion accent, green/blue for keep/later. Bricolage Grotesque and JetBrains Mono. Fast, decisive, playful copy. Reduced-motion users get no animation.

## Components

### Setup form
Collects name, one-liner, features, budget; parses features; restores and saves the last form. PRD ref: `prd.md > Setting up a round`.

### Card stage
Draws the current card plus a blurred one behind it; handles drag, buttons, keys, undo, and effort cycling. PRD ref: `prd.md > Sorting cards`.

### Trap detector
A list of keyword rules (accounts, payments, real-time, notifications, admin, maps, localization, native, social, AI). Each gives a label, a short warning, a default effort, and a cut reason. PRD ref: `prd.md > Sorting cards`.

### Budget meter and HUD
Sums the hours of kept features against the budget; shows over-budget state. PRD ref: `prd.md > Budget and trimming`.

### Trim, Kernel, Result screens
Trim demotes keepers; Kernel picks one; Result shows the score and builds the Markdown for copy/download. PRD ref: `prd.md > Kernel and result`.

## Data Model
One in-memory object `st`: name, one-liner, budget, a list of features, the current card index, a history stack, the kernel.
Each feature: `{ text, traps[], effort (0 to 3), choice: null | keep | later | cut }`.
Only the last form values (name, one-liner, features text, budget) are saved to `localStorage`; reloading returns you to the form with those values filled in.

Score (out of 100): fits budget 40, tight scope 25 (fewer keepers = more), traps dodged 20, kernel chosen 15.

## File Structure
```
scope-cutter/
├── index.html          # the whole app: markup, styles, script
├── README.md           # how to run it
├── devpost/            # planning docs from the Devpost Learn skills
│   ├── scope.md
│   ├── prd.md
│   └── spec.md
└── .agents/skills/     # the Devpost Learn skill pack
```

## External Services and Dependencies
Google Fonts only (free, no key). Nothing else.

## Important Failure Modes
- **Fonts fail to load** → system fonts are used; layout still works.
- **`localStorage` blocked** (private mode) → the app works; the form just doesn't remember.
- **Clipboard blocked** → a fallback copy runs; if that fails, a toast points to the Markdown preview.

## What Was Simplified and Why
- **Keyword rules** instead of AI estimates — no keys or backend, and the reasons stay explainable. The fuller version would call a model and need a server to hide the key.
- **Fixed four effort sizes** instead of free-form hours — faster to tap, enough to force trade-offs.
- **One HTML file** instead of a component framework — less setup, nothing to break.

## Decisions and Open Issues
- All decisions above were made by Claude for the learner, not by the learner.
- Learner uncertainty: none was expressed or discussed, so none is recorded here.
- Open: whether the learner wants to change the idea, name, or visual style before approving.

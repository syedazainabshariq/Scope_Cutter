---
doc: scope
status: draft
---

# Scope Cutter

A game-like web app where you swipe a bloated feature wish-list down to a proof of concept you can build in an afternoon.

> **Process note:** The learner asked Claude to make the planning decisions for this project. Every choice below was made by Claude on the learner's behalf and is open for the learner to change before approving. Nothing here is a quote from the learner.

## The Unique Kernel
Cutting scope feels like a game, not a chore. Each feature is a card you keep, park, or cut against a visible time budget, and the app flags "scope traps" (accounts, payments, real-time, and so on) that quietly blow up a proof of concept.

## Who It's For
Someone about to start a hackathon or side project with a head full of features and one afternoon. Today they keep the list in their head or a notes app, then build the fun parts, run out of time, and submit something half-finished.

## The Core Loop
They paste their feature list and pick a time budget. A card appears for each feature. They swipe it: keep now, later, or cut. The budget bar fills as they keep things. At the end they pick the one kernel feature, and get a scope sketch they can paste straight into a planning doc. Then they can cut again and beat their focus score.

## Inspiration & Identity
Paper cards and a red editing pen. Thick ink outlines, hard offset shadows, warm paper background, a single vermilion accent. Feels like an editor's desk crossed with a card-sorting game. Quick, decisive, a little cheeky. Typefaces: Bricolage Grotesque for headings, JetBrains Mono for labels.

## Why This Matters to the Learner
Not established. The learner delegated the idea, so there is no stated personal stake yet. *(To fill in by the learner.)*

## What "Working" Looks Like
Paste 10 to 12 features, choose "4 hours," and sort them with arrow keys or by dragging cards. The meter turns red when you keep too much, forcing a trim. You choose your kernel and see a score, a rank ("Ruthless Editor"), and a scope sketch where every cut has a real reason. The "oh, that's cool" beat is the red meter and the trim step, followed by a copy-ready Markdown scope.

## The POC Boundary
- Paste or type a feature list, with a built-in sample idea
- Choose a build-time budget
- Swipe cards: keep, later, cut, with undo
- Automatic effort guess per feature, adjustable by tapping
- Scope-trap detection by keyword, with a short reason
- Trim step when kept work exceeds the budget
- Pick one kernel
- Focus score, rank, and a Markdown scope sketch to copy or download

## Later
- AI that estimates effort and suggests the kernel
- Sharing a result as an image
- Saving several ideas and comparing rounds
- Team mode where friends vote on cuts

## Explicitly Cut
- **User accounts and login** — the app stores nothing server-side, so there is nothing to protect.
- **A backend or database** — everything runs in the browser, and the only saved data is the last form in local storage.
- **AI-powered suggestions** — needs an API key and unpredictable output; keyword rules prove the idea without it.
- **Native mobile app** — the web version works on a phone and is far faster to build.

---
doc: prd
status: draft
---

# Scope Cutter — Product Requirements

A game-like web app that turns a bloated feature list into a buildable proof-of-concept scope, for anyone starting a hackathon or side project.
Source: `scope.md > The Unique Kernel`, `scope.md > The Core Loop`.

> **Process note:** Product decisions here were made by Claude at the learner's request to delegate them. They are proposals for the learner to review, not the learner's own words.

## The Core Journey
1. The person opens the page and sees the headline and a form.
2. They enter an idea name, an optional one-line description, and a feature list (one per line, at least 3). They can load a sample idea instead.
3. They pick a time budget (2, 4, 8, or 16 hours) and press **Start cutting**.
4. A card appears for the first feature, showing its text, any scope-trap warnings, and an effort estimate.
5. They sort it: **Keep** (right), **Later** (down), or **Cut** (left), by dragging, pressing a button, or using arrow keys. They can tap the effort label to change the estimate, or undo.
6. The budget bar fills as they keep features. It turns red if they exceed the budget.
7. After the last card, if they are over budget they trim: they move kept features to Later until they fit, or choose to continue anyway.
8. They choose the one kept feature that is the kernel.
9. They see their focus score, rank, and a scope sketch (kernel, build now, later, cut with reasons). They can copy or download it as Markdown, cut again, or start a new idea.

## Screens and Layout
One page, five states shown one at a time: **Setup**, **Sort** (cards, budget bar, counters, three buttons), **Trim** (list of kept features, each with a "move to Later" button), **Kernel** (pick one), **Result**. A sixth tiny **Empty** state appears if everything was cut.

## Look and Feel
Paper-and-red-pen. Warm paper background with faint ruled lines, thick ink outlines, hard offset shadows, one vermilion accent, green for keep, blue for later. Bricolage Grotesque for headings and body, JetBrains Mono for small labels. Playful, decisive tone ("Your idea is too big."). Works on phone and desktop. Respects reduced-motion settings.

## Features and Behavior

### Setting up a round
- As someone with a big idea, I want to paste my features so that I can sort them quickly.
  - [ ] Fewer than 3 distinct features shows an error and does not start
  - [ ] Bullets and numbering in pasted lines are stripped; duplicates are removed
  - [ ] No more than 20 features are used
  - [ ] "Try a sample idea" fills the form with a sample

### Sorting cards
- As a player, I want to keep, park, or cut each feature so that I end up with a short list.
  - [ ] Dragging past a threshold, pressing a button, or pressing an arrow key records the choice
  - [ ] Undo (button or Z) returns to the previous card
  - [ ] The counters and budget bar update after every choice
  - [ ] Features matching a scope trap show a warning and default to a larger effort estimate
  - [ ] Tapping the effort label cycles S, M, L, XL (0.5h, 1h, 2h, 4h)

### Budget and trimming
- As a player, I want to see when I am over budget so that I am forced to trim.
  - [ ] The bar turns red and shows the hours over
  - [ ] If over after the last card, the Trim screen appears; moving items to Later updates the total
  - [ ] "Continue" is enabled only when within budget, with an explicit "ship over budget anyway" link

### Kernel and result
- As a player, I want to name my kernel and get a scope sketch so that I can start building.
  - [ ] Exactly one kept feature can be the kernel
  - [ ] The result shows a score out of 100 with its breakdown, a rank, and the four lists
  - [ ] Every cut shows a reason, specific when it matched a scope trap
  - [ ] Copy and Download produce the same Markdown shown in the preview

## States and Boundaries
- **First use** — empty form with placeholders.
- **Return visit** — the last form values are restored from the browser's local storage.
- **Everything cut** — a message and a button to sort again.
- **Single keeper** — that feature becomes the kernel automatically.
- **Clipboard blocked** — falls back to a hidden-textarea copy, then a message pointing to the preview.
- **Nothing leaves the browser** — no network calls except loading fonts.

## Product Decisions
- Keyword rules, not AI, detect scope traps — works offline, instant, explainable, and needs no key.
- The score rewards fitting the budget, keeping few features, dodging traps, and choosing a kernel — it nudges toward the habit the hackathon teaches.
- Output is Markdown shaped like `scope.md` — so it feeds straight into the planning process.
- A single self-contained HTML file — easy to run, host, and review.

## What We're Building
Everything in the Core Journey, working in the browser from one HTML file.

## Deferred From the POC
- **AI effort estimates and kernel suggestions** — needs an API key and a backend.
- **Saved history of rounds** — needs storage design beyond the last form.
- **Shareable result image** — extra rendering work.

## Possible Later Enhancements
Team voting on cuts, custom trap rules, an export that also drafts a PRD outline.

## Non-Goals
- Not a project manager or task tracker.
- Not an accurate time estimator; the hours are rough guesses to force trade-offs.
- Does not judge whether the idea is good.

## Open Questions
- Should the learner replace Claude's idea with their own? *(Can wait; the app works for any idea.)*
- Does the learner want a name other than "Scope Cutter"? *(Can wait.)*

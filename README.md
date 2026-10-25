# Scope Cutter

A browser game that turns a long feature wish-list into a buildable proof-of-concept scope. Sort each feature into Keep, Later, or Cut against a time budget, then get a scope sketch in Markdown.

Built for the Devpost "Build With AI: Basics" hackathon.

## Run it

No install, no keys.

- Open `index.html` in a browser, or
- `python3 -m http.server 8000` and visit http://localhost:8000

## Use it

1. Click **Try a sample idea** (or paste your own features, one per line).
2. Click **Start cutting**.
3. Sort cards: drag, use the buttons, or press ← (cut), ↓ (later), → (keep). `Z` undoes.
4. If you are over budget, trim. Then pick your kernel feature.
5. Copy or download the Markdown scope sketch.

## Planning docs

The planning docs from the Devpost Learn skills are in [`devpost/`](devpost/): `scope.md`, `prd.md`, `spec.md`. The skill pack is in `.agents/skills/`.

## Tech

One self-contained `index.html` (HTML, CSS, vanilla JavaScript). Fonts load from Google Fonts. Nothing is sent anywhere; the only saved data is your last form in the browser's local storage.

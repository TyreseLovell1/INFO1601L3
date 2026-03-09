Purpose
-------
This repository is a minimal static front-end site (no build system or server-side code). The agent's goal is to make small, safe edits to HTML/CSS/JS, run the site locally for verification, and keep changes minimal and easily testable.

Key facts
- Project type: static site with these root files: [index.html](index.html), [script.js](script.js), [style.css](style.css)
- No package.json, no build step, no tests, and no CI detected.
- JS is loaded via a plain `<script src="script.js"></script>` at the end of `index.html`.
- There is an inline `<style>` block in `index.html` that currently styles `div` elements. `script.js` and `style.css` are present but empty.

How to run locally (developer workflows)
- Quick check: open [index.html](index.html) in a browser (double-click or `file://`).
- Recommended: run a simple HTTP server to preserve relative paths and mimic real environment:
```sh
python -m http.server 8000
# then open http://localhost:8000 in your browser
```
- Alternatively, use VS Code Live Server extension for fast reloads.
- Debugging: use browser DevTools (F12) — console for JS errors, Elements for DOM/CSS.

Repository-specific patterns and examples
- Single-page, static markup. Keep DOM changes minimal and predictable.
- Inline styles exist in `index.html`; example rule:
```css
/* from index.html */
div {
  background-color: lightgrey;
  width: 300px;
  border-bottom: solid;
  padding: 50px;
  margin: 20px 10px 40px 20px;
}
```
- `script.js` is the place for behavior. Keep initialization at top-level or wrap in `DOMContentLoaded` if adding DOM-dependent logic.

Integration & external dependencies
- None detected. There are no external CDNs or npm/yarn dependencies in the repo files.

Editing and PR guidance for agents
- Make small, reviewable edits: modify `style.css` for styling changes and keep `index.html` structural edits minimal.
- If you must change script loading, preserve the order: CSS -> HTML -> script at body end.
- Run the local server and verify the page renders and console is clean before submitting a PR.

What not to assume
- There is no framework, router, or build tooling. Do not add or depend on Node/npm unless the user asks.
- There are no tests or CI; avoid adding complex test infra without explicit request.

If unclear or incomplete
- Ask the maintainer whether they want a build tool, testing, or CI before introducing them.
- If the goal is a larger refactor (framework migration, componentization), ask for constraints and target browsers.

Contact for follow-up
- When proposing larger changes, include quick manual verification steps (URLs, expected DOM text, and console output).

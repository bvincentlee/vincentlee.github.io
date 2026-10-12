# Vincent's Portfolio

Vincent's product design portfolio, published with GitHub Pages at https://bvincentlee.github.io (repo: `bvincentlee/vincentlee.github.io`).

## Structure

Static site with no build step, framework, or package manager.

- `index.html` — the entire site: inline `<style>`, markup, and an inline `<script>` at the bottom
- `assets/` — images (webp), `Resume.pdf`, favicons
- `logo/` — logo variants (svg/webp/png); not currently referenced by `index.html`

## How the page works

`index.html` is a single-page app. Each view is a `<div class="page">`, and only the one with `.active` is shown:

- `#home-page` — hero plus project cards
- `#info-page` — bio and resume link
- `#project-<id>` — one per case study: `signup`, `mars-rover`, `salesforce`, `peloton`, `nasa`, `river-web`

Navigation is handled in JS with `showPage`, `showHome`, `showProject(id)`, and `togglePage` (the nav button, which toggles between "His info" and "Other works"). There is no URL routing or hash state.

Animations use `.reveal` and `.reveal-word` with an IntersectionObserver, plus scroll-linked motion on the home hero and cards.

## Conventions

- Design tokens are CSS custom properties on `:root` (`--bg`, `--coral`, `--text`, `--page-max`, ...). Reuse them instead of hard-coding values.
- Images are webp in `assets/`, mostly with `loading="lazy"`. Keep new images as webp.
- To add a project, add a `#project-<id>` page div and a home card that calls `showProject('<id>')`.
- To update the resume, replace `assets/Resume.pdf` in place; the link path stays the same.

## Skills

Emil Kowalski's design-engineering skills (`emilkowalski/skill`) are installed in `.claude/skills/`: `emil-design-eng`, `animate`, `review-animations`, `improve-animations`, `find-animation-opportunities`, `prototype`, `animation-vocabulary`, `apple-design`, `pick-ui-library`. Use them for motion and UI polish work on this site.

`.claude/` is gitignored, so `skills-lock.json` is the record of what's installed. Restore with `npx skills experimental_install` and update with `npx skills update -p`.

## Preview and publish

- Preview locally by serving the repo root, for example `python3 -m http.server 8000`, then open http://localhost:8000.
- Pushing to `main` publishes the live site.
- Work directly on `main`; don't use worktrees.

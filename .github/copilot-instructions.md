# Copilot Instructions for this repository

## Project overview
This repository is a Hugo-based static site for a personal travel journal and creative writing portfolio. The site is content-driven: journal entries are Markdown files under `content/journal/`, while the visual structure and page templates live in `layouts/` and the styling lives in `static/css/style.css`.

Key files and responsibilities:
- `hugo.toml`: site metadata, base URL, locale, and page title
- `content/journal/`: published and draft journal entries, each as a Markdown file with front matter
- `layouts/index.html`: homepage composition and journal listing
- `layouts/_default/baseof.html`: shared document shell and header/footer
- `static/css/style.css`: all custom site styling and editorial design tokens
- `archetypes/default.md`: default front matter for new content files

The repository does not use a JavaScript framework, package-based web app build, or test suite. It is a static Hugo site with a simple content model.

## Build, test, and validation commands
Run the site build from the repository root:
- `hugo` — generate the static site into `public/`
- `hugo server` — start local preview server for the site
- `hugo server -D` — preview drafts and unpublished content
- `hugo --minify` — production-style build with minified output

There are no automated tests or lint commands in this repo. When making content or template changes, validate with a Hugo build (for example, `hugo` or `hugo server`) and check for template or Markdown errors in the CLI output.

## Conventions specific to this codebase
- Prefer content changes in `content/journal/*.md` over creating new custom logic unless the site structure truly needs it. This site is organized around Markdown content and Hugo templates rather than application code.
- Journal entries use Hugo front matter with fields such as `date`, `title`, `description`, `categories`, and optional `draft = false` / `draft = true`.
- Keep the homepage listing in sync with the journal section. The homepage uses `where .Site.RegularPages "Section" "journal"` in `layouts/index.html`; new entries under `content/journal/` appear there automatically.
- Keep styling changes centered in `static/css/style.css`. The project uses a custom editorial design system with CSS variables such as `--bg-color`, `--coral`, and `--turquoise`.
- `public/` is generated output; it is not the source of truth for edits. Make changes in the source files under `content/`, `layouts/`, and `static/`.
- New content files should follow the established pattern in `archetypes/default.md`, including Hugo front matter and a published/draft status that matches the intended site behavior.

## Editing guidelines
- Use Markdown for content pages, with concise front matter and plain prose. This site is designed for readable, editorial writing rather than structured CMS metadata.
- When changing layout or navigation, keep the site’s theme consistent with the existing serif editorial styles and the custom color palette defined in `static/css/style.css`.
- If a new entry is meant to be public, set `draft = false` before publishing; keep draft posts as `draft = true` until ready to appear in generated output.

## Common maintainer workflow
1. Add or edit a journal post in `content/journal/`.
2. Run `hugo` or `hugo server` to verify the Markdown and templates compile cleanly.
3. Review the generated output or local preview for broken links, layout regressions, and missing metadata.

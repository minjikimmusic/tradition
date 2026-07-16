# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

A single-file static personal profile/portfolio page for 김민지 (Kim Minji), a Korean traditional music (국악) researcher and gayageum performer. There is no build system, package manager, or dependencies — the entire site is one self-contained HTML file plus a profile photo.

## Files

- `index.html` — the entire site: markup, CSS (inline `<style>` in `<head>`), no JavaScript.
- `profile.jpg` — profile photo referenced by `index.html`.

## Running / previewing

There is no build or dev server. Open the file directly:

```
open index.html
```

## Absolute rules

- Always respond in Korean.
- Never use `!important` in CSS.
- Minimize external libraries/dependencies — this project has none; keep it that way unless the user asks otherwise.

## Code conventions

- Manage colors via CSS custom properties on `:root` rather than repeating literal hex values (the current stylesheet predates this convention and still uses literal hex — prefer `:root` variables for any new/updated CSS).
- Class names use kebab-case (e.g. `pub-title`, `video-card`, `card-grid`) — follow this for any new classes.

## Author & design

- Site owner: 김민지 (Kim Minji).
- Design is light mode: white background (`#ffffff`), black text (`#111111`) — not dark mode. This was an explicit, deliberate change made mid-project; don't revert to dark mode without being asked.

## Architecture

`index.html` is a single-page site with a sticky header nav and four anchor-linked sections (`#profile`, `#research`, `#videos`, `#demos`):

- **`#profile`** — photo, name/title, and short bio tags.
- **`#research`** (`연구`) — publication list grouped by year (`.pub-year` containing `.pub-item` entries), most recent year first. Each entry follows a fixed sub-structure: `.pub-title` (bold title, `::before` CSS adds the `• ` bullet), `.pub-authors`, `.pub-detail` (venue name with only the journal/publisher title in `<em>`, then registration type e.g. `(KCI)`/`(SCOPUS/KCI 우수등재)`, volume/issue, date). When adding new entries, follow this exact structure and ordering rather than introducing a new format.
- **`#videos`** (`연주 영상`) — grid of performance video placeholder cards (`.video-grid` > `.video-card`), each with a `.thumb` placeholder and `.caption`. Real video embeds/thumbnails should replace the `.thumb` placeholder content.
- **`#demos`** (`연구 데모`) — grid of research demo placeholder cards (`.card-grid` > `.card`), same pattern as `#videos`.

Design system (defined once in `<style>`, reused across sections): white background, black text, centered `<section>` containers (max-width 720–760px) with a bottom border separating sections, except `#research` which is left-aligned internally for readability of the publication list. Sections without real content yet are intentionally left as clearly-labeled placeholder cards rather than removed — do not delete placeholder sections without being asked.

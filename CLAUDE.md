# CLAUDE.md

## Project Overview

Interactive single-page web application displaying a map of Pennsylvania shipbuilding and energy projects, targeting Korean shipbuilding materials (조선기자재) investment opportunities. Built as a static HTML file with no build system or dependencies beyond a CDN-loaded mapping library.

## Repository Structure

```
USA/
└── index.html    # Entire application (HTML + CSS + JS, ~440 lines)
```

This is a **single-file project** — all markup, styles, and logic live in `index.html`.

## Tech Stack

- **HTML/CSS/JavaScript** — no frameworks, no build tools, no package manager
- **Leaflet.js v1.9.4** — interactive map library, loaded from unpkg CDN
- **Map tiles** — CartoDB dark theme (`dark_all`)
- **Language** — Korean (`lang="ko"`) with English project names

## Architecture

### Data Model

Five project objects in a `const projects` array, each with:
- `lat`, `lng`, `zoom` — map coordinates and zoom level
- `color` — marker color
- `name`, `area`, `invest`, `status`, `desc`, `cardId` — display content

### UI Layout

- Two-column flexbox layout: left map (65%) + right sidebar cards (35%)
- Responsive breakpoint at 768px switches to single column
- Dark theme with navy/midnight blue backgrounds

### Key Functions

- `flyTo(idx)` — animates map to a project's coordinates
- Markers use custom `L.divIcon` with inline SVG
- Polygons define Navy Yard and Greenway District boundaries
- Cards and markers are linked via click handlers

## Development Workflow

### Running Locally

Open `index.html` directly in a browser. No server, build step, or install required.

### Making Changes

1. Edit `index.html` directly
2. Refresh browser to see changes
3. All CSS is in a `<style>` block; all JS is in a `<script>` block at the end

### No Build/Test/Lint

- No package.json, no npm scripts
- No test framework
- No linter or formatter configured
- No CI/CD pipeline

## Conventions

- **CSS classes**: BEM-inspired naming (`project-card`, `project-header`, `project-icon`)
- **IDs**: Cards use `card-1` through `card-5`
- **Colors**: Accent `#7ab8f5`, success `#6dce6d`, warning `#f5c842`
- **No modules** — vanilla JS with functional style
- **Inline everything** — styles and scripts are embedded, not in separate files

## Git

- Default branch: `main`
- Signed commits enabled (`gpg.format=ssh`)
- Commit messages should describe what changed and why

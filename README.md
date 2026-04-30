# 108 Moves

A step-by-step guide to the simplified versions of the 108 moves of Tai Chi as practised by the Caerphilly beginner class of Tai Chi Evolutions.

Built with Hugo and Tailwind CSS v4.

## Features

- All 108 moves defined in `content/_index.md` front matter and rendered automatically
- Each move is a collapsible card showing step-by-step instructions
- Toggle between standard and advanced step descriptions per move
- Adjustable card size (Small, Normal, Large) persisted in local storage
- Connector lines and transition notes between moves
- Sticky navbar and title bar for easy access while scrolling
- Collapsible tutorial block at the top of the page

## Getting Started

1. Install Hugo Extended.
2. Install Node dependencies:

```bash
npm install
```

3. Run local development server:

```bash
hugo server -D
```

4. Build production output:

```bash
hugo
```

## Adding or Editing Moves

All moves are defined in `content/_index.md` as a `moves` front matter array. Each entry supports:

| Field | Required | Description |
|---|---|---|
| `name` | Yes | Display name of the move |
| `weight` | Yes | Sort order (ascending) |
| `steps` | Yes | Array of standard step descriptions |
| `steps_advanced` | No | Array of advanced step descriptions (shown when Advanced is toggled on) |
| `transition_note` | No | Short note shown in the connector between this move and the next |

## Project Structure

- `config.toml` — site config, favicon path, and build settings
- `content/_index.md` — all move data and homepage prose
- `assets/css/main.css` — Tailwind entry file and theme tokens (`@theme`)
- `assets/css/modules/layout.css` — base styles and move-flow size system
- `layouts/index.html` — homepage template with size and advanced controls
- `layouts/partials/components/move-card.html` — collapsible move card partial
- `layouts/partials/components/move-transition.html` — connector and transition note partial
- `layouts/partials/components/rich-content-classes.html` — shared prose Tailwind classes
- `static/favicon.svg` — site favicon

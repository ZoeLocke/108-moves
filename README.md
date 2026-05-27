# 108 Moves

A visual guide to the 108 moves of Tai Chi as practised by the Caerphilly beginner class of Tai Chi Evolutions. Each move features instructional videos with responsive fallback support.

Built with Hugo and Tailwind CSS v4.

## Features

- All 108 moves rendered from individual content files
- Collapsible move cards with descriptive prose content
- Embedded instructional videos (WebM with MP4 fallback) for each move
- Lazy-loaded videos that only load when a card is opened
- Automatic format fallback if WebM fails to load or render
- Adjustable card size (Small, Normal, Large) persisted to local storage
- Connector lines with transition notes between moves
- Sticky header for navigation while scrolling
- Fully responsive and accessible design

## Getting Started

1. Install Hugo Extended.
2. Install Node dependencies:

```bash
npm install
```

Local dev note: if you are testing locally without a live reCAPTCHA setup, comment out `recaptcha_site_key` in `config.toml`.

3. Run local development server:

```bash
hugo server -D
```

4. Build production output:

```bash
hugo
```

## Adding or Editing Moves

Each move is a separate directory under `content/moves/` with an `index.md` file. Each move supports:

| Field | Required | Description |
|---|---|---|
| `title` | Yes | Display name of the move |
| `weight` | Yes | Sort order (ascending, 1–108) |
| `learned` | Yes | Boolean indicating if the move is in active rotation |
| `direction` | No | Direction of movement (e.g., "Left", "Front", "Right") |
| `tip` | No | Handy tips to help you remember how to do the move |
| `transition_note` | No | Short note shown in the connector to the next move |
| Content body | No | Prose description of the move (supports Markdown) |

### Media Files

Each move directory can optionally include:
- `*.webm` — WebM video file (preferred format for efficiency)
- `*.mp4` — MP4 video file (fallback if WebM fails)

Videos are lazily loaded only when the move card is expanded. If a WebM file fails to load or stall during playback, the player automatically switches to MP4.

## Project Structure

- `config.toml` — site configuration and parameters
- `content/moves/` — 108 individual move directories, each with `index.md` and optional video files
- `content/login.md`, `content/privacy.md`, `content/tutorial.md` — static pages
- `assets/css/main.css` — Tailwind entry point with CSS custom properties (`@theme`)
- `assets/css/modules/layout.css` — responsive sizing system and base styles
- `layouts/index.html` — homepage template with move flow container and size controls
- `layouts/_default/` — standard Hugo layout templates
- `layouts/partials/components/move-card.html` — collapsible move card with video player
- `layouts/partials/components/move-transition.html` — visual connector and transition note
- `layouts/partials/components/move-controls-bar.html` — header with size menu
- `layouts/partials/header.html`, `footer.html` — global header and footer
- `static/robots.txt`, `static/images/` — static assets

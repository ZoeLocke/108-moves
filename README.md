# Hugo Tailwind Starter

A bare-bones website starter that keeps the core Hugo architecture and Tailwind CSS v4 integration.

## Included

- Hugo templates: base, home, list, and single layouts
- Tailwind CSS integration through Hugo's asset pipeline
- Minimal content: Home, About, and Blog with one sample post
- Minimal reusable CSS foundation in assets/css/modules/layout.css

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

## Project Structure

- config.toml: Site config with Hugo and Tailwind build settings
- assets/css/main.css: Tailwind entry file
- assets/css/modules/layout.css: Minimal base layer styles
- layouts/: Core templates and partials
- content/: Starter pages and blog content

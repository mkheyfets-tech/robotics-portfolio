# robotics-portfolio

Personal portfolio site — robotics engineering projects, built with [Astro](https://astro.build) and deployed to GitHub Pages at
[mkheyfets-tech.github.io/robotics-portfolio](https://mkheyfets-tech.github.io/robotics-portfolio/).

## Structure

```text
public/              images, PDFs, favicon (served from /robotics-portfolio/…)
src/
├── components/
│   └── DotField.jsx     interactive cursor dot-field (currently unused — see below)
├── layouts/
│   └── Layout.astro     design system, site header/footer, project page shell
└── pages/
    ├── index.astro      hero + work index
    ├── 404.astro
    └── projects/*.md    one markdown file per project
```

## Adding a project

Drop a new `.md` file into `src/pages/projects/`. It gets picked up automatically
by the work index on the homepage. Frontmatter:

```yaml
---
layout: ../../layouts/Layout.astro
title: Project name
summary: One or two sentences, shown on the index and as the page lede.
course: RBE 3001 — Unified Robotics III   # optional, shown in the spec list
image: /robotics-portfolio/thumbnail.png
tech: [C++, PID Control, CAD]
---
```

The layout renders the title, lede and spec table from frontmatter, so the
markdown body should start straight into content — no `# Title` needed.

To list a project under **Research & strategy** rather than **Selected work**,
add its title to the `RESEARCH_TITLES` array at the top of `src/pages/index.astro`.

## Design notes

- Type: Instrument Serif (display) / IBM Plex Sans (body) / IBM Plex Mono (labels).
- Colour lives in `:root` and `html.light-theme` in `Layout.astro`. The palette is
  deliberately near-monochrome — `--signal` is the only accent and is reserved for
  interactive states, so adding it as decoration will flatten the hierarchy.
- Theme preference persists in `localStorage` and is applied before first paint.

`DotField.jsx` is kept but no longer mounted. To bring it back, import it in
`index.astro` and render `<DotField client:load />` inside `.hero`.

## Commands

| Command           | Action                                       |
| :---------------- | :------------------------------------------- |
| `npm install`     | Install dependencies                          |
| `npm run dev`     | Dev server at `localhost:4321`                |
| `npm run build`   | Production build to `./dist/`                 |
| `npm run preview` | Preview the production build locally          |

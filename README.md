# Ask Charli3 — HyperFrames Video

**A code-driven, ~40-second promo video for the Charli3 Oracle AI Agent Skills, built as an HTML + GSAP [HyperFrames](https://hyperframes.heygen.com) composition and rendered to MP4.**

## Overview

This repository is a [HyperFrames](https://hyperframes.heygen.com) project — a motion-graphics video defined entirely as HTML, CSS, and GSAP timelines rather than authored in a traditional video editor. The composition tells the launch story of *Charli3 Oracle AI Agent Skills* (installable via `npx skills add`), moving through an intro, a skills cloud, a terminal install sequence, and an outro. The full plan lives alongside the code as a written `SCRIPT.md` (voice-over + timing) and `STORYBOARD.md` (beats, palette, and shot direction), so the narrative intent is version-controlled with the frames.

It targets 1920×1080 at 30 fps and is orchestrated by a master timeline in `index.html` that sequences four sub-compositions plus a synchronized caption overlay.

## Features

- **Master timeline orchestration** — `index.html` mounts sub-compositions via `data-composition-src` and drives them from a single paused GSAP timeline registered on `window.__timelines`.
- **Four sequenced scenes** — `intro`, `skills-cloud`, `terminal`, and `outro`, each a self-contained HTML composition under `compositions/` (with an additional `dev-split` scene available).
- **Animated terminal sequence** — a stylized terminal that types out the `npx skills add` install flow.
- **Timed caption overlay** — a data-driven captions array fades cue text in and out in sync with the timeline.
- **Deterministic rendering** — no `Date.now()`, `Math.random()`, or network fetches in the animation logic, so every render is frame-for-frame reproducible.
- **Documented narrative** — `SCRIPT.md` and `STORYBOARD.md` capture the voice-over, timing table, color palette, and beat-by-beat direction.

## Tech Stack

- **HyperFrames** (HeyGen) — HTML-as-video framework; config in `hyperframes.json`, metadata in `meta.json`
- **GSAP 3.14.2** — timeline and tween engine (loaded via CDN)
- **HTML5 / CSS3** — layout, styling, and per-scene compositions
- **Google Fonts** — Outfit and JetBrains Mono
- **heygen-com/skills** — AI-agent skills pinned in `skills-lock.json` for authoring the compositions

## Getting Started

The project is rendered and previewed through the HyperFrames CLI (run via `npx`, no install step required):

```bash
# Preview in the browser studio editor
npx hyperframes preview

# Validate all compositions (errors + warnings)
npx hyperframes lint

# Render the composition to MP4
npx hyperframes render
```

## Project Structure

```
.
├── index.html            # Master composition — root timeline + captions
├── compositions/         # Sub-compositions mounted by the master
│   ├── intro.html
│   ├── skills-cloud.html
│   ├── terminal.html
│   ├── outro.html
│   └── dev-split.html
├── SCRIPT.md             # Voice-over script + timing table
├── STORYBOARD.md         # Beats, palette, and shot direction
├── meta.json             # Project metadata (name, duration, resolution, fps)
├── hyperframes.json      # HyperFrames project config
├── skills-lock.json      # Pinned authoring skills
├── AGENTS.md / CLAUDE.md # Agent authoring guidance
└── .agents/ , .kiro/     # Installed HeyGen authoring skills
```

---

Built by [nickthelegend](https://github.com/nickthelegend) · [nickthelegend.tech](https://nickthelegend.tech)

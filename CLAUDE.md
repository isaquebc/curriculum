# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static HTML/CSS personal portfolio website for Isaque Benevides Costa (full-stack developer). No build process, no dependencies, no package manager — just open `index.html` in a browser.

**Owner:** Isaque Benevides Costa  
**Goal:** Job search — targeting well-paid remote/international and Brazilian senior roles (Full Stack Developer, CTO/Tech Lead)  
**Last updated:** April 2026 (after 5-year CDI GlobalTrack tenure ended)

## Architecture

The entire site is two files:

- **[index.html](index.html)** — All content hardcoded in HTML: profile, work experience timeline, projects list, skills section, and contact info
- **[style.css](style.css)** — All styling: layout, typography, responsive design, experience timeline, component styles

Assets live under [assets/](assets/):
- `assets/images/` — Profile photo (`IsaqueCosta-68.jpg`), project logos (including `gt-logo.svg` for CDI, `sementes-logo.svg`), skill icons
- `assets/files/` — PDF resume (currently outdated — from 2019, needs replacement)

## Content Structure

### Sections (in order)
1. **Profile (`#profile`)** — Photo, name, title, social links, bio
2. **Work Experience (`#experience`)** — Vertical timeline with 3 entries (newest first)
3. **Projects (`#projects`)** — Horizontal-scroll cards, 10 projects
4. **Skills (`#knowledge`)** — 4 subsections: Frontend, Backend, DevOps/Cloud, Other/Background
5. **Contact (`#footer`)** — GitHub, LinkedIn, WhatsApp

### Bilingual System (PT / EN)
The site is bilingual. Language is toggled by clicking the `PT | EN` button in the nav.

- `<body data-lang="pt">` — default language attribute on `<body>`
- Bilingual text uses paired `<span class="lang-pt">` / `<span class="lang-en">` siblings
- CSS hides the inactive language:
  ```css
  .lang-en { display: none; }
  [data-lang="en"] .lang-pt { display: none; }
  [data-lang="en"] .lang-en { display: inline; }
  ```
- A small inline `<script>` at the bottom of `<body>` toggles `document.body.dataset.lang`
- When adding new bilingual content, always provide both `lang-pt` and `lang-en` spans

### Work Experience Timeline
Each entry in `.timeline` is a `.timeline-item` containing:
- `.timeline-dot` — decorative dot
- `.timeline-card` — card with `.timeline-header`, `.company-name`, `.timeline-location`, `.timeline-bullets`, `.tech-tags`

Current entries:
1. **CDI GlobalTrack** — Senior Full Stack Developer — Mar 2021–Apr 2026 — Oklahoma, USA (remote)
   - Django + React + TypeScript + PostGIS + WebSockets + RxDjango + Docker + AWS + Prometheus/Grafana
2. **ACE1** — CTO — 2019–2021 — Brazil
   - React Native + Serverless AWS (Lambda) + Node.js — marketplace competing with GOAT/StockX
3. **TheVelops** — Tech Lead (started as trainee) — 2017–2019 — Brazil
   - React + Node.js + MongoDB + AWS — startup agency, flagship project: Permuta Fácil

### Projects (horizontal scroll)
Each `.project-item` has: logo/image, title label, `.content` with role, `.description`, optional links.

Current projects (in order):
1. CDI GlobalTrack — gt-logo.svg (local)
2. Sementes — sementes-logo.svg (local) — Next.js + Strapi social impact platform
3. CIB Style — `<h5 class="cib-title"><//>` — npm: @alphorriese/cib-style
4. SOM — round-black-image class
5. ACE1
6. Permuta Fácil
7. Consorciei
8. ARCA
9. Cento e Onze (111) — centoeonze class
10. agroTechs — agro-image class

### Skills (4 subsections)
- **Frontend:** React, Next.js, React Native, TypeScript, Redux, GraphQL, Apollo.js, webpack, ES6
- **Backend:** Django, Node.js, Python, Express, FastAPI, PostgreSQL, MySQL, MongoDB, Redis, Socket.io
- **DevOps / Cloud:** Docker, AWS EC2, S3, Lambda, API Gateway, ECR/ECS, Route 53, CodePipeline, GitHub Actions, Prometheus, Grafana
- **Other / Background:** C, C#, Java EE, Linux, MySQL, Entrepreneurship

**External dependencies loaded at runtime:**
- Google Fonts (Source Code Pro) via `fonts.googleapis.com`
- Google Analytics (`gtag.js`, ID: `UA-134482175-1`)
- Skill/social icons from `cdn*.iconfinder.com`, `cdn.worldvectorlogo.com`, and other CDNs

## Background / Career Context

Full career timeline (for content decisions):
- 2013: Started programming in college
- 2017: First internship at TheVelops
- 2017–2019: TheVelops (trainee → junior → tech lead). Startup agency serving multiple startups. Key projects: Permuta Fácil, Consorciei, ARCA, SOM, 111, agroTechs, ACE1 (client).
- 2019–2021: ACE1 — CTO. Brazilian luxury-goods marketplace (competing with GOAT/StockX). React Native iOS+Android, serverless AWS, zero infra cost for 2 years.
- Mar 2021 – Apr 2026: CDI GlobalTrack — Senior Full Stack Developer. Oklahoma (USA) company, remote. Enterprise pipeline pigging inspection platform. Django 5.1 + React 18 + TypeScript + PostGIS + WebSockets + RxDjango + Docker + GitHub Actions CI/CD + AWS + Prometheus/Grafana monitoring.
- Personal projects (ongoing): Sementes, Compartilhaê, CIB Style (published npm), RoboTrader, Minha Kaya, ABM/Aucthoria Digital

Other projects at `/home/isaquebc/theVelopment/`:
- `cdi/` — Full CDI GlobalTrack codebase (monorepo: Django backend, React frontend)
- `sementes/` — Sementes platform (Next.js + Strapi)
- `cib-style/` — CIB Style component library (React + TypeScript + Storybook)
- `money/compartilhaae/` — P2P item lending marketplace (Next.js + Django)
- `cripto/bot_cripto/` — Binance trading bot (Python)
- `abm/aucthoria-digital/` — Enterprise app (Next.js + Prisma + Stripe)

## Development

No install step. To preview locally, open `index.html` directly in a browser or serve with any static file server:

```bash
python3 -m http.server 8080
```

No tests, no linter, no build commands.

## TODO
- Replace PDF resume (`assets/files/`) — current one is from 2019
- Add CDI GlobalTrack website link to the project card when/if available

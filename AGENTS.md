# AGENTS.md — naina-site

Public landing page for **Naina Rao**, an openly-AI lifestyle creator, used as the flagship
proof for **Personae** (Everfold Labs service: brand-owned AI creators, built and run for
brands). Live on GitHub Pages; low-churn marketing page. **This repo is PUBLIC.**

## Stack & layout
Plain static HTML, no build step, no package manager, no `.gitignore`.
- `index.html`: the whole site (hero, services, gallery, how-it-works, compliance, booking CTA); only external dep is Google Fonts
- `naina.jpg` (hero portrait), `promo.mp4` (embedded promo), `gallery/` (images shown on the page)
- `media/posts/ig-ready/`: month-1 social post images hosted for posting; not referenced by `index.html` but published with the site, so do not delete or rename them
- `ci/site_check.py`: CI link/asset checker and stager

## Setup
None. Needs `python3` (3.12+) and `node` (checker runs `node --check` on any JS files).

## Run / build / test / lint
- Preview: `python3 -m http.server 8000` (unverified)
- Check (what CI runs; stage outside the repo, since there is no `.gitignore` for `_site/`):
  `python3 ci/site_check.py --repo naina-site --output /tmp/naina-site-_site` (verified 2026-10-11).
  It refuses an existing output dir; delete it before re-running.

## Environment variables
None required.

## Codex cloud environment
- Setup script: `python3 --version && node --version` (nothing to install)
- Internet during agent phase: off is fine
- Secrets to add: none

## Deployment (do not break)
- GitHub Pages, default branch is **`master`** (not main). URL: https://kaustubhtripathi-code.github.io/naina-site/
- `.github/workflows/ci-cd.yml` checks every push/PR and deploys with `actions/deploy-pages`
  only from `master`. A push to `master` = live. Do not push to `master` without owner
  approval; use a branch + PR. Do not edit the workflow or `ci/` unless asked.

## Rules for agents
- Naina is AI and the page says so. Keep the "openly-AI" / "fully AI-disclosed" framing on
  every surface (title, meta/og descriptions, copy); never present her as a real person.
- Keep the Everfold Labs attribution link and the existing contact mailto (plain address, no `+alias`).
- Large binaries (images, mp4) are committed directly; keep new media reasonably sized and
  referenced with relative paths (the checker fails on missing assets).

## Open work
- None recorded. `ci/portfolio-20260907` is already merged into `master`.

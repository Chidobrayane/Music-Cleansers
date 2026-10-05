# AGENTS.md

## What this repo is
A single-page static site: `index.html` (all HTML, CSS and JS inline). No build step, no package manager, no backend.

## Running it
`docker compose -f docker-compose.base44.yml up -d` — serves the repo root read-only through nginx on host port 3000.

- No dependencies to install; there is no manifest or lockfile.
- No credentials/secrets: the app runs entirely in the browser. It pulls its runtime libraries from public CDNs (`cdnjs.cloudflare.com` for lamejs, `cdn.jsdelivr.net` for `@huggingface/transformers` and `mediabunny`), and speech recognition/audio processing happen client-side.
- Audio files are never uploaded; anything that touches user audio stays in the browser.

## Editing
There is no dev server / live reload: edits to `index.html` are visible after reloading the preview.
When an HTML/CSS/JS change must show up, reload the preview page.

## Verification
`curl -sfI http://localhost:3000/index.html` should return 200. `docker compose -f docker-compose.base44.yml ps` should report the `web` service healthy.

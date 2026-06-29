# AGENTS.md

Static marketing landing page for the **NFT Sales Alert** Android app. No build step, no framework, no package manager, no tests.

## Deploy

- Hosted on **GitHub Pages** serving straight from the repo root. Remote: `github.com/paputechxyz/NftSalesAlertWebsite`.
- `CNAME` pins the custom domain `nftsalesalert.com`. Pushing to the default branch is the deploy — there is no CI pipeline and nothing else runs.
- To preview locally, open `index.html` directly in a browser; no dev server is needed (and none is configured).

## Structure / critical gotchas

- Two HTML pages only: `index.html` (landing) and `privacy-policy.html`.
- All live styling lives inline in a `<style>` block inside `index.html`; CSS custom properties under `:root` are the design tokens. There is no separate stylesheet.
- All page JS is inline at the bottom of `index.html`, including the `<canvas>` 3D ocean-wave mesh animation in the banner — that canvas is the centerpiece visual, edit carefully.
- Assets live in `public/` and are referenced via absolute paths like `public/logo.png`. This works *because* Pages serves from the repo root; do not "fix" these to relative paths.
- External CDN deps (no install): Font Awesome 6.4.0, Google Fonts (Inter), Firebase JS SDK 12.6.0.

## Analytics

- `index.html` wires up both **Google Analytics** (`G-PVL8NYK2J7`, via `gtag`) and **Firebase Analytics**. The `firebaseConfig` block is committed inline — these are public web client identifiers by design, not secrets. Do not scrub them.

## Content links (don't change without reason)

- Web app: `https://app.nftsalesalert.com/`
- Google Play: package `com.paputechxyz.openseasales`
- Contact: `paputechxyz@gmail.com`

## Verification

There is no lint, typecheck, or test command — do not invent one. After edits, visually reload `index.html` in a browser and confirm the banner animation, scroll reveals, and Google Play CTAs still work.
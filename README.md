# N > 1 — landing page

Static landing page for **NGTOne** (N > 1) — a vertically integrated software-and-clinical-evidence
company. Single-file site presenting the thesis to prospective co-founders, board members, and investors.

## Contents

- `index.html` — the complete landing page. Self-contained: all CSS inline, no JavaScript; the only
  external dependency is Google Fonts.

## Local preview

No build step. Open `index.html` directly, or serve it:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

## Call to action

There is no form and no backend — the page is fully static. The single CTA links to the founder's
X (Twitter) DMs (opens in a new tab; "DMs open"):

```
https://x.com/pwidden
```

To change it, edit the one `<a class="btn btn-primary x-cta" href="…">` in the `#contact` section of
`index.html`, plus the `.form-note` line (`DMs open · @pwidden on X`) beneath it.

## Deploy

Hosted on **GitHub Pages** from this repo (`ngtonehq/ngtone`). Single static file — no build step, no
config; `index.html` at the repo root is the entry point.

Pages serves the default branch (`main`). After pushing, enable it once under **Settings → Pages**
(source: `main` / root). Custom domain `ngtone.com` goes in that same panel (writes a `CNAME` file),
with DNS pointed at GitHub Pages.

Notes:
- GitHub Pages publishes from a **private** repo only on a paid plan; on the free plan the repo must be
  public. The published page is public either way — it's `noindex, nofollow` by intent.
- `VISION.md` is not in this repo (it lives at the project root, outside `web/`), so it is never published.

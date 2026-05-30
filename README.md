# N > 1 — landing page

Static landing page for **NGTOne** (N > 1) — a vertically integrated software-and-clinical-evidence
company. Single-file site presenting the thesis to prospective co-founders, board members, and investors.

## Contents

- `index.html` — the complete landing page. Self-contained: all CSS and JS inline, only external
  dependency is Google Fonts.

## Local preview

No build step. Open `index.html` directly, or serve it:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

## Contact form

The contact form POSTs JSON to an [n8n](https://n8n.io) webhook, which handles the email send to
`paul@ngtone.com`. The webhook URL is set once in `index.html`:

```js
var WEBHOOK_URL = "https://ngtone.app.n8n.cloud/webhook/contact";
```

Confirm this path matches your n8n Webhook node's **Production URL**, and that the workflow:

1. Responds with an `Access-Control-Allow-Origin` header (your domain or `*`).
2. Handles the `OPTIONS` preflight request.

Payload shape:

```json
{ "name", "email", "organization", "role", "message", "source", "submitted_at" }
```

> Note: the webhook URL is visible in client-side source — that's expected for a public form endpoint.
> Keep auth/secrets in the n8n workflow, never in this file.

## Deploy

Any static host works (Vercel, Netlify, Cloudflare Pages, GitHub Pages). Point it at the repo root;
`index.html` is the entry point.

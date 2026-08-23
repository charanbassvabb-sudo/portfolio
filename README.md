# charan-basava.dev — Portfolio

Personal portfolio for Charan Basava — full-stack developer and security-minded
Computer Science student (BSc Computing & Cybersecurity, University of Greenwich).

Static site, no build step. One `index.html`, one photo, one CV PDF.

## What's on it

Every project linked from this page is real and verifiable:

- **[Indish](https://indishzambia.com)** — live restaurant + loyalty platform for a
  real two-branch business. [Source](https://github.com/charanbassvabb-sudo/Indish-loyalty-dashboard-and-website)
- **CipherVault** — FastAPI password manager, dissertation project.
  [Source](https://github.com/charanbassvabb-sudo/CipherVault)
- **[Basava Group](https://basavagroup.org)** — live business website.
  [Source](https://github.com/charanbassvabb-sudo/Basava-website)

The "live github stats" panel in the hero calls the public GitHub REST API
client-side (`api.github.com/users/charanbassvabb-sudo/repos`) and falls back
to the static numbers already in the markup if the request fails or is rate
limited — nothing breaks if GitHub is unreachable.

## Running it locally

No build step — just open `index.html` in a browser, or serve the folder:

```bash
npx serve .
```

## Deploying (for the contact form to actually work)

The contact form uses **Netlify Forms** (`data-netlify="true"` on the `<form>`),
which only works once the site is deployed on Netlify — Netlify's build step
scans the deployed HTML for the form and wires it up automatically. No backend,
no API keys, no third-party form service needed.

1. Push this repo to GitHub (already done if you're reading this from there).
2. On [netlify.com](https://netlify.com) → **Add new site → Import an existing
   project** → pick this repo. Build command: none. Publish directory: `.`
3. Deploy. Submissions land in **Site settings → Forms** in the Netlify dashboard,
   and can be forwarded to email from there.

If the site is hosted anywhere else (GitHub Pages, etc.), the form will fail
its POST and the page shows a friendly fallback pointing to direct email —
it won't silently pretend to succeed.

## Before you point a real domain at this

- Update `og:image`/`og:url` in `<head>` to absolute URLs once the domain is final.
- `netlify.toml` sets a few baseline security headers (`X-Frame-Options`,
  `X-Content-Type-Options`, `Referrer-Policy`) — adjust if you add other hosts.

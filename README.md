# pragmatic-docs

Public documentation for the **Architecture Agentic Suite** (`pragmatic-tech-ai`): TODL, todl-runtime, Mural,
Fresco and Plexus. The published site is **<https://docs.pragmatic-tech.ai/>**. It's rebuilt on every push to
`main` that touches `docs/**`.

The site moved here from `dev-kit` on 2026-11-18 (copied from dev-kit@d5f63a6; earlier history is in dev-kit,
which is now private). Internal design specs and plans stay in `dev-kit` and are not published.

## How it works

The docs are plain Markdown under [`docs/`](docs/). GitHub's
[`jekyll-build-pages`](https://github.com/actions/jekyll-build-pages) action renders them with the github-pages
gem, and [`.github/workflows/deploy-docs.yml`](.github/workflows/deploy-docs.yml) publishes the result. No npm,
no package registry, no secrets. Pages Markdown without front matter renders as-is, and relative `.md` links
become page URLs.

## Adding docs

1. Add or edit Markdown under `docs/`.
2. Link it from [`docs/index.md`](docs/index.md).
3. Push to `main`. The workflow rebuilds and deploys.

**Never publish internal material here.** That means infrastructure, designs, plans and anything with
addresses or account details. This repository and its site are public.

## Removal tickets

Readers can select text on a page and file a `docs-removal` ticket.
[`docs-removal.yml`](.github/workflows/docs-removal.yml) runs the
[docs-removal agent](.github/agents/docs-removal.agent.md) to remove the flagged text and close the ticket.

## Setup (already done)

- **Pages:** **Settings → Pages → Source = "GitHub Actions"**, custom domain `docs.pragmatic-tech.ai` (file
  `docs/CNAME`), HTTPS enforced.
- **DNS:** Cloudflare `docs` CNAME → `pragmatic-tech-ai.github.io`, not proxied.

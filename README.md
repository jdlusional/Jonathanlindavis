# jonathanlindavis.com

Personal site for Jonathan Lin Davis — researcher, author, consultant, and strategist.
Static HTML/CSS/JS, no build tools or bundlers, hosted on Cloudflare Pages (auto-deploys
on push to `main`). Contact form and newsletter signup run through Cloudflare Functions
(`functions/api/`).

See `CONTEXT.md` for full orientation — project map, conventions, and standing rules.
Read that first if you're picking up work here.

## What's here

- **Personal site pages** — `index.html`, `about.html`, `writing.html`, `projects.html`,
  `contact.html`, `newsletters.html`, `house-rules.html`,
  `ten_issues_90th_legislature.html`.
- **GIFT** (`gift.html`) — the Grand Index of Funders in Texas, a free search index of
  private foundations and public charities built from public IRS filings. Data workspace
  lives outside this repo in `Jonathanlindavis General\GIFT subfolder (files not
  website)`.
- **F4F** (`f4f.html`) — Fellowships4Free, a free index of graduate and early-career
  fellowships. As of 2026-07-01 this is self-hosted here (`data/fellowships.json` +
  `.csv`) rather than fetching from fellowship4free.com — that domain is being retired in
  favor of maintaining everything on this repo. Working files (staged additions not yet
  merged into the live dataset) live outside this repo in `Jonathanlindavis General\F4F
  subfolder (files not website)`.
- **NPA Job Board** (`npa-job-board.html` + related pages) — job board app.
- **Unlisted pages** — reachable by direct link only, not in nav/sitemap, blocked via
  `robots.txt` and `noindex` meta tags:
  - `/kct` — Katelyn C. Thompson site (client work)
  - `/llopensecrets` — Vanderbilt LLO EdD cohort profiles
  - `/testing` — internal staging page for previewing in-progress work (tabbed iframe
    interface)

  See `CONTEXT.md`'s "Unlisted-page convention" for the full pattern, including a
  case-sensitivity routing gotcha worth reading before adding another one.

## Conventions

- **Testing-page-first:** for site changes, verify in `/testing` before it's considered
  live (for pages that have a dedicated live URL, direct edits are fine since the page
  *is* the live site).
- **Branch preview for visible changes:** push to a branch, share the Cloudflare Pages
  preview URL (`https://<branch>.jonathanlindavis.pages.dev`), then merge once approved.
  Small technical fixes can go straight to `main`.
- **Working files stay out of the repo:** anything not meant to ship (staging data,
  scratch extracts, review queues) lives in a sibling `<Project> subfolder (files not
  website)` folder, never committed here.

Full detail on all of the above in `CONTEXT.md`.

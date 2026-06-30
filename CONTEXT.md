# Web Domain Sites — Context File for Claude Code

This file lives at the root of the Web Domain Sites folder and gives Claude Code
a complete orientation to all projects here. Read this at the start of any session.

---

## Owner

**Jonathan Lin Davis** — researcher, author, consultant, and strategist.
Austin, Texas. Email: jdavis92105@gmail.com.

---

## Project Map

| Project | Folder | Live URL | Host |
|---|---|---|---|
| Personal site | `Jonathanlindavis General\Jonathanlindavis.com` | jonathanlindavis.com | Cloudflare Pages |
| Consulting firm | `Microgroup.info General\Microgroup.info` | microgroup.info | Cloudflare Pages |
| Fellowship index | `fellowship4free General\fellowship4free.com` | fellowship4free.com | GitHub Pages |
| GIFT data workspace | `Jonathanlindavis General\GIFT subfolder (files not website)` | (no domain; outputs go to jonathanlindavis.com/gift.html) | local only |
| KCT client assets | `Katelyn C Thompson General` | (no domain; mockups hosted on jonathanlindavis.com/testing.html) | N/A |

---

## GitHub Repository Structure

**Primary repo:** `github.com/jdlusional/Jonathanlindavis`
- Hosts all jonathanlindavis.com content and deployments
- Deployed to Cloudflare Pages (auto-deploy on push to main)
- Contains: gift.html, gift_*.json files, gift_exclusions.json, excluded_funders.csv, CSS, JS, assets

**GIFT data workspace:** Local git repo in `GIFT subfolder (files not website)`
- Separate from Jonathanlindavis repo (for data processing)
- Contains Python scripts, parquet index, XML fetches, build outputs
- Output files copied to Jonathanlindavis repo for deployment
- No remote (local workspace only)

**Other repos:**
- `fellowship4free.com` — GitHub Pages hosted (CC-BY-4.0 data, MIT code)
- `Microgroup.info` — Cloudflare Pages hosted

**Deployment workflow:**
1. Edit files in GIFT subfolder (data workspace)
2. Copy output files (gift.html, gift_*.json, exclusions, etc.) to Jonathanlindavis folder
3. Commit to Jonathanlindavis repo on main branch
4. Cloudflare Pages auto-deploys on push
5. Live at jonathanlindavis.com/gift#/

**Testing-page-first workflow:**
- All GIFT changes staged at jonathanlindavis.com/testing.html (noindex)
- Verify in browser before considering live
- Individual project repos (F4F, etc.) pull from jonathanlindavis.com copies when needed

---

## 1. jonathanlindavis.com

**Folder:** `Jonathanlindavis General\Jonathanlindavis.com`

Static HTML site hosted on Cloudflare Pages. Shared design system across all pages.

### Key files
- `index.html` — homepage (hero, three-arena directory, footer)
- `about.html` — bio and background
- `writing.html` — writing / Substack
- `projects.html` — projects directory
- `contact.html` — contact form (Cloudflare Function backend)
- `newsletters.html` — newsletter archive
- `testing.html` — internal testing page, noindex; tabbed iframes for all project previews
- `house-rules.html` — House Rules project landing page
- `ten_issues_90th_legislature.html` — House Rules full app (large standalone HTML)
- `f4f.html` — Fellowships4Free app (mirrored here for same-origin iframe embedding)
- `gift.html` — GIFT app (Grants Index For Texas)
- `kct-mockups-v2.html` — Katelyn C. Thompson website design mockups v2 (hero + slideshow)
- `style.css` — shared stylesheet for all pages
- `site.js` — shared JS (nav toggle, chevron scroll, footer year, etc.)
- `Assets/` — headshot.jpg, house-rules-cover.jpg, writing-cover.jpg, gift-cover.png, f4f-logo.png, micro-mark.svg, linkedin.png, substack.png, jd-mark.svg (favicon), micro-mark.svg
- `functions/api/` — Cloudflare Functions: contact.js, subscribe.js

### Design tokens (from style.css)
- Fonts: Bitter, Cormorant Garamond, Barlow Semi Condensed, Marcellus, Cinzel, Parisienne, Michroma, Libre Franklin (Google Fonts)
- Color scheme: navy + gold on warm backgrounds; chess texture background pattern on panels
- CSS vars: `--navy`, `--gold`, `--gold-soft`, `--paper`, `--muted-light`, `--line-navy`, `--navy-card`, etc.
- Layout: full-viewport snap panels (`.panel.navy.chess`), `.wrap.inner` for content width
- Components: `.eyebrow`, `.btn`, `.xcard` (expandable details), `.chevron` scroll button, `.footer-panel`

### Google Analytics
- Tag ID: `G-08J22J0DXL`

### Testing page pattern
`testing.html` uses a tabbed interface (`.test-tab` / `.test-panel`) with iframes.
To add a new artifact: add a `<button class="test-tab">` to the tablist and a
`<div class="test-panel">` with an `<iframe class="test-frame">` pointing to the file.
The page is noindex and not linked from the nav.

Current tabs: House Rules, NPA Job Board (4 views), Fellowships4Free, GIFT, KCT Mockups.

---

## 2. microgroup.info

**Folder:** `Microgroup.info General\Microgroup.info`

MICRO Group, LLC — Jonathan's consulting business. Static HTML, Cloudflare Functions.

### About MICRO Group
"A multi-service consultancy dedicated to serving nonprofit, education, and government
institutions through expertise in Management, Integration, Culture, Research, and Operations."
Mailing address: 1801 E 51st St., STE 365, PMB 354, Austin, Texas.

The name MICRO is an acronym: Management, Integration, Culture, Research, Operations.

### Key files
- `index.html` — homepage (hero with logo, five-discipline medallions, mission/vision/values/approach quad, footer)
- `contact.html` — contact form
- `style.css` — site stylesheet (shares many conventions with jonathanlindavis.com)
- `site.js` — shared JS
- `contact.js` — Cloudflare Function for contact form
- `king-mark.svg` — favicon (king chess piece mark)
- `MICRO_logo_navy.svg`, `MICRO_logo_green.svg` — primary logo variants
- `MICRO_wordmark_dark.svg` — footer wordmark

### Logos (Active Logos folder)
Full brand asset set in `Active Logos/`: lockup (light/dark), square (light/dark),
icon (light/dark), in SVG and PNG. Old Logo subfolder has prior brand versions.

### Google Analytics
- Tag ID: `G-4J4XGXZ4CN`

---

## 3. fellowship4free.com

**Folder:** `fellowship4free General\fellowship4free.com`

Free, public, open-data index of graduate and early-career fellowships. Hosted on GitHub Pages.

### What it is
"Because finding money shouldn't cost you money." No-paywall alternative to
membership-gated fellowship databases. Data is CC-BY-4.0, code is MIT.
Seeded with 93+ fellowships across AI policy, public policy, nonprofit governance,
education, data analysis, and more.

### Architecture
- `index.html` — single-page app; loads `data/fellowships.json` in the browser;
  search, filter, sort, CSV/JSON export; no backend
- `data/fellowships.json` + `data/fellowships.csv` — the dataset
- `pending/candidates.json` — queue of candidates awaiting review
- `scripts/` — Python pipeline scripts
- `.github/workflows/` — GitHub Actions (weekly import cron + Pages deploy)
- `assets/` — logos and favicon

### Weekly pipeline (automated)
Monday cron: `fetch_candidates.py` reads RSS/Atom feeds (no scraping, robots.txt honored),
keyword-filters for fellowship items, sweeps expired pending candidates, queues up to 25
ranked by deadline urgency. Opens a GitHub Issue for review. You approve up to 10 per week
via `approve_candidates.py`, then push to main to redeploy.

### Data schema
`id, organization, fellowship, url, area, type, funded, duration_months, opens,
deadline, next_cohort, flag, description, terms, contact, notes, added, source`

### Logos (Active F4F Logos folder)
SVG and PNG variants: lockup (light/dark), square (light/dark), icon (light/dark),
favicon at 32px and 64px.

---

## 4. GIFT data workspace

**Folder:** `Jonathanlindavis General\GIFT subfolder (files not website)`

This is NOT a website folder. It is a data processing workspace with its own git repo
and CLAUDE.md. The output goes to `jonathanlindavis.com/gift.html`.

### What GIFT is
GIFT (Grant Index of Funders in Texas) — a free funder index built from public IRS filings for
tax year 2023. Top 100 private foundations + top 100 public charities (ranked separately),
10,259 recipients. Everything traced to public IRS filings. Data from ProPublica and the
GivingTuesday Data Lake.

### Key data files (large, do not open without reason)
- `gift_funders.json` (62 KB) — funder list
- `gift_funder_detail.json` (3 MB) — funder detail pages
- `gift_recipients.json` (5 MB) — recipient list
- `gift_recipient_detail.json` (3 MB) — recipient detail pages
- `gift_edges.csv` (2 MB) — grant edges (funder -> recipient)
- `gift_exclusions.json` — coded exclusion roster with bases A-E
- `excluded_funders.csv` — enhanced download with comprehensive basis info
- `index_all_years_efiledata_xmls_created_on_2026-06-04.parquet` (1.3 GB) — IRS XML index

### Python scripts
Build scripts: `build_json5.py` (current builder), `build_excluded_audit.py`, etc.
Fetch scripts: `fetch_xml.py` (funder XML), `fetch_recipient.py` (recipient 990 XML)
Parse scripts: `parse_grants_full.py`, `extract_recipient_total.py`, etc.
Utility/check scripts: `check_*.py`, `inspect_*.py`, `diagnose_*.py`, etc.

For GIFT working instructions, read the CLAUDE.md in that folder. Key convention:
"Tool: Python | Location: [full path]" headers on every code execution instruction.

### GIFT UX improvements (as of 2026-06-30)

**Homepage redesign:**
- Centered GIFT SVG logo with branding ("Grant Index of Funders in Texas")
- Fading search label mechanism: "Find who funds organizations like yours" ↔ "Find who does the work you support" (4s cycle)
- Cycling keywords under description: "Who they give to", "Why they give", "How much they give", "Where they give" (15s total, 3s intervals)
- Centered all content: hero text, search block, tabs, ledger
- Max-width constraints for optimal readability

**Directory pages (recipients & funders):**
- Centered layout with max-width constraints
- Search bar centered with 600px max-width
- Centered controls and listings
- Individual profile pages remain left-aligned

**Recipient pages:**
- All funder names linked to funder profiles (lookup by name if EIN unavailable)
- Mission statements converted to sentence case (first letter capitalized only)
- Automatic conversion of all-caps text to readable format

**Exclusion roster system (integrated A-E coding):**
- **Codes A-E** map directly to the 5 exclusion bases:
  - A = Closed loop to a controlled entity
  - B = Closed certified or membership network
  - C = Operator or conduit
  - D = In kind rather than cash
  - E = No researchable public identity
- One integrated "What gets excluded, and why" section showing basis descriptions + codes
- Codes are clickable to highlight in roster (yellow background, centers on page)
- Full roster shows all organizations with all applicable codes (e.g., Trinity Christian Academy: A;D)
- Organizations can have multiple codes if they meet multiple exclusion criteria
- **Enhanced CSV download:**
  - CODE column (A-E, semicolon-separated for multi-basis)
  - EXCLUSION_BASIS column (full descriptions)
  - REASON column (comprehensive: basis description + specific details)
  - Provides complete context for research and verification

### Current state (as of 2026-06-30)
Recipient-side totals work complete. Full UX redesign and exclusion system integrated.
The gift.html SPA is live on jonathanlindavis.com with all improvements.
See CLAUDE.md for the locked method and decided parameters.

---

## 5. KCT client work (Katelyn C. Thompson)

**Folder:** `Katelyn C Thompson General`

NOT a repo. This is a client asset folder for website work for Katelyn C. Thompson,
a Tennessee policy and communications leader.

### About the client
- Name: Katelyn C. Thompson
- Domain: Public Policy and Strategic Communications, Tennessee
- Tagline: "Turning ideas into action."
- Description: "A Tennessee policy and communications leader who turns complex challenges
  into people-centered solutions."
- Bio reference: `Thompson. K Quick Bio.pdf`
- Copy reference: `KCT Snippets.docx`

### Photo assets
KCT1-7.JPG (original shoots), KTC8.jpg, KCT10.png (upscaled/sharpened for hero),
KTC111.png (portrait, used in slideshow), KTC12.png (portrait, used in slideshow).

### Design work
Website mockups v2 (`kct-mockups-v2.html`) — self-contained HTML with embedded
base64 images (~1 MB). Contains:
- Hero section: full-body portrait (KCT10) with header "KATELYN C. THOMPSON",
  eyebrow "Public Policy · Strategic Communications", h1 "Turning ideas into action.",
  supporting copy. Photo + message together form one full viewport.
- Slideshow: full-height horizontal sliding carousel, 3 portrait photos (KTC111, KTC12, and one other),
  30s loop (6 frames, seamless), caption "The Policy Fashionista / Substance with sophistication."

Brand palette for KCT site:
- `--maroon: #6A1E29`
- `--bg: #EDEAE4`
- `--ink: #17171A`
- `--muted: #55534E`
- `--border: #D8D3CB`

Fonts: Cormorant Garamond (eyebrow), Playfair Display (headings), Source Serif 4 (body), Inter (labels/notes)

The mockup is currently viewable at jonathanlindavis.com/testing.html under the "KCT Mockups" tab.

---

## Shared conventions across sites

- All static sites use Cloudflare (Pages + Functions) or GitHub Pages
- All sites share similar font stacks (Cormorant Garamond is common across all three)
- No build tools or bundlers — plain HTML/CSS/JS files, no npm
- Contact forms use Cloudflare Functions (functions/api/contact.js pattern)
- Google Analytics on all live sites
- Testing / internal pages use `<meta name="robots" content="noindex, nofollow">`
- The jonathanlindavis.com testing.html is the staging ground for all new project work

## Working convention: testing-page-first workflow

**For any site change, first output to the testing page before touching the live file.**

- jonathanlindavis.com has iframe-embedded copies of all project apps (f4f.html, gift.html, etc.)
- Make changes to the jonathanlindavis.com copy first (e.g. `f4f.html`, `gift.html`)
- Confirm the result looks correct in testing.html under the appropriate tab
- Only then propagate the change to the live standalone repo (fellowship4free.com, etc.)
- For jonathanlindavis.com pages themselves, direct edits are fine since the page IS the live site

**For web items without a dedicated page (mockups, prototypes, tools):**
- Default to testing.html — do not create a new standalone page unless explicitly told to
- If a prior version exists in testing, copy the new file over it (e.g. replace `kct-mockups-v2.html`)
- If it's a new item with no existing tab, create a new tab in testing.html
- Confirm it's visible under the correct tab after deploying

---

*Last updated: 2026-06-30*

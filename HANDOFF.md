# Handoff

Last updated: 2026-09-05

## Project

`portfolio-test` — a placeholder personal portfolio site. Plain HTML/CSS/JS, no framework, no build step. Purpose: verify the git → GitHub → Vercel deploy pipeline works before real content is written.

- Repo: https://github.com/Psych0Ray/portfolio-test (branch `main`)
- Hosting: Vercel, connected to the GitHub repo, auto-deploys on push to `main`

## Files

- [index.html](index.html) — hero section (name + tagline), About, Projects (3 placeholder cards), Contact, footer
- [style.css](style.css) — minimal dark theme, responsive card grid
- [script.js](script.js) — one line, sets the footer copyright year

## Done so far

1. Built the initial one-page placeholder (hero + About + Projects + Contact + footer).
2. Initialized git repo locally, set local git identity (user.name "Rutujeet Nayak", user.email rutujeetnayak@gmail.com — repo-local config, not global).
3. Committed and pushed to `origin/main` on the new GitHub repo.
4. Updated hero title and footer from "Your Name" to "Rutujeet", committed and pushed — used to confirm the Vercel auto-deploy pipeline picks up pushes.
5. Added this handoff process (`CLAUDE.md` + `HANDOFF.md`).
6. Installed Node.js LTS (v24.19.0) on this machine — was previously missing entirely (no `node`/`npm`/`npx` on PATH in bash or PowerShell).
7. Installed the `taste-skill` plugin (marketplace: `leonxlnx/taste-skill`) — 13 frontend design-taste skills (brutalist, minimalist, soft, redesign, image-to-code, etc.), user scope, ~1.7k tok always-on.
8. Installed the `vercel-optimize` skill manually into `~/.claude/skills/vercel-optimize` (sparse-cloned from `vercel-labs/agent-skills`, not a native Claude Code plugin format — copied the skill folder directly). Needs Vercel CLI v53+, `vercel login`, `vercel link`, and ideally Observability Plus to be useful; dormant until the site has real production traffic.
9. Installed Playwright agent CLI (`@playwright/cli`, global npm install) + Chromium/Firefox/WebKit browsers + the Claude Code skill (`.claude/skills/playwright-cli`, project-scoped). Verified working: served the site locally on port 8080 (file:// URLs are blocked by the CLI) and screenshotted it — renders correctly. Found one minor issue: no favicon (404 on `favicon.ico`).
10. Installed GSAP 3.15.0 via CDN (SRI-pinned) in [index.html](index.html). Verified loading in a real browser (`gsap.version` → 3.15.0). No animations written yet — wired in only, per user's call.
11. Built 3 UI mockup iterations in Figma on the "Portfolio Ideations" page (file `uG8MdK8svbC6sa0wQ5kyIK`). Brief: red primary, frosted glass, premium/minimal, 6 work pieces directly after hero, custom cursor + hover states. Each iteration = one "Site UI" frame + one "Cursor & Hover States" frame, grouped in a Figma Section:
    - **Iteration 01 · Vault** — near-black `#0A0A0B`, vermilion `#E8402A`, Geist + Geist Mono. Asymmetric split hero with frosted-glass caption; bento work grid (rows of 2 / 3 / 1).
    - **Iteration 02 · Editorial** — cool paper `#EFEFED`, deep red `#C8102E`, Bricolage Grotesque + Geist. Typographic manifesto hero with filmstrip preview; staggered two-column work grid; full-bleed red contact block.
    - **Iteration 03 · Chroma** — `#08070A` with luminous `#FF3B2F`, Schibsted Grotesk + JetBrains Mono. Full-bleed chroma hero with floating glass nav + glass hero card; wave-offset three-column grid, glass caption on every tile.
12. Looked at (but did not install — it's not a plugin) `voltagent/awesome-design-md`: a reference library of ~100+ brand `DESIGN.md` style-guide files. Usage model: user picks a brand, we fetch that one file, I use it as a style spec. No action taken yet — waiting on user to pick a brand if they want this route for a future redesign.

## In progress / not yet confirmed

- Waiting on user to confirm the Vercel deployment actually updated after the last push (deployment trigger looked correct on the git side; visual confirmation on Vercel dashboard/live URL still pending).

## Next up (not started)

- **Awaiting user's pick of one of the 3 Figma iterations** (or a hybrid) before building the real site.
- Work tiles in all 3 Figma iterations use gradient placeholders, not real imagery — the Figma plugin API blocks `createImageAsync`, so real project images must be dropped in manually or the direction rebuilt with generated assets.
- Replace all placeholder content (name is set; tagline, About text, Projects, Contact still placeholders).
- Add a favicon (currently 404s, caught by the Playwright tooling — cosmetic only).
- Write the actual GSAP animations once a design direction is chosen.

## Notes for future sessions

- Git identity for this repo is set locally (not global) — if committing from a different machine/environment, identity will need to be set again.
- Line-ending warning (LF→CRLF) appears on git operations on Windows; harmless, not yet addressed with a `.gitattributes` — could add one if it becomes noisy.
- Node.js is now installed globally on this machine (not project-specific) — available for any future JS tooling needs.
- To visually check the site with Playwright: serve it over local HTTP first (e.g. a quick Node static server on a port), since `file://` URLs are blocked by the CLI by default.

## Vantage Landing Page — Plan

A single, polished landing page for the RenderException hackathon project **Vantage** — built in the existing TanStack Start stack, using the color language from `demo_page.html` (Aether scheme: near-black bg, green `#47E39B` = local vision, violet `#9B87FC` = cloud reasoning).

### Design direction
- Dark, dense, developer-tool aesthetic (ProjectDiscovery / Linear-adjacent, per the demo).
- Faint CSS grid + soft radial glows in green/violet on the hero.
- Mono for code/eyebrow labels (JetBrains Mono via `<link>` in `__root.tsx`), sans (Inter) for UI/body.
- Semantic tokens in `src/styles.css` under `@theme inline` + `:root` (oklch): `background`, `surface`, `border`, `foreground`, `muted-foreground`, `accent` (green), `violet`, `ok`, `warn`, `crit`. No hard-coded colors in components.

### Assets
- `RE-Logo.png` → `src/assets/re-logo.png.asset.json` via `lovable-assets` — shown small in the footer ("A RenderException project").
- `vantage.png` → `src/assets/vantage-logo.png.asset.json` — used as the navbar mark and as the favicon (`links` in root head).

### Page structure (single route: `src/routes/index.tsx`)
1. **Top nav** — Vantage mark + wordmark, anchor links (Features, How it works, Architecture, Team), GitHub button.
2. **Hero**
   - Eyebrow: `RENDEREXCEPTION · HACKATHON 2026`
   - H1: "Autonomous QA swarm for **Android** & mobile web."
   - Lede from the README overview.
   - Two CTAs: "View on GitHub" (ghost) + "Read the docs" (primary green).
   - Fact chips: `10 → 100 concurrent sessions`, `redroid`, `vision-model driven`, `Apache-2.0`.
   - Right side: a stylized "session card" mock (status dot, task prompt, device profile, agent action trace lines) rendered in pure CSS to hint at the product UI.
3. **Stat strip** — 4 tiles: Concurrent sessions, Action vocab size (7), Agent loop steps (5), Session statuses (7).
4. **Features grid** (6 cards, 3-col → 1-col responsive) — pulled verbatim-in-spirit from README Features: AI-driven agent loop, Ground-truth logcat monitoring, UI settle detection, Warm pool, Clean-state teardown, Live screen mirror + manual control.
5. **How it works** — 5 numbered steps (Observe → Decide → Act → Settle → Ground-truth check) as a horizontal/stepped layout with mono code snippets (`adb screencap`, `input tap x y`, etc.).
6. **Architecture** — ASCII diagram from the README rendered in a `<pre class="mono">` card, plus a components table (New Session Input, Scheduler, redroid pod, Agent sidecar, Dashboard, Storage).
7. **Input types** — two side-by-side cards: **APK** and **Web domain**, matching the README's two input modes.
8. **Build plan / Roadmap** — 7 phases as a vertical timeline with phase name + scope.
9. **Team card — RenderException** — RE logo, team name, one-line tagline, hackathon entry note.
10. **Footer** — repo link, license, small RE mark.

### Head metadata (`src/routes/index.tsx` `head()`)
- `title`: `Vantage — Autonomous QA swarm for Android & mobile web`
- `description`: from README overview (≤160 chars).
- `og:title`, `og:description`, `og:type: website`, `twitter:card: summary_large_image`.
- Favicon link → vantage logo asset URL.
- Override the root's placeholder title/description via `meta` (TanStack merges by name/property).

### Files touched
- **New**: `src/assets/vantage-logo.png.asset.json`, `src/assets/re-logo.png.asset.json`.
- **Edit**: `src/styles.css` (add Vantage token palette + `--font-mono`/`--font-sans` + `@utility grid-bg`), `src/routes/__root.tsx` (Inter + JetBrains Mono `<link>` tags, drop placeholder title/description defaults so leaf head wins cleanly), `src/routes/index.tsx` (full landing page — replaces the blank-app placeholder).
- **No** backend, routing, or business-logic changes. Frontend-only, static content sourced from the README.

### Out of scope
- No auth, no data fetching, no Lovable Cloud.
- No separate Dashboard/Session routes — this is a marketing landing page only.
- No design-direction exploration step: the demo_page palette is the spec.

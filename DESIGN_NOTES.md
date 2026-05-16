# joshua.penman.dev — Design Notes

_Last updated: 2026-05-16. These notes are for future agents picking up this work._

---

## Intent

This is Joshua's personal spot on the internet — not a portfolio, not a CV. It starts with four projects he's proud of and should feel personal, developer-authored, and honest. No stock-photo hero, no "I'm passionate about solutions," no corporate gloss.

---

## Current state

- **Repo**: https://github.com/KiwiGeek/kiwigeek.github.io  
- **Host**: GitHub Pages at https://joshua.penman.dev  
- **Mockup file**: `mockup.html` in the workspace root  
- **Status**: Mockup only — not yet deployed

---

## Projects covered

| Name | Repo | Live | Language | Accent colour | Platforms |
|---|---|---|---|---|---|
| Scriptoria | KiwiGeek/ChurchScribe | joshua.penman.dev/ChurchScribe/ | JS/CSS/HTML | `#c08a38` (warm amber) | Windows |
| MiraCLI | KiwiGeek/mira-cli | — | TypeScript / Node.js | `#22c55e` (terminal green) | Windows (full), macOS (partial) |
| BrainFudger | KiwiGeek/BrainFudger | — | C# | `#a78bfa` (soft purple) | Windows, macOS |
| AteChips | KiwiGeek/AteChips | — | C# / GLSL | `#22d3ee` (retro cyan) | Windows, macOS, Linux |

### One-liners approved for use
- **Scriptoria**: "Sermon & Bible study notes that never leave your browser."
- **MiraCLI**: "A terminal REPL for ChatGPT — no API key required."
- **BrainFudger**: "A Brainf*ck compiler that generates real native binaries."
- **AteChips**: "A CHIP-8 emulator with CRT shaders and a custom audio engine."

### Platform icons
Cards show a "Runs on" strip with small monochrome SVG icons for each supported platform:
- **Windows**: 4 filled squares in a 2×2 grid (universally recognisable)
- **macOS**: Simplified Apple silhouette
- **Linux**: Simplified Tux penguin (oval body + circle head)

Icons use `fill: currentColor` at 14×14px, coloured with `var(--text-dim)` to stay subtle.
They sit between the description and the footer separator line.

**Partial platform support**: when a platform works but isn't first-class (e.g. MiraCLI on macOS — functional but not as polished as Windows), the icon renders at `opacity: 0.45` with a `title` tooltip explaining the caveat. Full support = full opacity. This lets the distinction be visible at a glance without requiring any extra copy on the card.

---

## Design decisions

### Colour palette

```
Light mode
  --bg:         #f5f4f0   warm off-white (not pure white)
  --bg-card:    #ffffff
  --text:       #18170f   near-black with slight warmth
  --text-dim:   #6b6860
  --border:     #e2e0da
  --accent:     #1d4ed8   site wordmark accent

Dark mode
  --bg:         #111009   near-black, slight warm undertone
  --bg-card:    #1b1a14
  --text:       #e5e3db
  --text-dim:   #8a8780
  --border:     #282720
  --accent:     #60a5fa
```

### Typography
- Body: system-ui stack (`-apple-system, BlinkMacSystemFont, "Segoe UI", system-ui`)
- Code/labels: `"Courier New", Courier, monospace`
- Hero size: `clamp(2.75rem, 6vw, 4.5rem)` — big but not obnoxious on mobile

### Layout
- 2-column card grid on ≥ 720px, single column below
- Cards: `minmax(480px, 1fr)` replaced with `repeat(2, 1fr)` for tighter control
- Max content width: 1120px for grid, 760px for hero

### Cards
- Each card gets a per-project CSS custom property `--c` for its accent colour
- Top stripe (3px, always visible) + inner border glow on hover (`::after`)
- Subtle `translateY(-2px)` lift on hover — CSS only, no JS
- `color-mix(in srgb, var(--c) N%, transparent)` for icon bg and tag bg/border
- No scroll-jacking: all animations are CSS `transition` only, triggered by `:hover` not scroll

### Theme toggle
- Header is `position: sticky` with `backdrop-filter: blur(12px)` — no solid white/black bar flash
- Toggle updates icon (moon ↔ sun SVG) and label ("Dark" / "Light")
- Respects `prefers-color-scheme` on load; listens for OS-level changes

### Scroll behaviour
- `html { scroll-behavior: smooth; }` only — no scroll listeners, no intersection observer animations
- Cards do **not** animate in on scroll (avoids the "can't scroll until animation finishes" problem the user explicitly called out)

---

---

## Project detail pages

Each card links to its own detail page. Cards are `<a>` elements; a `→` arrow appears on hover to signal clickability. The footer's GitHub/Live links use `event.stopPropagation()` to open in a new tab without triggering the card navigation.

### URL structure

| Project | URL |
|---|---|
| Scriptoria | `/scriptoria/` |
| MiraCLI | `/miracli/` |
| BrainFudger | `/brainfudger/` |
| AteChips | `/atechips/` |

Note: Scriptoria's live app lives at `/ChurchScribe/` (GitHub Pages default). `/scriptoria/` is a separate info/overview page — these don't conflict.

### Project page layout (per page)

Each project page inherits the same header/footer as `index.html`. Content sections in order:

1. **Back nav** — `← Back` link in the header row (or just below it), styled like a breadcrumb
2. **Hero** — Project name (large), tagline, platform icons, accent colour stripe or tinted background
3. **Overview** — 3–5 paragraphs. More expansive than the card copy. Covers the "why" behind the project, not just "what"
4. **Screenshots / visuals** — Full-width or 2-column image grid. Use `<figure>` + `<figcaption>`. Placeholder until real screenshots are supplied
5. **Key features** — A compact feature grid (2–3 column). Icon + heading + 1-sentence description per feature. Not a bullet-point list
6. **Getting started** — Install steps. For CLI tools (MiraCLI, BrainFudger): code blocks with the install command. For AteChips: link to Releases. For Scriptoria: link directly to the PWA
7. **Links row** — GitHub, live demo (if applicable), any releases page

### Shared project page template

A single `project-page.html` template should be created and then specialised per project. CSS custom property `--c` (the project accent colour) drives theming throughout — hero tint, icon backgrounds, tag colours, link hover states.

### Navigation

- Home → Project page: via card click
- Project page → Home: via `← Back` in the header area (not the sticky nav — keep the nav clean)
- Between project pages: no direct prev/next needed yet, but leave room in the layout

---

## Things to discuss before implementing

1. **About / contact section?** Currently the hero is the only prose. Does Joshua want a short bio, links to socials, or an email?
2. **Page title / domain**: Currently `<title>Joshua Penman</title>` — fine for root. Subpages TBD.
3. **Favicon**: Nothing set yet. Could be a simple `JP` monogram or the wordmark `j.p` in monospace.
4. **Font upgrade**: The system stack looks clean but a self-hosted variable font (e.g., Inter or Geist) would give more control over weight and letter-spacing. Low priority.
5. **Project ordering**: Currently Scriptoria → MiraCLI → BrainFudger → AteChips (reading-order left-to-right top-to-bottom). Open to reordering.
6. **More projects**: The grid naturally expands — just add more `<div class="card">` blocks.
7. **GitHub API integration**: Cards could auto-pull star counts and last-commit dates from the GitHub REST API. Nice-to-have once the static site is live.

---

## Implementation path (when ready)

1. Copy `mockup.html` content into `index.html` at repo root.  
2. Decide on favicon and commit a `favicon.svg` or `favicon.ico`.  
3. Optionally extract CSS to `styles.css` — the single-file approach works fine for a site this size.  
4. No build step needed; this is plain HTML/CSS/JS with zero dependencies.  
5. Push to `main` → GitHub Pages auto-deploys.

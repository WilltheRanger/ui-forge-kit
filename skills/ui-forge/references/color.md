# Color: why builds come out gray, and the fix

## Why it happens

1. **shadcn's defaults are grayscale.** `npx shadcn init` writes a neutral/zinc/slate base where
   `--primary` is near-black (light) or near-white (dark), and `--accent` is just another gray. Every
   component pulls from those variables, so an untouched theme makes the whole UI colorless.
2. **Anti-slop bans push models to retreat.** "No purple gradients, no glows" with no positive color
   instruction makes gray the safest answer. A ban list must always come with a color assignment.
3. **No one assigns color a job**, so it's either everywhere (slop) or nowhere (gray template).

## The fix

### Stage 2: decide color with intent

Write a **color plan** into the design system:

- **Brand hue** from the direction/references (sample favourites; `awwwards:export_design_tokens`).
- **Neutral ramp tinted toward the brand hue** (not pure zinc), e.g. chroma 0.005–0.02 in OKLCH.
- **One accent** for the primary action and the L1 moment; optionally one secondary for data.
- **Data palette** (`--chart-1..5`) designed together with the brand (use the `dataviz` skill's validator).
- **Color budget:** roughly neutral 80–90% · brand 5–15% · accent ≤5%. Name *where* the brand color appears (hero visual, primary button, active nav, chart highlight, section band).
- Build ramps in **OKLCH** (11 steps, 50–950) so light/dark stay perceptually even. Check AA contrast.

### Stage 3: actually wire it into shadcn

Override **every** shadcn variable in `globals.css` for `:root` and `.dark`, not just `--primary`:
`--background --foreground --card --popover --primary --primary-foreground --secondary --muted
--accent --accent-foreground --destructive --border --input --ring --chart-1..5 --sidebar-*`.

- Map: `--primary` = brand/accent, `--ring` = brand, `--accent` = tinted brand-50/900 (not gray),
  `--muted`/`--border` = tinted neutral.
- Starting points: 21st.dev themes (`search` with `type: "theme"`, `color: "<hue>"`, `sort: "popular"`, then `get_theme` for free CSS), shadcn's themes page, tweakcn.
- Component styling goes through tokens only; no raw hex per component.
- Give color at least one **content** home (image, 3D, chart, illustration), not only chrome. Real assets from `assets.md` carry color better than tinted UI.

### Stage 4: verify it

- **Default-theme check:** diff `globals.css` against shadcn's base values. Any untouched variable is a finding.
- **Color presence check:** in screenshots, the brand hue must appear in the L1 element and the primary action on every viewport; a page that reads as pure grayscale is a finding.
- **Budget check:** brand/accent are not on every surface (that's the opposite failure).
- Keep ui-director's grayscale test: hierarchy must survive *without* color, and color must add meaning *with* it.

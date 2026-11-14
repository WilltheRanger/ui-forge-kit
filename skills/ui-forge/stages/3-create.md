# Stage 3 · Create

Load `ui-director` and run its **Steps 0–5** (triage, context, direction, hierarchy map, component
manifest, build). Its rules win: compose don't invent, fit test, spectacle budget, one library per job.
The build happens in two passes so design and motion each get full attention.

What ui-forge adds:

- **Direction is already decided.** ui-director Step 2's Design Read must restate the approved uxui phase 3 winner, not choose anew.
- **Short prompt, strong targets.** Build against the screenshots in `references/` and the approved mockup; aim for the fidelity % in `forge.md`. Match quality and feel, never copy one reference outright.
- **Sourcing order for each manifest row (21st.dev first, by user choice):** 21st.dev MCP (`search` → `get_component` with the result `id`; paid tier, unlimited retrievals. Its `generate` / `iterate_generation` are unavailable (aiGenerationEnabled false): adapt fetched code yourself. Its install commands need `API_KEY_21ST` set in the user's environment; never ask for or print the key) → shadcn/ui (Radix or Base UI) for primitives 21st.dev couldn't cover → `@magicui` / `@react-bits` via shadcn MCP → ui-director's other libraries (Aceternity, Sonner, Vaul, cmdk, NumberFlow, Beautiful UI, RareUI) → hand-built with a stated reason.
- **Tokens** come from the Stage 2 design system. Before installing components, override every shadcn CSS variable in `:root` and `.dark` per `references/color.md` Stage 3. Never ship shadcn's default grayscale theme.
- **Real assets, no placeholders.** Source images, video, 3D, icons and fonts from `references/assets.md`. Add an asset column to `components.md`, and log every file with source, author and license in the project's `assets.md`. 3D goes into the spectacle budget like any showpiece, with a static fallback.
- Optional: push to Figma via `use_figma` / `send_code_to_figma` (first call the Figma MCP's `get_figma_skill` for its usage rules, and `create_session` with the file key).

## 21st.dev deep sweep (every project, before the manifest)

Goal: make 21st.dev the main source for sections and blocks, not an afterthought. Intensity is set at
kickoff in `forge.md` (`21st intensity: deep` by default; `light` = old behaviour).

1. **Per hierarchy-map slot** (every section and block, plus nav, footer, forms, empty states, charts, loaders): run `search` with `type: "component"`, `limit: 30`, and **4–6 query phrasings** (job, layout, mood, domain words, e.g. "pricing 3 tiers toggle", "pricing table dark minimal", "plan comparison"). Also search `type: "template"` for whole-page starters and `type: "theme"` for the brand hue.
2. **Dedupe** by id and keep the strongest 5–8 per slot from the previews and videos.
3. **Fetch source for the top 3 per slot** with `get_component` (retrievals are unlimited) and judge on the real code: dependencies, built-in colors, accessibility, mobile, reduced motion. Never decide from metadata alone when the source is one call away.
4. **Show the board.** Per slot, `search_picker` with the shortlist so the user picks visually. Write everything to `21st-board.md` (slot → candidates → id, preview, verdict).
5. **21st.dev first for everything (user's standing choice).** Blocks, primitives and effects all start from 21st.dev. Fall back to another library only when every 21st.dev candidate fails the fit test or the source check (broken accessibility, no keyboard/focus handling, no mobile, abandoned deps), and record why in `21st-board.md`. Many 21st.dev components are built on shadcn/Radix, which is fine. Showpiece effects still use only the spectacle slots.
6. Adapt every chosen component per "Adapting a fetched component" below.

Target: a typical landing page should end with most of its section-level blocks from 21st.dev (adapted), unless the fit test rejects them; record each rejection's reason.

## Freshness sweep (every run, before the manifest)

ui-director's `component-map.md` is a snapshot; libraries ship new components constantly. Before
picking components:

1. Query what's new: `shadcn` MCP `list_items_in_registries` / `search_items_in_registries` for `@shadcn`, `@magicui`, `@react-bits`; 21st.dev `search` / `get_inspiration` (sort by newest); `awwwards:new_winners` and `search_elements` for fresh patterns. Optionally browse the libraries' changelog/"new" pages in Chrome.
2. Compare against the component log. The installed plugin is a read-only cache, so the editable log is the repo copy: `~/ui-forge-kit/skills/ui-forge/component-watch.md`. If that path doesn't exist (another machine or a cloud session), read the bundled `component-watch.md` beside this skill and write new finds to the project root's `component-watch.md` instead, then tell the user to merge it into the repo.
3. Append new finds there: date, library, component, install name, what job it solves, and whether it beat an older pick. Mark components that broke or were deprecated.
4. Prefer a newer component in the manifest only if it passes ui-director's fit test better than the mapped one; note it in `components.md`.
5. When a find proves itself in a shipped build, propose adding it to ui-director's `component-map.md` (ask the user first).

## Adapting a fetched component (21st.dev or any registry)

Never paste fetched code as-is. Before it enters the project:

1. **Dependencies:** compare the code's actual `import`s against the listed `npmDependencies` / `registryDependencies`; listings are author-written and can miss packages. Install what the imports need.
2. **Colors:** replace hardcoded hex/rgba (palettes, shader colors, shadows, backgrounds) with design-system tokens.
3. **Content:** replace demo copy, links, badges and logos with real product content.
4. **Fit:** cut parts the hierarchy map doesn't need; keep mobile variants and reduced-motion handling.
5. Record the component id, source URL and what was changed in `components.md`.

Save the manifest as `components.md`. 🛑 Show the hierarchy map + manifest before building (ui-director Step 4).

## 3a · Static build (no motion)

Build layout, type, color, spacing and every state with **zero animation**; showpiece components
render in their resting frame. Then run one Stage 4 round on the static page.

🛑 The user approves the static design (balance, hierarchy, spacing) before any motion is added.

## 3b · Motion pass

1. Record motion on the favourites: `awwwards:record_site_motion` (video), plus `get_motion_dna` and `analyze_scroll_map` / `analyze_hover_census`.
2. Go through each recording frame by frame and write `motion-spec.md`: per moment → trigger, element, property, from → to, duration, easing, delay/stagger.
3. Load `anthropic-skills:animate`; implement from the spec. Blend ideas across references; never copy one sequence exactly. Respect reduced-motion and the spectacle budget.
4. Hand off to Stage 4 for the motion lens.

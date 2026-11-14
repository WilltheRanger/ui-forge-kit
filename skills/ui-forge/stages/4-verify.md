# Stage 4 · Verify

Run `ui-director` **Step 6** (critique loop) using its `references/critique-rubric.md`: 7 lenses
scored 1–5, batched fixes via impeccable refine commands, its round limit. ui-forge adds a
fidelity score, a second judge on a different model, and side-by-side evidence.

## Each round

1. **Side-by-side.** Screenshots of the build at 375 / 768 / 1440 (light + dark), placed next to the matching `references/` shots. Save to `rounds/round-<n>/`. Screenshot tool, first that works: Playwright MCP (`browser_resize` + `browser_take_screenshot`) → the built-in browser pane (`mcp__Claude_Browser__resize_window` with `colorScheme`, then `computer` screenshot) → `awwwards:capture_live_site` for a deployed URL. If Playwright errors with "Chromium distribution 'chrome' is not found", tell the user once that `npx playwright install chrome` fixes it, then use the next tool.
2. **Fidelity %.** Estimate how close the build is to the approved mockup + references, per section and overall. Be harsh: builders over-score themselves.
3. **Two independent judges**, each in its own context, given only the screenshots, side-by-sides, hierarchy map, manifest and rubric (never the builder's opinion):
   - Judge A: `impeccable:impeccable-finish-reviewer`.
   - Judge B: a fresh `general-purpose` agent on a **different model** (Agent `model` override, e.g. `sonnet` or `fable`) scoring the rubric lenses plus an overall /10.
4. **Extra lenses** feed the same fix batch:

| Lens | Tool / skill |
|---|---|
| Taste / anti-slop | `design-taste-frontend` pre-flight check; `unslop` audit (`references/signs.md`) |
| Color | `references/color.md` Stage 4: no untouched shadcn variables, brand hue present on L1 + primary action, color budget respected |
| Copy | `anthropic-skills:stop-slop` on all UI text |
| Accessibility evidence | `awwwards:analyze_accessibility` |
| Reference fidelity | `awwwards:verify_build` against the favourites |
| Motion vs references | `motion-spec.md` + `awwwards:get_motion_dna` on build and favourites |
| Performance | `awwwards:audit_url`, `analyze_bundle`, `awwwards:analyze_images` (sizes, formats, 3D model weight) |
| Asset licensing | Every image/model/font in `assets.md` with a license that allows this use; no placeholders left |

5. **Fix everything in one batch**, ordered by `unslop`'s pass sequence (spacing → color → icons → copy → type → layout → details → visuals → motion) so later fixes don't undo earlier ones. Load the `unslop` skill for its rules and tokens. Skip its image-generation step (no Higgsfield; source visuals from `references/assets.md`). During the 3a static round, stop before the motion pass. Then next round.

## User calibration

Show the user each round's fidelity % and judge scores. If they say the real number is different
("that's 60, not 90"), **their number replaces yours** and is recorded in `review.md`. Use the
gap to re-anchor how harshly you score the next round.

## Stopping

Stop when the rubric pass bar is met **and** fidelity ≥ the `forge.md` target **and** both judges
≥ the `forge.md` score, or when the round limit / time budget runs out. Log every round to
`review.md` in the rubric's report format, plus fidelity % and both judge scores.

🛑 Show `review.md` and the latest side-by-sides; the user signs off. Then run ui-director Step 7
hand-off and `impeccable-documenter` for DESIGN.md.

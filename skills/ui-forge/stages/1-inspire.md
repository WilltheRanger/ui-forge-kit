# Stage 1 · Inspire

Goal: 9–12 real references, each with a reason. Evidence, not vibes. References carry layout,
spacing and type better than words, so keep later prompts short and point at screenshots.

Save every reference screenshot (full page + key sections, desktop and mobile) to `references/`.
These files are the build targets in Stage 3 and the comparison baseline in Stage 4.

## Gather (go wide)

Search by the job the screen must do ("pricing 3 tiers yearly toggle"), not a vibe ("cool pricing").

| Source | How | Use for |
|---|---|---|
| Awwwards MCP | `search_sites`, `new_winners`, `get_collections`, `search_elements`, `get_site_details` | Award-level sites and their design DNA |
| 21st.dev MCP (paid, unlimited) | `search` (type component/theme/template), `search_picker` to let the user pick visually, `get_inspiration`, `list_bookmarks` | Buildable component patterns. Each result has `previewUrl` + `videoUrl`: save previews to `references/` and use the videos as motion references in 3b |
| `shadcn` MCP → `@magicui`, `@react-bits` registries | browse/search registry items | Animated showpieces, text effects, backgrounds |
| Figma MCP | `search_design_system`, `get_libraries` (`create_session` first) | The user's existing files and system |
| User's Chrome (claude-in-chrome; read `anthropic-skills:chrome-browser` first) | new tab only | Visual judgment on 21st.dev, magicui.design, reactbits.dev, ui.aceternity.com, ui.shadcn.com Blocks, plus signed-in galleries (Mobbin, Godly, Dribbble…) |

Projects need these in `components.json` before shadcn can reach the registries:
`"registries": { "@magicui": "https://magicui.design/r/{name}.json", "@react-bits": "https://reactbits.dev/r/{name}.json" }`

## Asset scouting

While collecting references, note what kind of imagery/3D each favourite relies on, and shortlist
candidate real assets from `references/assets.md` (e.g. NASA 3D models, Unsplash photos, Poly Haven HDRIs).
Add an "Asset shortlist" section to `inspo.md`.

## Dissect (narrow)

For the top 2–3: `awwwards:analyze_page_structure`, `analyze_scroll_map`, `analyze_hover_census`, `get_motion_dna`.

## Output `inspo.md`

Per reference: URL/slug · screenshot · what to borrow (layout, type, motion, color) · what to avoid.

🛑 The user picks 3–5 favourites. Rejected ones stay listed and marked.

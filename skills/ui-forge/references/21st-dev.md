# 21st.dev: everything it offers, and where ui-forge uses it

The account is paid (unlimited search and retrieval) but has no hosted AI generation, so never
call `generate` / `iterate_generation`; fetch and adapt instead. Install commands need
`API_KEY_21ST` in the user's environment; never ask for or print the key.

| What | Tools | Stage | Use |
|---|---|---|---|
| **Components** | `search` (type `component`), `search_picker`, `get_component` | 1, 3 | Every block and primitive, first choice (deep sweep in `stages/3-create.md`) |
| **Templates** (whole pages/sites) | `search` (type `template`, `free`, `sort`, `tag`) | 1, 2 | Whole-page layout references and starting structures; open their `url` (no code to fetch) |
| **Themes** (full shadcn CSS variable sets) | `search` (type `theme`, `color`, `sort: popular`), `get_theme` (free) | 2, 3 | Starting point for the color plan in `references/color.md`; adapt, never ship unedited |
| **Inspiration** | `get_inspiration`, `record_inspiration_feedback` | 1 | Curated direction-level references; record which ones the user liked or rejected |
| **Logos** | `search_logo` | 3 | Brand marks for "built with", partner and data-source rows (trademarks still apply) |
| **Video blocks** (Remotion) | `search` with `runtime: "remotion"` (`kind`, `aspect`), `get_component`, `video_*` tools | 3b, hand-off | Product demo / promo videos (e.g. the 30s hackathon demo), animated scenes and transitions; the component's preview `videoUrl` also serves as a motion reference |
| **Bookmarks and lists** | `bookmark`, `create_bookmark_list`, `add_to_list`, `list_bookmarks`, `get_bookmark_list` | 1, 3 | Save each project's shortlist as a list named after the project, so it survives sessions and machines |
| **Team libraries** | `list_teams`, `list_team_libraries`, `list_team_components`, `list_team_lists` | 3 | Reuse components the user or team already made; check before searching publicly |
| **Publishing** | `submit_component`, `edit_component`, `withdraw_component` | after Stage 4 | Only on the user's explicit request: publish a finished custom component |

Not "only components": a good run touches templates (structure), themes (color), inspiration
(direction), logos (credibility rows), video blocks (demo), and lists (memory), not just blocks.
Other libraries (shadcn, Magic UI, React Bits, ui-director's map) remain the fallback per
`stages/3-create.md` and are still used when no 21st.dev item passes the fit test or code check.

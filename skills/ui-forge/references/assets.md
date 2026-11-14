# Asset sources

Real assets beat placeholders and AI-generic imagery. Pick by license first, then quality.
Every asset used goes in `assets.md` in the project root: file → source URL → author → license.
Never hotlink from a gallery page; download into `public/` (or use the source's official CDN/API).
Never use Blender, Godot or Higgsfield to get assets.

## Photos & video

| Source | License | Best for |
|---|---|---|
| **Unsplash** (unsplash.com, API) | Unsplash License: free commercial, no attribution required (credit anyway) | Editorial, lifestyle, nature, architecture |
| **Pexels** (photos + video) | Pexels License: free, no attribution | Stock video loops for heroes |
| **NASA Image & Video Library** (images.nasa.gov) | Generally public domain (check each item; no NASA logos/insignia, no implied endorsement) | Space, Earth, missions: first choice for space projects |
| **NASA Earth Observatory / NASA Scientific Visualization Studio** (svs.gsfc.nasa.gov) | Generally public domain, credit NASA | Data visualizations, Earth imagery, animations |
| **ESA / ESA-Hubble / ESA-Webb** | CC BY 4.0 (credit required) | Deep space, telescope imagery |
| **Lummi** (lummi.ai; REST API needs an approved key, no MCP) | Lummi License: free commercial, no attribution required (credit anyway); no reselling or claiming ownership. Pro tier exists | AI-generated stock with transparent/cut-out subjects. Don't use where viewers expect real photos (e.g. science/NASA claims) |
| Pixabay | Pixabay License | Fallback |

## 3D models, HDRIs, textures

| Source | License | Best for |
|---|---|---|
| **Poly Haven** (polyhaven.com) | CC0 | HDRI lighting, PBR textures, realistic models |
| **NASA 3D Resources** (nasa3d.arc.nasa.gov, github.com/nasa/NASA-3D-Resources) | Public domain | Spacecraft, satellites, planets, asteroids (glTF/STL) |
| **Sketchfab** (filter: downloadable + CC0/CC BY) | Per model; check it | Wide variety, high quality |
| **Poly Pizza** (poly.pizza) | CC0 / CC BY per model | Low-poly stylized |
| **Kenney** (kenney.nl) / **Quaternius** | CC0 | Stylized game-like kits |
| **Spline community** (spline.design) | Per file, remixable | Ready-made interactive web 3D scenes |

**Rendering on the web:** `@react-three/fiber` + `@react-three/drei` (`useGLTF`, `Environment` with a Poly Haven HDRI) for custom scenes; `@google/model-viewer` for a simple rotatable model; Spline's React export for designed scenes. Compress models with `gltf-transform` (Draco/Meshopt), keep hero models under ~2 MB, lazy-load below the fold, and provide a static poster image + reduced-motion fallback.

## Illustrations, icons, motion graphics

| Source | License | Best for |
|---|---|---|
| **Lucide** (shadcn default) | ISC | UI icons: use first for consistency |
| Phosphor / Tabler / **Iconify** (aggregator) | MIT etc. | Extra icon weights and sets |
| **Simple Icons** / 21st.dev `search_logo` | CC0 (trademarks still apply) | Brand logos |
| **LottieFiles** (free tier) | Lottie Simple License | Lightweight vector animations |
| unDraw / Open Peeps / Humaaans | Free / CC0 | Illustrations (use sparingly; easily read as generic) |

## Fonts & texture

- **Google Fonts** and **Fontshare** (free commercial). Self-host via `next/font`.
- Grain/noise: generate with SVG `feTurbulence` rather than downloading images.

## Rules

- Pick assets that serve the hierarchy map: the L1 element gets the best asset; avoid decorative filler.
- One visual source family per page (don't mix photoreal 3D, flat illustration and stock photos without a reason).
- Optimize: `next/image`, AVIF/WebP, correct `sizes`, explicit width/height to avoid layout shift, meaningful `alt`.

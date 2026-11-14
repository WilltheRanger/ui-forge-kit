---
name: ui-forge
description: End-to-end UI design framework in four gated stages — Inspire (Awwwards, 21st.dev, Magic UI, React Bits, Figma, browser galleries), Direct (uxui-workflow requirements → UX → rule-of-three UI), Create (ui-director composing shadcn/21st.dev/Magic UI/React Bits and its other libraries), Verify (ui-director critique loop plus impeccable, design-taste, animate, stop-slop and Awwwards audits). Use when the user wants "the best UI", asks to design/build/redesign a site, page, app or component from scratch with full research and review, or invokes /ui-forge. Also resumes when inspo.md, design-brief.md, components.md or review.md exist. Excludes Blender, Godot and Higgsfield.
argument-hint: "[stage] [brief or target]"
---

# UI Forge: inspire → direct → create → verify

An orchestrator. It owns Stage 1 and the extra Verify lenses; everything else is delegated to
`uxui-workflow` and `ui-director` so their rules stay the single source of truth.

| Stage | Instructions | Delegates to | Output |
|---|---|---|---|
| 1. Inspire | `stages/1-inspire.md` | — (own stage) | `inspo.md` |
| 2. Direct | `stages/2-direct.md` | `uxui-workflow` phases 1–3 | `requirements.md`, `design-brief.md`, canvas, design system |
| 3. Create | `stages/3-create.md` | `ui-director` Steps 1–5 | code, `components.md` |
| 4. Verify | `stages/4-verify.md` | `ui-director` Step 6 + extra lenses | `review.md`, DESIGN.md |

## Ground rules

- **The user makes every decision.** Recommend with reasons; never pick for them.
- **Stop at every 🛑 and wait.** Never answer your own checkpoint.
- **Stay in the current stage; read one stage file at a time.** Load delegated skills only when their stage arrives.
- **Precedence on conflict:** user's explicit choices → project files (PRODUCT.md, DESIGN.md, repo tokens) → `ui-director` → `uxui-workflow` → impeccable → taste skills.
- **Never call** Blender, Godot or Higgsfield MCPs.

## Kickoff: ask once, then run (before Stage 1)

Ask every question up front in one batch, then start: target fidelity % (default 95), judge pass score (default 9/10),
time budget and usage limit for the autonomous loop, and 21st.dev intensity (`deep` default, or `light`). Record them in `forge.md`.
🛑 gates stay in Stages 1–2 and before 3b (taste decisions are the user's). The Stage 3→4 build/judge
loop runs on its own, pacing work evenly across the budget, and stops at the bar or the budget.

## Feedback protocol (any stage)

- Ask for specific changes: which element, which property, which way. Marked-up screenshots welcome.
- If the user can't name what's off, **describe it back**: the section's layout, type sizes/fonts, colors (tokens), spacing, motion, so they can point at the exact part.

## Where to start

Files live in the project root. If the user named a stage (`/ui-forge verify`), go there after checking its input exists. Otherwise resume from the furthest file found:

- `review.md` → Stage 4 · `components.md` → Stage 4 · `ui-progress.md` or `design-brief.md` → Stage 3 (or finish uxui phase 3 first if `ui-progress.md` shows it open) · `inspo.md` → Stage 2 · none → Stage 1

When resuming, say in one line what you found and where you'll pick up, and wait for a yes.

## Show where you are

Open every stage with a header, and a new one when switching from going wide to narrowing:

> **Stage 1 · Inspire** · Gather (go wide)

## Between stages

1. Save the output in the project root.
2. Recap in 3–5 bullets what the user decided.
3. 🛑 Ask: start the next stage now, or stop here? (They can resume later with `/ui-forge`.)
4. Only on a yes, read the next stage file.

# Critique rubric

The critique loop exists to catch what the builder can't see in their own work. Two rules make it useful:

1. **Separate the judge from the builder.** The independent reviewer gets the screenshots, the
   hierarchy map, the manifest and this rubric. It does *not* get your opinion of the result.
2. **Bounded, batched rounds.** Screenshot desktop and mobile together, collect every finding, fix
   them all in one batch, then re-check. Open-ended "tweak, look, tweak" loops waste the user's
   money and drift away from the brief (impeccable makes the same point).

## Lenses

Score each lens 1–5 (1 = broken, 3 = acceptable but generic, 5 = a professional designer would ship it).

| # | Lens | Who checks it | What a 5 looks like |
|---|---|---|---|
| 1 | **Hierarchy** | You + reviewer, using hierarchy.md checks | Squint, grayscale and 5-second tests all pass. One L1. Clear reading path. |
| 2 | **Component fit** | You + reviewer | Every manifest row passes the fit test. Spectacle budget respected. No hand-rolled primitives without a stated reason. |
| 3 | **Slop scan** | impeccable detector + the "Patterns that read as AI-generated" list | None of the listed patterns present. Copy is specific to the product. |
| 4 | **Craft** | impeccable `critique` | One spacing scale, a tight type scale, consistent radii and alignment. Every state is designed. |
| 5 | **UX** | impeccable `critique` heuristics | The task flow is obvious. Errors are recoverable. Labels are clear. |
| 6 | **Technical** | impeccable `audit` | WCAG AA contrast, keyboard path, focus-visible, responsive at 375/768/1280+, no layout shift. |
| 7 | **Motion** | `animate` golden rules (Emil's `review-animations` if installed) | Purposeful, 150–300ms, exits faster than entries, reduced-motion respected, transform/opacity only. |

## Reviewer prompt template

Spawn `impeccable:impeccable-finish-reviewer` (or a fresh general-purpose agent) with:

```
You are reviewing a UI build for a professional design bar. Be specific and severe; generic praise is useless.
Inputs: <screenshot paths: desktop + mobile>, <hierarchy map>, <component manifest>,
<path to this rubric>, <path to hierarchy.md>.
For each lens 1–7: give a score 1–5, the evidence (what you see, where), and the fix.
Then list the top 5 fixes in priority order, each mapped to one impeccable command
(layout, typeset, quieter, distill, bolder, clarify, harden, adapt, polish, animate).
```

## Pass bar

<!-- TODO(human): define when the critique loop stops. -->

## Report format

```
Round <n>: Hierarchy 4 · Fit 5 · Slop 4 · Craft 3 · UX 4 · Technical 5 · Motion 4
Fixed this round: …
Still open: …   (stop reason: passed | round limit)
```

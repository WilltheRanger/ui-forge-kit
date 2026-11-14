# Visual hierarchy and component fit

Hierarchy is the difference between a page that *reads* and a page that is just *full*. Plan it
first; components are how you express it, not where it comes from.

## Levels

| Level | What it is | How many | Typical weight |
|---|---|---|---|
| **L1** | The one thing the user must see or do: headline, primary action, key metric, the artifact itself | Exactly 1 per screen/viewport | Largest size, highest contrast, the accent color, the most space around it. May carry the spectacle slot. |
| **L2** | Supporting what L1 says or does: subhead, secondary actions, key supporting content | 2–4 | Clearly smaller and quieter than L1. Neutral or muted color. |
| **L3** | Detail: body copy, list items, table cells, form fields | Many | Body size, normal weight. |
| **L4** | Chrome and meta: nav, footer, timestamps, labels, helper text | Many | Smallest, lowest contrast, but still meets WCAG AA. |

**Mode changes L1:**
- Persuade: L1 = the promise (headline) + one CTA.
- Operate: L1 = the user's current task (the table, editor or form), not a hero. Chrome stays quiet.
- Read: L1 = the content column. Typography does almost all the work.
- Experience: L1 = the work itself. The interface steps back.

## Weight levers: use the cheapest one that works

1. **Position**: top-left (LTR) and centre of the first viewport win.
2. **Size**: a type scale with clear jumps (e.g. ratio 1.25–1.333).
3. **Whitespace**: space around an element is emphasis.
4. **Contrast / weight**: font weight and luminance contrast.
5. **Color**: accent reserved for L1 and interactive state. If everything is accented, nothing is.
6. **Motion**: the most expensive lever. Ambient motion is for L1 only, and only in the spectacle slot.

If you reach for motion or effects to make something stand out, first ask whether position, size
or space would do it. Usually they do, and the result looks more professional.

## Spectacle budget

A "showpiece" is any component whose main job is to impress: animated backgrounds, beams,
spotlights, aurora, 3D tilt cards, globes, marquees, shimmer or glow borders, parallax, text morphs.

| Mode | Showpiece slots |
|---|---|
| Persuade | 1 per viewport, and at most ~3 on the whole page, never in adjacent sections |
| Experience | 1 per viewport, and it must serve the work being shown |
| Read | 0 (one subtle hero accent at most) |
| Operate | 0. Use micro-interactions only: press scale, focus rings, list-insert, NumberFlow. |

Assign slots in the hierarchy map *before* browsing Magic UI, Aceternity or 21st.dev. Browsing first
is how you end up with six effects.

## The fit test: ask it of every component in the manifest

1. **Job.** What user task or message does it serve on *this* screen? ("It looks premium" is not a job.)
2. **Level.** What level is it on, and does its visual weight match that level? An L3 item with L1 weight competes with L1.
3. **Mode.** Does it suit the surface mode? (A spotlight background on a settings page fails.)
4. **Competition.** Does it pull the eye away from L1 when you squint?
5. **Removal.** If you deleted it, would anything get worse for the user? If not, delete it.

Any "no" → cut it, downgrade it to a quieter component, or move it to where it does fit.

## Checks to run on screenshots

- **Squint / blur test:** blur the screenshot (or squint). The L1 should still be the first thing
  you notice, and the reading path should still be visible.
- **Grayscale test:** hierarchy must survive without color.
- **5-second test:** after 5 seconds, can someone say what this is and what to do next?
- **Count test:** one primary button per view, ≤ ~5 font sizes in use, one accent color, one radius family.

## Patterns that read as AI-generated

- Centered hero over a dark gradient mesh, purple-to-blue gradient text, "✨" badge above the headline.
- Three equal feature cards with icon + title + 2 lines, repeated in several sections.
- Bento grid used for content that isn't uneven in importance.
- Glow or gradient borders on every card. Glassmorphism on everything.
- Logo marquee with made-up logos. Testimonials with no real people behind them.
- Several CTAs of equal weight ("Get started", "Book demo", "Learn more" all as filled buttons).
- Every section has a different background effect.
- Icons on every bullet. Emojis as icons.
- Stat blocks with round invented numbers ("10x faster", "99% uptime").
- Generic copy: "Unlock", "Seamless", "Revolutionize", "Supercharge", "Elevate".

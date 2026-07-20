# Research

Competitive teardowns and prior-art notes. Screenshots live in [`screens/`](./screens/) and are referenced from here.

**Status:** desk research done, hands-on teardowns outstanding.

## Contents

- [**Competitive landscape**](./competitive-landscape.md) — 15 products across hard / soft / aspirational tiers, with the findings that were folded into the brief on 20 July 2026 and the six still open. Desk research only; the parser bake-off and hands-on teardowns are still to do.

## What's worth looking at

The brief has four areas where other products have already made the mistakes, and where seeing how they handled it is cheaper than deriving it:

- **Portion scaling** — who reflows quantities live, who hides it behind a "recalculate" button, and what they do with `3 eggs × 1.5`
- **Grocery merge** — how duplicate ingredients across recipes are combined and presented, and whether the merge is auditable back to its sources
- **Recipe capture** — paste and URL import flows, and specifically how much correction work the review step demands of the user
- **Pantry** — the graveyard feature. Worth finding out how existing implementations die, since §5.8 is betting on a two-tier split to avoid it.

## Format

One section per product. For each: what it does well, where it breaks down, and the specific implication for Cooksy — a finding without an implication isn't finished.

Link screenshots as `![caption](./screens/filename.png)` so claims stay checkable.

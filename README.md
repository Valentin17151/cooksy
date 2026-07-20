# Cooksy

> A digital recipe book that turns what you want to cook into exactly what you need to buy.

**Status:** design phase. The brief is settled and scope is combined (no v1/v2 staging). Nothing is built yet, and no tech stack has been chosen — that decision is deliberately deferred.

## The loop

Save a recipe → set the portions → plan a few meals → get one merged grocery list.

Every quantity rescales live when you change the serving count. Ingredients shared across meals combine into a single line, grouped by store aisle, minus whatever is already in your cupboard.

## Who it's for

Cooking lovers who are also optimisers — people who enjoy cooking but resent the overhead around it. They already know what they want to cook; they want the logistics to disappear.

---

## Repo map

This table is the index — update the status column as work lands.

| Path | What lives here | Status |
|---|---|---|
| [`CLAUDE.md`](./CLAUDE.md) | The product brief — source of truth for scope, features and locked decisions | ✅ Written |
| [`research/`](./research/) | Competitive teardowns and prior-art notes | ⬜ Empty |
| [`research/research.md`](./research/research.md) | Written findings, and what they imply for Cooksy | 🟡 Stub |
| [`research/screens/`](./research/screens/) | Screenshots from other products, referenced by `research.md` | ⬜ Empty |
| [`wireframes/`](./wireframes/) | Low-fidelity layouts for the seven screens | ⬜ Empty |
| [`concept/`](./concept/) | Visual direction — moodboards, type and colour, a rendered screen or two | ⬜ Empty |
| [`tokens/`](./tokens/) | Design tokens: colour, type scale, spacing, radii, elevation | ⬜ Empty |
| [`components/`](./components/) | Component specs — states, sizes, behaviour | ⬜ Empty |
| [`design-system/`](./design-system/) | The assembled system: how tokens and components fit together, usage rules | ⬜ Empty |
| [`handoff/`](./handoff/) | Developer-facing output — redlines, specs, asset exports | ⬜ Empty |

The folders exist but are placeholders — each holds a `.gitkeep` and nothing else, so git tracks the structure before there's work in it. Delete a row if a folder turns out not to be needed.

## Screens

Three primary tabs, because three things get used daily — **Library**, **Week plan**, **Grocery list**. Reached contextually rather than from the tab bar: **Recipe**, **Add recipe**, **Pantry**, **Settings**. Pantry stays out of the tab bar deliberately: it's configured once and touched rarely.

## Scope

- **Metric only** — the ingredient list uses grams, millilitres and pieces. No spoons, no cups. Non-metric input is converted at import.
- **Capture by paste or URL** — both land on the same editable review screen, where you correct every amount before it saves
- **Live portion scaling** — a servings stepper that reflows the whole ingredient list
- **Aggregated grocery list** — merged across meals, aisle-grouped, checkable, auditable
- **Pantry** — zero-maintenance staples plus opt-in tracked quantities, subtracted from the list *visibly*, never silently
- **Weekly meal planner** — seven days, per-slot portion sizes and member assignment, per-day and weekly-average calories
- **Estimated calories** — kcal per 100 g for the dish itself, plus kcal per portion at whatever portion size you choose
- **Household sharing** — shared library, shared plan, live shared grocery list. Invisible if you cook alone.
- **Sharing outward** — export the list as text, share a recipe as a read-only link

Cloud accounts from day one. Mobile-first, desktop adapted later.

## Design principles

The servings stepper is the hero. Merged numbers are always auditable. Honest estimates over confident guesses. Kitchen and shop are hostile environments. The user's recipe is sacred. Solo use must not pay for shared use.

## Not a diet tracker

Cooksy reports what a dish is. No macros, no goals, no logging what you actually ate, no streaks.

## Deliberately not built

Recipe discovery, social features, price lookup and online ordering, photo/OCR import, package-size reconciliation, monetisation. These would make Cooksy a different product.

## Build order

Scope doesn't phase, but the work has a required sequence:

1. Canonical ingredients + the weight model — four features join on it
2. Recipe capture → review → save, paste path first
3. Portion scaling and calories
4. Grocery list — merge and aisle grouping → **cook a real week off it before going further**
5. Weekly planner
6. URL import
7. Pantry
8. Household sharing

Steps 1–4 are the product. If attention runs out, it should run out at the bottom of this list, not the middle.

## Open question

**Where the canonical ingredient data comes from** — ingredients need kcal/100 g, density, average unit weight and aisle category, and no existing dataset carries all four. Candidates are in §10 of the brief. The fallback is fixed regardless: an unmatched ingredient never blocks saving a recipe.

## Full brief

See [CLAUDE.md](./CLAUDE.md) — feature specs, the weight model, screens, design principles, the open question, and the build order in full.

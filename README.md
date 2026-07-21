# Cooksy

> A digital recipe book that turns what you want to cook into exactly what you need to buy.

**Status:** design phase. The brief is settled, and **the stack is decided: Cooksy is a PWA** — one installable web app across mobile and desktop. Nothing is built yet. Eleven open questions were closed on 21 July 2026; one remains, and it doesn't block design work.

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
| [`research/`](./research/) | Competitive teardowns and prior-art notes | 🟡 In progress |
| [`research/research.md`](./research/research.md) | Index of the research, and what's still outstanding | ✅ Written |
| [`research/competitive-landscape.md`](./research/competitive-landscape.md) | 15 products across three tiers; the user pain underneath them; what was folded into the brief, and how each open finding was decided | ✅ Written |
| [`research/comparison.md`](./research/comparison.md) | The 15 compared on audience · product base · key mechanism · trust · monetization | ✅ Written |
| [`research/benchmark-retrieval.md`](./research/benchmark-retrieval.md) | Retrieval scored — 8 criteria × 5 best-in-niche products, what to transfer, what to refuse | ✅ Written |
| [`research/ux-patterns.md`](./research/ux-patterns.md) | Five organising principles for storing and retrieving a recipe; which one the brief already chose, and its one failure mode | ✅ Written |
| [`research/summary.md`](./research/summary.md) | Synthesis of the three documents above, with eight gaps each carrying a falsifiable hypothesis | ✅ Written |
| [`research.html`](./research.html) | The same synthesis as one browsable page — comparison tables, screens, cross-linked gaps | ✅ Written |
| [`research/screens/`](./research/screens/) | Screenshots from other products, referenced by `comparison.md` | ✅ 20 captured |
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
- **Capture by paste or URL** — both land on the same editable review screen, where you correct every amount before it saves. Review is mandatory; nothing saves silently.
- **Live portion scaling** — a servings stepper that reflows the whole ingredient list
- **Aggregated grocery list** — merged across meals, aisle-grouped, checkable, auditable
- **Offline-first** — the recipe and the list work with the radio off. Writes queue and merge; the shop has no signal.
- **Search by ingredient** — what can I make with the aubergine, not just what did I call that recipe
- **Sub-recipe links** — a recipe can link to another. Links only: no nested scaling, no merged ingredients.
- **Pantry** — zero-maintenance staples plus opt-in tracked quantities, subtracted from the list *visibly*, never silently
- **Weekly meal planner** — seven days, per-slot portion sizes and member assignment, per-day and weekly-average calories
- **Estimated calories** — kcal per 100 g for the dish itself, plus kcal per portion at whatever portion size you choose
- **Household sharing** — shared library, shared plan, live shared grocery list. Invisible if you cook alone.
- **Sharing outward** — export the list as text, share a recipe as a read-only link

Cloud accounts from day one, but local-first: the network is a background synchroniser, never something you wait on. Mobile-first, desktop adapted later. Zero budget — free-tier hosting, no monetisation.

**Deferred to post-MVP:** OS share-sheet capture (Android only — iOS Safari has no Web Share Target support) and full library export.

## Design principles

The servings stepper is the hero. Merged numbers are always auditable. Honest estimates over confident guesses. Kitchen and shop are hostile environments. The user's recipe is sacred. Solo use must not pay for shared use.

## Not a diet tracker

Cooksy reports what a dish is. No macros, no goals, no logging what you actually ate, no streaks.

## Deliberately not built

Recipe discovery, social features, price lookup and online ordering, photo/OCR import, package-size reconciliation, cooking mode of any kind, user-editable aisle order, video recipe import, monetisation. These would make Cooksy a different product.

## Build order

The work has a required sequence:

0. **Local-first storage and the sync model** — not a feature and not a screen, which is why it comes first. Every write in the product is built on its shape.
1. Canonical ingredients + the weight model — four features join on it
2. Recipe capture → review → save, paste path first
3. Portion scaling and calories
4. Grocery list — merge and aisle grouping → **cook a real week off it before going further**
5. Weekly planner
6. URL import
7. Pantry
8. Household sharing

Steps 1–4 are the product. If attention runs out, it should run out at the bottom of this list, not the middle. Search and sub-recipe links have no step of their own — see §11 of the brief.

## Open question

**Where the canonical ingredient data comes from** — ingredients need kcal/100 g, density, average unit weight and aisle category, and no existing dataset carries all four. Candidates are in §10 of the brief. It must be settled before build step 1 and not before, so it doesn't block the current design phase. The fallback is fixed regardless: an unmatched ingredient never blocks saving a recipe.

The other eleven — aisle order, library export, cook mode, video, search, sub-recipes, mandatory review, budget, permissions, metric-only and the stack — were closed on 21 July 2026. The register is §10.1 of the brief.

## Full brief

See [CLAUDE.md](./CLAUDE.md) — feature specs, the weight model, screens, design principles, the open question, and the build order in full.

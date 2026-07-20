# Competitive landscape

**Date:** 20 July 2026
**Scope:** 15 products across three tiers, assessed against the brief (§1–§11)
**Method:** desk research — vendor documentation, app store listings, and 2026 comparison reviews. No hands-on teardown yet; see *Gaps in this research* at the foot.

Published version of this document: [claude.ai/code/artifact/ea530c9b-c730-432b-aa58-5d76691e5751](https://claude.ai/code/artifact/ea530c9b-c730-432b-aa58-5d76691e5751)

---

## The three tiers

**Hard** — same product, same audience. Recipe library, portion scaling and a merged grocery list, sold to people who already know what they want to cook.

**Soft** — different product, same underlying job. Where this audience's recipes actually live today. The real switching cost is measured against these, not against Paprika.

**Aspirational** — the craft bar. Products that set the standard for reading a recipe and running a list.

Within each tier, entries run from closest to furthest.

---

## Tier 1 — Hard

### Paprika Recipe Manager 3

*Hindsight Labs · iOS / Android / Mac / Windows · one-time purchase per platform*

The category default. Clip → scale → aisle-sorted merged list → pantry. Feature for feature, the closest thing that exists to Cooksy, minus the household.

**Does well.** The pantry — quantity, purchase date, expiry, in/out-of-stock — is the proven shape of §5.8, and it has survived years of real use. Ingredient merge and aisle sort work. One-time purchase with no subscription is why users tolerate an ageing interface.

**Breaks down.** No household sharing at all: recipes, plans and lists are personal, synced across your own devices only. An item can only exist in one grocery list at a time. Aisle organisation is limited.

**Implication.** Its two loudest weaknesses are Cooksy's two wedges — household sharing (§5.10) and list lifecycle (§5.9). The single-list limitation is a known complaint and must not be inherited by accident; §5.9's "generating never destroys" rule exists because of it.

### Fond

*fond.kitchen · cross-platform · subscription*

The 2026 challenger, positioned explicitly against Paprika on exactly Cooksy's combined scope: shared library, shared plan, shared list.

**Does well.** Workspaces for up to ten members. Actively markets against the incumbent's gaps, which makes their comparison pages a free map of the category's pain points.

**Breaks down.** Unknown — needs hands-on. Their roles model (owner / editor / viewer) is the open question.

**Implication.** Cooksy has deliberately rejected roles (§5.10) on the grounds that households run on offline trust. Fond is the live experiment. Worth watching whether their users exercise roles or ignore them; that answer either validates the flat model or kills it.

### Samsung Food (formerly Whisk)

*Samsung · iOS / Android / Web · free tier + Food+ at $59.99/yr*

Import from any URL, weekly plan, one-click shopping list, shared with a shopping partner. The same loop, at global scale, with Samsung behind it.

**Does well.** The URL importer is the category benchmark. Recipe scale (240k recipes, 124k guided), nutrition coverage across ~2.3m ingredients.

**Breaks down.** It is a content platform first — AI meal plans, Health Scores, dietary feeds. Precisely what §2 and §8 reject.

**Implication.** Test the §5.2 parser against the same pages Samsung Food handles cleanly; that is the quality bar. Their bloat is Cooksy's positioning — the brief's refusal to become a discovery product is the differentiator, not a limitation.

### Plan to Eat

*iOS / Android / Web · subscription*

Planner-first, generating a categorised list straight from the week. Long-lived, loyal, non-social — an optimiser's tool.

**Does well.** User-reorderable list categories and per-store lists. A Staples list for things bought regularly but not tied to a recipe, plus a separate pantry that suppresses items from future lists.

**Breaks down.** Unknown — needs hands-on.

**Implication.** Their Staples list validates §5.8's zero-maintenance tier as a real, used pattern. **Their reorderable categories expose a gap:** §5.9 promises "a sensible walking order through a store", but that order is store-specific and an optimiser will want to rearrange it. Currently unaddressed in the brief.

### Tandoor Recipes

*Open source · self-hosted · free*

The nerd-optimiser's choice: a real food database, editable unit conversions, Open Food Facts nutrition attached to ingredients, totals at recipe and meal-plan level.

**Does well.** The closest existing answer to the §10 open question. Their food and unit model is worth reading directly as a data-model reference.

**Breaks down.** Setup and interface cost keep it to a technical audience.

**Implication.** Open Food Facts is a credible seed for kcal, but it will not supply density, average unit weight, or aisle category — the three attributes §5.5 needs and no nutrition database carries. Tandoor is also proof that a correct model behind a poor interface still loses.

---

## Tier 2 — Soft

### Apple Notes & Notion

*General notes · everywhere · free tier*

The true incumbent. No structure, no friction, works everywhere. Most "I'll organise it later" recipes die here.

**Implication.** This sets the bar for **capture speed**. If paste → review → save is slower than pasting into a note, Cooksy loses before scaling gets a chance to impress. This is the origin of the share-sheet decision in §5.2 and the reason the review screen must be fast, not merely correct.

### Instagram & TikTok saves

*Social video · mobile · free*

Where recipes are found and hoarded in 2026 — an unstructured, unsearchable graveyard of saved reels and screenshots. The pain is real and unsolved.

**Implication.** Two things. The capture surface is the **system share sheet**, not a field inside the app — now locked in §5.2. And video recipes carry no schema markup and no pasteable text, which is an unresolved scope question the brief should answer explicitly the way it answered cookbook OCR.

### AnyList

*Grocery-first · iOS / Android / Web · freemium*

A grocery list app that grew recipes and planning, not the reverse. Many households already run the entire loop from here.

**Implication.** The live shared list of §5.10 is their home turf, and the comparison users will make hardest. Their store/aisle handling and one-thumb checkoff ergonomics are the reference implementation. See also Tier 3, where they appear again as a craft benchmark.

### Apple Reminders & Google Keep

*Shared lists · platform-native · free*

The zero-effort shared grocery list. A household with a working shared Keep list has no felt problem for Cooksy to solve.

**Implication.** The list must beat a shared Keep list at simply *being a list* before merge and pantry cleverness counts for anything. These are also the export target — §5.11's text export exists to feed exactly this.

### Cookpad & Pinterest

*Discovery-first · everywhere · free*

Recipe storage as a side effect of a social product. Enormous, free, and where most people think their recipes are kept.

**Implication.** Mostly a negative reference — the discovery feed rejected in §8. Useful as evidence that saving is not cooking: save rates are vast, cook-through rates are dismal. §9 is right to measure success as a real shop rather than a saved count.

---

## Tier 3 — Aspirational

### Mela

*Silvio Rizzi · iOS / iPadOS / Mac · paid*

The design benchmark for the category. Reader-grade typography, no chrome, an import flow that feels like a magic trick. Same author as Reeder.

**Implication.** The reference for how a recipe should read *while you are cooking it* — typographic hierarchy, ingredient/step separation, a dark mode that survives a dim kitchen. §7.4 executed properly.

### Crouton

*iOS / iPadOS / Mac · freemium*

The interaction benchmark. Tap to strike out an ingredient mid-cook, inline scaling, micro-interactions that feel physical.

**Implication.** §7.1's hero moment is a Crouton-class interaction, not a form field. Crouton is also the model for a minimal cook mode — keep-screen-awake plus tap-to-strike steps — which is *not* the timer-laden thing §8 rejects. Worth narrowing that exclusion.

### NYT Cooking

*The New York Times · iOS / Android / Web · subscription*

The editorial standard for presenting a recipe and holding trust at scale.

**Implication.** Ingredient-to-step linkage, and how to present an estimate without borrowing authority it hasn't earned — directly relevant to §5.6's "~640 kcal, never 638".

### AnyList (second appearance)

*Sync benchmark · iOS / Android / Web*

The best shared grocery list that exists. Sync so fast it feels local; category assignment essentially always right.

**Implication.** Sets the §5.10 latency bar: sub-second, optimistic, offline-tolerant checkoff. As the brief already notes, this is the one screen where milliseconds are visible.

### Things 3 & Todoist

*Outside the category · list craft*

The standard for how a list feels under one thumb: undo, gestures, empty states, instant writes, flawless offline behaviour.

**Implication.** The craft floor for list interfaces generally, and the direct source of §5.12's offline-first write model. The list gets used in a shop basement with no signal, and no recipe app has done this as well as these two.

---

## Findings against the brief

The brief is unusually complete on the hard parts — the weight model, normalisation, auditability. Every gap sat in the boring, table-stakes layer that all fifteen products above already ship.

### Resolved — folded into the brief on 20 July 2026

| Finding | Where it landed |
|---|---|
| **Share-sheet capture.** A URL field inside the app asks the user to leave where they are, switch, find a screen and paste. Every hard competitor imports from the browser or Instagram share sheet. | §4, §5.2 (rewritten as three entry paths, share sheet primary), §6.5, §11.6 |
| **Offline behaviour.** Cloud accounts from day one with no offline story, while §7.4 correctly names the shop as hostile. Shops have no signal. | §4, new **§5.12**, §5.9, §7.4, new build step **§11.0** |
| **Ingredient groups.** "For the dough / for the sauce" appears in a large share of real recipes. The parser spec had no notion of it and review had nowhere to put it. | New **§5.2.1** — optional, recipe-local, display-only; the list stays flat and aisle-grouped |
| **List lifecycle.** Undefined what happens when a shop is half-finished and a new week is generated. | §5.7 (weeks kept and duplicable forward), §5.9 (generating never destroys; dated, browsable history), §6.2, §6.3 |

### Open — raised, not yet decided

| Finding | Severity | Note |
|---|---|---|
| **User-editable aisle order** | Must-have | §5.9's walking order is store-specific. Plan to Eat and AnyList both ship reordering. Hardcoding it guarantees a one-pass trip (§9) that isn't one. |
| **Full library export** | Must-have | §5.11 exports one list and one recipe; nothing exports everything. Paprika's users tolerate a dated app largely because their data stays theirs. An optimiser asks this before typing in sixty recipes. |
| **Minimal cook mode** | Must-have | §8 rightly rejects timers, but keep-screen-awake and tap-to-strike steps are baseline in Mela, Crouton and Paprika, and are the literal expression of §7.4. Narrow the exclusion to timers only. |
| **Video recipes** | Open | A growing share of this audience's recipes arrive as Reels and TikToks — no markup, no text. In or out; say so explicitly, as the brief did for cookbook OCR. |
| **Search depth** | Open | §6 says "search, tag filters". Searching *inside* ingredients is expected, and nearly free once §5.5 exists. |
| **Sub-recipes** | Open | A base sauce reused across three dishes. Probably rightly out of scope — but §11.8 warns the data model must stop moving before sharing lands, so decide before, not after. |

---

## The read

The defensible wedge against the hard tier is **strict metric, plus the weight model, plus honest and auditable estimates**. Nobody in that tier handles portion size in grams properly, and the two most active competitors are drifting away from it — Samsung Food toward content, Fond toward permissions.

The risk is not the wedge. It is losing on the boring layer above it.

---

## Gaps in this research

Desk research only. Before any of this hardens into design decisions:

- **Hands-on teardown of Paprika, Fond and AnyList** — particularly the grocery merge audit trail and what the pantry actually feels like to maintain over a month. Screenshots to `./screens/`.
- **Parser bake-off.** Feed the same ten real recipe URLs (including at least three in cups/ounces and two with ingredient groups) to Samsung Food, Paprika and Mela, and record how much correction each demands. This is the §5.2 quality bar and currently it is an assertion, not a measurement.
- **Fond's roles model** — whether users exercise owner/editor/viewer or ignore them. Decides whether §5.10's flat permissions hold.
- **Nothing here is EU-specific.** Most sources are US-centric; aisle taxonomies and store layouts differ, and §5.5's aisle categories are unvalidated against a European supermarket.

## Sources

- [paprikaapp.com](https://www.paprikaapp.com/)
- [fond.kitchen — vs Paprika](https://fond.kitchen/vs/paprika/)
- [samsungfood.com](https://samsungfood.com/)
- [plantoeat.com — shopping list help](https://learn.plantoeat.com/help/shopping-list)
- [tandoor.dev](https://tandoor.dev/)
- [cooklang.org — Tandoor vs Mealie vs KitchenOwl](https://cooklang.org/blog/42-tandoor-vs-mealie-vs-kitchenowl/)
- [getforkee.com — best recipe manager apps 2026](https://www.getforkee.com/blog/best-recipe-manager-apps/)
- [recipeone.app — 12 best recipe apps 2026](https://www.recipeone.app/blog/best-recipe-manager-apps)

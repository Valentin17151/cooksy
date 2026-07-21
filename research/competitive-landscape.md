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

**Does well.** The pantry — quantity, purchase date, expiry, in/out-of-stock — is the proven shape of §5.8, and it has survived years of real use. Ingredient merge and aisle sort work, with **custom aisle organisation** on top. Data is stored locally with explicit offline access — a closer precedent for §5.12 than a cloud-era product has any right to be. One-time purchase with no subscription is why users tolerate an ageing interface.

**Breaks down.** No household sharing at all: recipes, plans and lists are personal, synced across your own devices only. An item can only exist in one grocery list at a time.

**Implication.** Its two loudest weaknesses are Cooksy's two wedges — household sharing (§5.10) and list lifecycle (§5.9). The single-list limitation is a known complaint and must not be inherited by accident; §5.9's "generating never destroys" rule exists because of it.

### Fond

*fond.kitchen · cross-platform · subscription*

The 2026 challenger, positioned explicitly against Paprika on exactly Cooksy's combined scope: shared library, shared plan, shared list.

**Does well.** Workspaces for up to ten members. Actively markets against the incumbent's gaps, which makes their comparison pages a free map of the category's pain points.

**Breaks down.** Unknown — needs hands-on, and the product reads as pre-launch (waitlist, "Coming soon"). An earlier draft of this document attributed an owner / editor / viewer roles model to them; **nothing on their site corroborates it** and the claim has been withdrawn.

**Implication.** Cooksy has deliberately rejected roles (§5.10) on the grounds that households run on offline trust. That decision was reaffirmed on 21 July 2026 and **now stands on its own reasoning**, not on a competitor's behaviour — which is stronger, given the competitor behaviour turned out to be unverifiable. Fond remains worth watching, but nothing in the brief is waiting on what it does.

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

**Implication.** Two things, and both were subsequently overtaken by decisions on 21 July 2026. The capture surface should be the **system share sheet**, not a field inside the app — accepted in §5.2, then **deferred to post-MVP** when the stack landed, because a PWA cannot register as a share target on iOS. And video recipes carry no schema markup and no pasteable text — now answered explicitly, and the answer is **out** (§8).

Which leaves this tier's finding half-unpaid: the capture-speed problem is real, is documented here, and MVP ships without the fix for it. The paste box carries the whole load.

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

## The user pain underneath

**Added 21 July 2026.** Synthesised across all three tiers — what fifteen products chose to build, omit and market implies a shape of user pain none of them states directly. Per the house rule in [`research.md`](./research.md), each pain carries its implication for Cooksy.

### The meta-pain: saving is not cooking

The most repeated signal in the research, arriving from three unrelated tiers:

- Instagram / TikTok — *"capture is effortless; **retrieval is hopeless**"*, with 114M reels on `#recipe` alone
- Apple Notes / Notion — *"most 'I'll organise it later' recipes die here"*
- Cookpad / Pinterest — *"save rates are vast, cook-through rates are dismal"*

And from the supply side: *"everyone leads with capture; nobody leads with correctness."* All five hard competitors market import above everything else.

**The whole market competes at the moment of saving, and that is not where the pain is.** The pain arrives four days later — at 6pm in a kitchen, or standing in aisle three — and almost nobody is there for it. This is the frame the six pains below sit inside, and it is the reason §9 measures success as a real shop rather than a saved count.

### Seven structural pains

1. **Retrieval, not capture.** The recipe is saved and cannot be reached, and certainly cannot be queried — *what can I make with this aubergine before it turns?* Storage is solved everywhere; usable storage nowhere. **Implication:** this is what §5.13's ingredient search is for, and why it was worth adding despite costing almost nothing — it addresses the largest pain in the set.

2. **The last mile is where tools quit.** The two products this research names as best-in-class at *being a list* are Things 3 and Todoist — **neither is a food app**. Offline behaviour is unaddressed on Fond's, Plan to Eat's and AnyList's own sites. The shop basement has no signal and the category has largely not noticed. **Implication:** direct support for §5.12 and build step §11.0. Paprika is the exception and the precedent — local storage, explicit offline, one-time purchase.

3. **The list is something that happens *to* you.** *"The grocery list is always derived, never authored."* Paprika allows an item to exist in only one list at a time, so a half-finished shop is destroyed by planning next week. Only AnyList treats the list as a first-class object — *"and it's the one product households actually run their shop from."* That correlation is the finding, not an aside. **Implication:** §5.9's "generating never destroys" and its dated, browsable history exist because of this.

4. **Numbers nobody will show you the parts of.** *"Trust is signalled socially, never demonstrated numerically… nobody proves a number by showing its parts."* NYT borrows trust from the masthead, Cookpad from "made 300,000+ times", Samsung from ratings. So an optimiser re-checks the merged quantity by hand — and **a tool you verify by hand has negative ROI**. **Implication:** §7.2's auditability is an unoccupied position in the entire category, and the closest thing Cooksy has to a defensible wedge.

5. **The fear tax on your own library.** Export is unaddressed on Fond's, Plan to Eat's and AnyList's sites; on Instagram/TikTok you can export nothing at all. The two products with the strongest data story — Mela ("does not collect any data") and Tandoor (GDPR, self-host, 90-day export) — have the most evangelical users. Nobody types in sixty recipes without knowing they can leave. **Implication:** full library export is post-MVP (§8.1), which leaves this pain knowingly unpaid. Worth revisiting the moment a real library exists.

6. **Quantity chaos, preserved deliberately.** *"Everyone converts units; nobody constrains them."* Crouton sells metric/imperial conversion *as a feature*; Tandoor makes conversions user-editable. A cup of flour and a cup of sugar differ by ~80 g, and every product in the set keeps that ambiguity alive. **Implication:** §5.1's three-unit rule is unique across all 15 and unvalidated by anyone's shipped behaviour — simultaneously the sharpest idea in the brief and the least externally supported.

7. **The correct model has historically shipped inside the worst interface.** Tandoor alone shares Cooksy's ingredient-first architecture and is comfortably the least approachable product of the fifteen. **The optimiser's real choice today is a good model behind Docker, or a good app that fudges the maths.** **Implication:** this is the gap Cooksy is walking into, and the reason a design-led approach to an ingredient-first product is a genuine market position rather than a preference.

### The uncomfortable part

Cooksy attacks pains 4 and 6 hardest, has good answers to 1, 2 and 3, and is walking straight into the opening described by 7.

But **two decisions taken on 21 July both raise the cost of capture, in the same pass**: review stayed mandatory (§5.2), and share-sheet capture went post-MVP (§8.1). This document's own words, from the Tier 2 entry on Apple Notes: *"if paste → review → save is slower than pasting into a note, Cooksy loses before scaling gets a chance to impress."*

Every differentiator Cooksy owns sits **downstream** of a step that just got more expensive. That is not an argument to reverse either decision — it is the reason the parser bake-off in *Gaps* is no longer optional.

Two pains are knowingly left on the table: **5** (export deferred) and **video-native recipes**, now the largest capture surface in the market and rejected in §8.

### How good is this evidence

**None of this is observed user pain.** It is inferred from vendor marketing, App Store copy, and what fifteen products chose to build or omit — desk research, no hands-on teardown, no user interviews. Absence in marketing is real signal, and the convergence across three independent tiers is worth something, but this is the same class of claim already flagged about the parser: **an assertion, not a measurement.**

The cheapest upgrade available is pain-adjacent and already listed in *Gaps*: the pantry is called the graveyard feature, and §5.8 bets a two-tier split on surviving a failure mode nobody here has watched happen.

---

## Findings against the brief

The brief is unusually complete on the hard parts — the weight model, normalisation, auditability. Every gap sat in the boring, table-stakes layer that all fifteen products above already ship.

### Resolved — folded into the brief on 20 July 2026

| Finding | Where it landed |
|---|---|
| **Share-sheet capture.** A URL field inside the app asks the user to leave where they are, switch, find a screen and paste. Every hard competitor imports from the browser or Instagram share sheet. | §4, §5.2, §6.5 — *then reversed on 21 July: the PWA decision put it post-MVP (§8.1), since iOS Safari has no Web Share Target support. The reasoning survives in §5.2; only the ship date moved.* |
| **Offline behaviour.** Cloud accounts from day one with no offline story, while §7.4 correctly names the shop as hostile. Shops have no signal. | §4, new **§5.12**, §5.9, §7.4, new build step **§11.0** |
| **Ingredient groups.** "For the dough / for the sauce" appears in a large share of real recipes. The parser spec had no notion of it and review had nowhere to put it. | New **§5.2.1** — optional, recipe-local, display-only; the list stays flat and aisle-grouped |
| **List lifecycle.** Undefined what happens when a shop is half-finished and a new week is generated. | §5.7 (weeks kept and duplicable forward), §5.9 (generating never destroys; dated, browsable history), §6.2, §6.3 |

### Decided — 21 July 2026

All six were closed in one pass, together with the five PM questions in [`comparison.md`](./comparison.md). The register lives in **§10.1** of the brief; the outcomes are recorded here against the findings that raised them.

| Finding | Raised as | Decision |
|---|---|---|
| **User-editable aisle order** | Must-have | **Rejected.** One fixed walking order. The research case was strong — and it strengthened further when the Paprika correction below showed reordering is the category default, not a Plan to Eat quirk. Overruled knowingly; §8 records it as the cheapest thing on the list to reverse if a real shop proves it wrong. |
| **Full library export** | Must-have | **Post-MVP.** Accepted as an obligation, not a feature — §8.1. |
| **Minimal cook mode** | Must-have | **Rejected**, and the recipe screen (§6.4) is expected to carry §7.4 on its own. Note the PWA does *not* block this: the Screen Wake Lock API ships on both platforms. Recorded as a scope decision so it can be revisited on honest terms. |
| **Video recipes** | Open | **Out, for now.** A whole capture pipeline, and MVP hasn't proved the text one. §8. |
| **Search depth** | Open | **In.** Search by recipe name *and* by ingredient — new §5.13. The cheapest yes in the set, exactly as this finding predicted: §5.5's normalisation had already paid for it. |
| **Sub-recipes** | Open | **In, as links.** A recipe can link to another; no nested scaling, no merged ingredients, nothing recursive in the weight model — new §5.2.2. Decided before §11.8, as this finding demanded. |

**The pattern in the outcomes:** the two findings graded *Open* both landed in scope, and two of the three graded *Must-have* were rejected. The severity column measured how strongly the category ships something, which turns out to be a poor predictor of whether Cooksy should. Worth remembering when grading the next batch.

---

## The read

The defensible wedge against the hard tier is **strict metric, plus the weight model, plus honest and auditable estimates**. Nobody in that tier handles portion size in grams properly, and the two most active competitors are drifting away from it — Samsung Food toward content, Fond toward permissions.

The risk is not the wedge. It is losing on the boring layer above it.

---

## Gaps in this research

Desk research only. Three items remain outstanding — the decisions above were taken without them, which is a fact about the decisions worth recording:

- **Parser bake-off.** Feed the same ten real recipe URLs (including at least three in cups/ounces and two with ingredient groups) to Samsung Food, Paprika and Mela, and record how much correction each demands. This is the §5.2 quality bar and currently it is an assertion, not a measurement. **Now the highest-value item on this list**, because mandatory review was reaffirmed on reasoning alone and paste is MVP's main capture road.
- **Hands-on teardown of Paprika, Fond and AnyList** — particularly the grocery merge audit trail and what the pantry actually feels like to maintain over a month. Screenshots to `./screens/`.
- **Nothing here is EU-specific.** Most sources are US-centric; aisle taxonomies and store layouts differ, and §5.5's aisle categories are unvalidated against a European supermarket. **Raised in priority by the aisle-order rejection:** with reordering off the table, the fixed default order is the only order a user gets, so it had better be right for the shops they actually walk.

*Closed:* **Fond's roles model.** No longer needed — §5.10's flat permissions were reaffirmed on their own reasoning on 21 July 2026, so nothing depends on what Fond ships.

## Sources

- [paprikaapp.com](https://www.paprikaapp.com/)
- [fond.kitchen — vs Paprika](https://fond.kitchen/vs/paprika/)
- [samsungfood.com](https://samsungfood.com/)
- [plantoeat.com — shopping list help](https://learn.plantoeat.com/help/shopping-list)
- [tandoor.dev](https://tandoor.dev/)
- [cooklang.org — Tandoor vs Mealie vs KitchenOwl](https://cooklang.org/blog/42-tandoor-vs-mealie-vs-kitchenowl/)
- [getforkee.com — best recipe manager apps 2026](https://www.getforkee.com/blog/best-recipe-manager-apps/)
- [recipeone.app — 12 best recipe apps 2026](https://www.recipeone.app/blog/best-recipe-manager-apps)

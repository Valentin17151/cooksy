# Research

Competitive teardowns and prior-art notes. Screenshots live in [`screens/`](./screens/) and are referenced from here.

**Status:** desk research done, five-axis comparison done, all eleven open questions decided on 21 July 2026. **Parser bake-off and hands-on teardowns still outstanding** — the decisions were taken without them.

## Contents

- [**Competitive landscape**](./competitive-landscape.md) — 15 products across hard / soft / aspirational tiers, with the findings folded into the brief on 20 July 2026 and how each of the six open findings was decided on 21 July. Includes **[the user pain underneath](./competitive-landscape.md#the-user-pain-underneath)** — one meta-pain and seven structural ones, synthesised across all three tiers, each with its implication for Cooksy.
- [**Comparison**](./comparison.md) — the same 15 products compared on audience · product base · key mechanism · trust · monetization, one table per tier, with screenshots in [`screens/`](./screens/). Ends with five market patterns, five differences, five PM questions **now answered**, and three corrections to the landscape doc **now applied**.
- [**Patterns — storing and retrieving a recipe**](./ux-patterns.md) — five organising principles (typed record · document · index · output-first · conversational), each with the same four-part anatomy, judged against the brief. **Names the pattern the brief already chose** — typed record — and its one failure mode, capture cost. Second place is the output-first list, under a named and measurable condition.
- [**Summary**](./summary.md) — synthesis of the three documents above for review: the 15-product matrix condensed, three market patterns and three differences, the top-3 retrieval mechanisms for MVP plus the one to refuse, the chosen interaction pattern explained through one worked scenario, and eight gaps each carrying a falsifiable hypothesis. Everything unsourced is listed as such in its own section. Also published as [`research.html`](../research.html), a single browsable page with the comparison tables and screens inline.
- [**Benchmark — retrieval**](./benchmark-retrieval.md) — one dimension, scored. Eight criteria × five best-in-niche products from outside the category (SuperCook, Eat Your Books, Apple Photos, Raycast, Todoist), plus Paprika and Tandoor as the category floor. **Scores §5.13 as written at 23/40 — below Tandoor** — names four mechanisms to transfer and one to refuse, and raises five questions for PM. Takeaways revised after PM review the same day; the pantry↔search join was declined, and description/process search added.
- [**Critique**](./critique.md) — an adversarial audit of `personas.md` and `jtbd.md`. Every claim marked **confirmed / hypothesis / invented**; then the dangerous list — claims that drive design decisions while resting on `[?]` or on invention — and three questions that would close the biggest gaps. Names the circularity at the root of the persona work, and finds that **fifteen products were read through their marketing and not one through its complaints.**
- [**Jobs to be done**](./jtbd.md) — one main job, five related jobs on the path to it, three emotional and two social, each traced to the persona and the evidence it grew from. Anything resting only on the research's or the brief's own assertion is held in a **Hypotheses** table instead, with the gap that would promote it. Includes a run wording check against product vocabulary — job statements describe the person's progress, never a feature.
- [**Personas**](./personas.md) — four personas assembled from the corpus's people-observations: **P-1 the Systematic Optimiser (primary)**, plus the Household Logistics Lead, the Reel Hoarder (the risk persona) and the Data Sovereign (the edge), with two anti-personas marking the scope boundary. Every block is source-linked; gaps say [?] and are phrased as hypotheses. Standing caveat inherited from the corpus: no interviews or user reviews sit behind any of them, so each persona is a falsifiable hypothesis carrying its own validation test.

The decision register itself lives in **§10.1 of [`CLAUDE.md`](../CLAUDE.md)** — that is the source of truth for what was decided. These documents record what the evidence said and where it was overruled.

## What's worth looking at

The brief has four areas where other products have already made the mistakes, and where seeing how they handled it is cheaper than deriving it:

- **Retrieval** — getting from intent to the right recipe in a library you already own. **Benchmarked: [`benchmark-retrieval.md`](./benchmark-retrieval.md).** It is pain #1 in the landscape doc and the brief currently answers it at the category floor.
- **Recipe capture** — paste and URL import flows, and specifically how much correction work the review step demands of the user. **Now the priority.** Review stayed mandatory and share-sheet capture went post-MVP, so paste-then-review is the only road into the product and its speed decides whether anything downstream gets used.
- **Grocery merge** — how duplicate ingredients across recipes are combined and presented, and whether the merge is auditable back to its sources
- **Portion scaling** — who reflows quantities live, who hides it behind a "recalculate" button, and what they do with `3 eggs × 1.5`
- **Pantry** — the graveyard feature. Worth finding out how existing implementations die, since §5.8 is betting on a two-tier split to avoid it.

One area to add, now that aisle reordering is rejected: **the default aisle order itself.** It's the only order a user will ever get, and it has never been validated against a European supermarket.

## What building the IA exposed — 5 August 2026

Drawing [`sitemap.md`](../sitemap.md) and [`flows.md`](../flows.md) put weight on this corpus and found four places where it holds nothing. Recorded here rather than in the IA, because these are gaps in the **research**, not in the map.

**1 · Ingredient substitution has no prior art in this corpus at all.** The product now lets a person swap one ingredient for another with three scopes — once, always, or saved as a variant copy. **Not one of the fifteen products was examined for this**, so there is no answer to the obvious questions: does anyone ship it, do they scope it, and does a variant stay linked to its parent or stand alone. Cooksy chose *stands alone*, on internal consistency with how a shared recipe saves, and on nothing external.

**2 · The parser bake-off (G-1) has changed shape and is now worth more, not less.** It was framed as *does a deterministic parse produce a review a person will tolerate*. Formatting is now done by a model, so the question is **does a model's proposal produce a review a person will tolerate** — and a second one arrived with it: **is a text-only draft, saved offline and formatted later by a queue, acceptable, or does it read as the app failing?** Both are still unrun, and the second has no prior art here either.

**3 · The persona weighting no longer matches the product, and the coverage matrix now says so numerically.** `personas.md` rates **P-2 the Household Logistics Lead** the strongest secondary persona and calls them *"the cheapest place a single conversation would change the picture."* After the household was paused, **P-2 has zero screens.** P-4 the Data Sovereign has zero too, and after bulk export was declined that is permanent. **Three of the four personas in this corpus are now unserved by the product it was written for.** That is a scope position rather than an error — but a persona document whose secondary characters have no product left should say so on its own front page, and currently does not.

**4 · Pain #1 rests on the narrowest surface in the product.** Retrieval is the corpus's loudest single finding, and the matrix gives **J-2 two screens** — the fewest of any covered job. That is defensible, since search is the substance of the Library rather than a screen of its own. It is also exactly the kind of thing worth knowing before, not after, a first real week of use.

**None of the four is closed by more desk research.** The first needs a teardown, the second needs the bake-off, the third needs a decision recorded in `personas.md`, and the fourth needs someone cooking for a month.

## Format

One section per product. For each: what it does well, where it breaks down, and the specific implication for Cooksy — a finding without an implication isn't finished.

Link screenshots as `![caption](./screens/filename.png)` so claims stay checkable.

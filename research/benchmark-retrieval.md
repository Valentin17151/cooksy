# Benchmark — retrieval

**Date:** 21 July 2026
**Dimension:** **retrieval** — the distance between *"I want to cook something"* and the right recipe **out of your own library**.
**Not** capture (benchmarked elsewhere), and **not** discovery, which §8 rejects. The library is already yours; the question is whether you can reach into it.

**Why this dimension.** [`competitive-landscape.md`](./competitive-landscape.md#seven-structural-pains) names this pain #1 — *"Retrieval, not capture… storage is solved everywhere; usable storage nowhere"* — and the meta-pain above it, *"saving is not cooking"*, is the same finding stated once more. The brief answers all of it with **§5.13**, one section, justified on the grounds that it *"costs almost nothing, because §5.5 already did the work."*

That is true of the ingredient index. It is not true of retrieval. **This document scores §5.13 as written against five best-in-niche products and puts it at the category floor** — see [Where Cooksy scores](#where-cooksy-scores-today).

**Method:** vendor documentation, official manuals and App Store listings, fetched 21 July 2026. `supercook.com` and `eatyourbooks.com` return 403 to server-side fetchers; both were read through search-result extraction and, for Eat Your Books, a third-party library guide. Claims sourced only to secondary write-ups are marked ⚠︎. No hands-on teardown — same standing caveat as the rest of `research/`.

**Revision — 21 July 2026, same day.** §6 was rewritten after PM review. The criteria (§1), the field (§2) and the scores (§3, §5) are unchanged; **what to take from them changed.** Coverage ranking was cut back to presence-only matching with no quantities on the input side, a fourth mechanism was added for description and process search, and the projected outcome fell from ~32 to **30** — bought, this time, without any dependence on inventory accuracy. The reasoning is recorded in §6 so it isn't relitigated.

---

## 1. Criteria

Eight criteria, each scored **1–5**. Anchors are given for 1 and 5 so a score is checkable rather than a vibe.

| # | Criterion | What it measures | 1 | 5 |
|---|---|---|---|---|
| **R1** | **Zero-recall find** | Can you reach an item without remembering what you called it? | Title substring only — misremember the name, lose the recipe | You never name the thing; you describe it, or its parts, and arrive |
| **R2** | **State-driven query** | Can the query be built from what you *have*, not what you remember? | No concept of inventory; every query is typed from memory | The query composes itself from stored state; zero keystrokes to a real answer |
| **R3** | **Vocabulary tolerance** | Synonyms, plurals, typos, regional names — aubergine ↔ eggplant | Literal string match; one wrong word, zero results | Semantic or fully normalised — the user's word never has to be the stored word |
| **R4** | **Composability** | Several constraints at once, including exclusion | One box, one term | Multiple constraints combine with AND / OR / NOT and hold together |
| **R5** | **Match transparency** | Does the result say **why** it surfaced, and where the match lives? | Ranked list, no explanation — a black box | Every row carries its evidence, precise enough to act on without opening it |
| **R6** | **Cost to first useful result** | Setup + keystrokes + latency + does it work with no signal | Heavy setup before anything works, or a network round-trip per query | Nothing to configure, two or three keystrokes, local, instant |
| **R7** | **Query durability** | Can a repeated question become a reusable object? | Retype it every time | Saved queries are first-class objects, one tap, persistent |
| **R8** | **The two empty cases** | What's shown before you type, and what happens when nothing matches | Blank list, then "no results" | The pre-query state is already useful; a dead end suggests the relaxation that fixes it |

R5 is the one the category has left vacant — [`comparison.md`](./comparison.md#common-market-patterns) pattern 5: *"nobody proves a number by showing its parts."* R2 and R8 are where Cooksy's own spec is silent.

---

## 2. The five products

Chosen for **best-in-niche on retrieval**, not for category adjacency. Each owns a different one of the eight criteria outright, which is itself the finding — see §4.

| Product | Niche | Why it's here |
|---|---|---|
| **[SuperCook](https://www.supercook.com/)** | Recipe search by pantry | The only product built entirely on R2. *"SuperCook only shows you recipes that require the ingredients you already have."* 11M recipes, 18,000 sites, 20 languages, a 2,000+ ingredient controlled vocabulary, voice pantry entry, and a **"missing one ingredient"** filter. 4.8★ / 22K ratings. |
| **[Eat Your Books](https://www.eatyourbooks.com/quick-tour)** | Search across cookbooks you already own | The purest statement of the problem: a library you own and cannot search. Human indexers, not OCR, build the index. *"You type eggplant tomatoes carrots in the search box, and you get a list of all the recipes in all your cookbooks that contain all three ingredients"* — and the result names **the book and the page number**. |
| **[Apple Photos](https://www.macrumors.com/how-to/ios-use-natural-language-search-photos/)** | Retrieval from an unlabelled personal library | 40,000 items, none tagged by the user, and *"pizza with mushrooms"* still works. On-device: *"This process happens on your device to protect your privacy."* The [2026 search rebuild](https://letsdatascience.com/news/apple-rebuilds-search-infrastructure-powering-spotlight-and-b37590b7) resolves *"beach trip with Sara"* offline. Memories curates unasked, while the phone charges. |
| **[Raycast Root Search](https://manual.raycast.com/search-bar)** | Known-item retrieval, keystroke economy | *"typing `msg` finds Messages, `slk` finds Slack."* Explicit published ranking order: exact alias → alias prefix → title fuzzy score → subtitle/keyword → **"Frecency (a blend of frequency and recency) score"**. *"The more often, and the more recently, you pick a result for a given query, the higher it ranks."* Plus **Reset Ranking**. |
| **[Todoist filters](https://www.todoist.com/help/articles/introduction-to-filters-V98wIH)** | Durable, composable queries | *"Filters are custom views of your tasks using specific query syntaxes."* `&`, `\|`, `!`, parentheses, `search:` keyword, relative dates, comma for multi-column views — and every filter is a persistent sidebar object. |

**Category floor, for reference** — not part of the five, but the scores are meaningless without it:

- **[Paprika 3](https://www.paprikaapp.com/help/ios/)** searches *"`Name`, `Ingredients`, `Directions`, `Description`, `Notes`, `Source`, and `Source URL`"*, with multi-ingredient AND via commas (`chicken, spinach`) and four fixed smart categories. No saved searches, no synonym resolution, no match explanation.
- **[Tandoor](https://tandoor.dev/)** is the only in-category product with real vocabulary tolerance — PostgreSQL trigram similarity, so *"chkn"* finds chicken ⚠︎ ([secondary source](https://www.blog.brightcoding.dev/2026/02/07/tandoor-recipes-the-ai-powered-kitchen-revolution-developers-love); the official docs page for search 404s). Server-side, self-hosted, so R6 is structurally capped.

---

## 3. Scores

| | R1 zero-recall | R2 state-driven | R3 vocabulary | R4 composable | R5 transparency | R6 cost | R7 durability | R8 empty cases | **Total** |
|---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| **SuperCook** | 5 | **5** | 4 | 4 | **5** | 3 | 4 | 4 | **34** |
| **Apple Photos** | **5** | 2 | **5** | 4 | 1 | **5** | 3 | 4 | **29** |
| **Eat Your Books** | 5 | 3 | 4 | 4 | **5** | 2 | 3 | 2 | **28** |
| **Raycast** | 4 | 1 | 4 | 2 | 3 | **5** | 4 | **5** | **28** |
| **Todoist** | 2 | 2 | 2 | **5** | 4 | 3 | **5** | 3 | **26** |
| *Tandoor (floor)* | *4* | *3* | *5* | *4* | *2* | *2* | *3* | *2* | *25* |
| *Paprika (floor)* | *3* | *2* | *2* | *3* | *1* | *4* | *2* | *3* | *20* |

**Score notes, where the number isn't obvious:**

- **SuperCook R6 = 3.** Once the pantry exists, results cost zero keystrokes — the best in the table. Getting there costs entering your entire kitchen, *"including oils, spices, and yes — even that old bottle of Worcestershire sauce"*, before the first useful result appears. Voice entry lowers that cost; it doesn't remove it.
- **SuperCook R8 = 4.** The pre-query state is weak (an empty pantry returns nothing), but the zero-result recovery is the best here and is literally their tagline: *"Every ingredient you add unlocks more recipes."* A dead end is presented as one item away from an answer.
- **Apple Photos R5 = 1.** It is the black box of the set — results arrive with no reason attached, and the Memories curation is [documented as opaque even to researchers](https://www.cambridge.org/core/journals/memory-mind-and-media/article/between-automated-memory-and-history-blocking-sensitive-locations-from-apple-memories/B9F494C0829A13A1E7A33D8328D758F5). Highest ceiling on finding, lowest floor on trusting.
- **Eat Your Books R6 = 2.** The index is superb because humans built it book by book; the user still has to enter their shelf, and it is an online-only subscription site.
- **Raycast R4 = 2.** Root Search is deliberately one-token. Composition happens inside a command, never in the bar — a real limit, and a deliberate one.
- **Todoist R1 = 2, R3 = 2.** `search:` is substring matching. The query language is the best in the set precisely because the matching underneath it is dumb.

---

## 4. What the spread says

**No product scores well on all eight, and the failures are not random — they split into two clusters that almost never co-occur.**

- **Finding cluster** (R1, R2, R3): SuperCook, Apple Photos, Eat Your Books. Strong retrieval, weak or absent explanation and reuse.
- **Control cluster** (R4, R5, R7): Todoist, Eat Your Books. Strong queries and provenance, weak matching underneath.
- **Raycast is the only product that treats R8 as a design problem at all** — everyone else's pre-query screen is a blank box or a browse grid.

The mirror of pattern 5 in [`comparison.md`](./comparison.md#common-market-patterns): **the products that find best explain least.** SuperCook and Eat Your Books are the exceptions, and both explain for a structural reason rather than a design one — SuperCook must tell you what's missing or the result is unusable, EYB must name the book or you cannot cook from it. Provenance became a feature because the product broke without it.

That is the transferable lesson, and it lands directly on §7.2.

---

## 5. Where Cooksy scores today

§5.13 as written: search over names, tags and ingredients; several ingredients narrow to recipes containing **all** of them; results distinguish a name match from an ingredient match; local, as-you-type, no network; synonyms resolved through §5.5 canonical ingredients.

| | R1 | R2 | R3 | R4 | R5 | R6 | R7 | R8 | **Total** |
|---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| **Cooksy, §5.13 as specified** | 4 | **2** | 4 | 3 | 3 | **5** | **1** | **1** | **23** |

R6 = 5 is earned outright — §5.12 makes local, instant, offline search a stated requirement, which is better than four of the five benchmarks manage. R3 = 4 is §5.5 paying out exactly as predicted. **The rest is at or below the category floor**, on the dimension the research names as pain #1:

- **R2 = 2.** The brief contains a pantry (§5.8) and a search (§5.13) and **no wire between them**. Both speak canonical ingredients; neither knows the other exists. *Raised here as the largest gap in the section; **closed at PM review as a deliberate decision** — the wire is not to be built, and R2 stays at 2. See §6.1 and §7.*
- **R7 = 1.** No saved searches, no filter objects, nothing. Every question is retyped.
- **R8 = 1.** Wholly unspecified. What the Library shows before you type, and what happens when a search returns nothing, are not in the brief. §6.1 says *"recipe grid/list"* — i.e. the default order is undefined.

**23 puts Cooksy below Tandoor.** The section is cheap because §5.5 paid for the index — but the index is R3, and R3 was never the pain.

---

## 6. Four mechanisms to transfer

*Revised after PM review — see the note at the head of this document.*

All four are arithmetic over local data and cost no server, which matters under §4. Only the fourth carries a genuine new cost, and it is named where it lands.

**One rule emerged from the review and is worth stating before the mechanisms, because three of them obey it:**

> **The user never types an amount. Cooksy always shows one.**

Quantities are output, never input. You search with ingredient *names*; every row answers with the amount the recipe needs. This is not a UI preference — it is the only honest arrangement, because Cooksy knows exactly what a recipe requires and knows almost nothing about what is in your kitchen (§5.8: staples carry no quantities, tracked items are opt-in and drift). Asking for amounts on the input side would be asking the user to supply the one number the app cannot verify.

### 1. Multi-ingredient search, presence only — *from SuperCook, stripped*

**The mechanism, as revised:** type a few ingredient **names** — `chicken lemon rice` — with no amounts and no units. Rank results by **how many of the typed terms the recipe contains**: all three first, then two of three, then one. Every row states which terms hit and which missed.

**What was cut, and why.** The first draft took SuperCook's coverage model wholesale — `have 6 of 8 · missing: double cream, thyme` — scored against pantry stock. That was wrong on the brief's own terms. It made retrieval depend on an inventory §5.8 deliberately refuses to keep accurate, and it quietly reintroduced the quantity problem on the input side. **Match on identity, count the query terms, and the pantry is not involved at all** — the feature then works on a fresh account with an empty pantry, which the coverage version never did.

**In Cooksy:** §5.13 already specifies that several ingredients narrow to recipes containing *all* of them. The change is one line of behaviour — **the near-misses are ranked, not discarded.** A strict AND that returns nothing for `chicken lemon rice` is a dead end; the same query returning four exact matches and then eleven two-of-three matches is an answer. Resolution runs through canonical ingredients (§5.5), so `aubergine` finds the recipe that said `eggplant`.

**Why it transfers:** it answers §5.13's own worked question — *"there is an aubergine in the fridge and it turns tomorrow"* — and it doubles as the zero-result recovery R8 has nothing for today. **R1: 4 → 5 · R4: 3 → 4 · R8 gains with it.**

**R2 is now deliberately not played.** The criterion asks whether the query can be built from stored state; Cooksy's answer is *no, on purpose*, and it stays at 2. That is a decision, not a gap, and §8 records it as one.

### 2. Match provenance on every result row — *from Eat Your Books*

**The mechanism:** EYB's result doesn't say *this book matches*. It says **which book and which page** — evidence precise enough to act on without opening anything. The index is worthless without it, because you cannot cook from a book title.

**In Cooksy — three things on the row, confirmed at review:**

1. **What matched** — the canonical ingredient, so it's clear why this recipe surfaced and which of the typed terms it answers.
2. **The amount the recipe needs** — `400 g`, at the recipe's **base servings**, labelled as such. This is the output half of the rule above: the user typed `aubergine` with no number, and the row answers with the number. Base servings rather than a scaled figure because a search result has no serving context yet, and §5.4 is explicit that scaling is a view and never mutates the stored recipe.
3. **The group, when the recipe has one** — `in "For the sauce"`. Only when the recipe has groups, exactly as §5.2.1 rules it: *"a recipe with no headings has one implicit group and shows a plain list — no empty scaffolding."* A row that says *for the sauce* tells the cook something a bare match never could: whether the aubergine is the dish or a component of it.

So the full row reads: `matched: aubergine · 400 g · in "For the sauce"`. §5.13 already promises the weak half of this (*"results distinguish a name match from an ingredient match"*); this is the strong half, and every field is already computed.

**Why it transfers:** it extends §7.2's auditability — *"merged numbers are always auditable"* — one step upstream, from the grocery line to the search result. [`competitive-landscape.md`](./competitive-landscape.md#seven-structural-pains) pain 4 calls auditability *"an unoccupied position in the entire category, and the closest thing Cooksy has to a defensible wedge"*; §3's scoring shows the same vacancy inside search, where three of five best-in-niche products score 3 or below. **R5: 3 → 5.**

### 3. Frecency as the default order, so the empty box is never empty — *from Raycast*

**The mechanism:** Raycast's published ranking ends in *"Frecency (a blend of frequency and recency) score"*, and the pre-query root list is already sorted by it. You open the bar and what you want is usually visible before you type. **Reset Ranking** exists so the learning is never a trap.

**In Cooksy:** the Library's default order is recency-and-frequency of *cooking*, not of saving — the planner (§5.7) and list history (§5.9) already record every time a recipe was cooked, dated, at no extra cost. §5.7 already observes that *"households rotate through the same fifteen dishes."* Those fifteen should be the top of the Library, unasked.

**Why it transfers:** it fixes the pre-query half of R8 (1 → 4) for the cost of a sort key, and it **substitutes for R7 at this library size**. Todoist needs saved filters because a task list has thousands of items and dozens of legitimate slices; a household with sixty recipes and fifteen live ones does not need a filter language — it needs the fifteen at the top. That is Raycast's answer to Todoist's problem, and it is much cheaper.

**Deliberately partial transfer from Todoist:** take the *idea* of a query as a reusable object if it's ever needed — a pinned chip, not a syntax. `&`, `|`, `!` and `search:` are a keyboard-and-desk interaction, and §7.4 specifies wet hands, one thumb and bad light. R7 stays at 1 for MVP, knowingly.

### 4. Description and process search, in two tiers — *from Apple Photos*

**Added at PM review.** The ask: typing `fried chicken` should return the dishes that *are* fried chicken first, and then **every meal where fried chicken is part of the cooking process** — the same move Apple Photos makes when `pizza with mushrooms` finds a photo nobody ever labelled.

**The mechanism:** one query, two labelled tiers.

| Tier | What lands in it | Matched against |
|---|---|---|
| **Dishes** | The recipe *is* the thing | Title, tags |
| **Used in** | The thing happens inside the recipe | Method steps, and any linked sub-recipe (§5.2.2) |

Never merged into one ranked list. The distinction is the answer — *"am I looking for the fried chicken, or for what to do with it"* — and §5.13 already promises results that make the reason for a match visible.

**This is the second unwired connection in the brief, and unlike the first one it's worth taking.** Sub-recipe links currently carry **no retrieval value whatsoever** — §5.2.2 is explicit that links are *"display and navigation only"* and that *"nothing traverses them but the user."* But a recipe linking to *Basic tomato sauce* is, factually, a meal where tomato sauce is part of the process. Surfacing it in the second tier reads the link without traversing it: no nested scaling, no merged ingredients, nothing recursive in the weight model. §5.2.2's guarantees survive intact.

**The honest cost, and where it lands.** Two of the three parts are free; one is not.

- **Searching the method text is free** and the incumbent already does it — Paprika searches *"`Name`, `Ingredients`, `Directions`, `Description`, `Notes`, `Source`, and `Source URL`"*. **It still scores R1 = 3.** Grep over the directions is not retrieval; `fried chicken` won't match *"fry the chicken until golden"* in any of those seven fields.
- **Resolution through canonical ingredients is free** — §5.5 already turns `chicken`, `chicken thighs` and `2 large chicken breasts` into one record.
- **The preparation vocabulary is not free.** Matching `fried` to *"fry"*, *"frying"*, *"pan-fried"*, *"shallow-fry"* needs a small controlled list of cooking verbs with their inflections — perhaps thirty to fifty entries. That is **a second dataset alongside §10's open question**, and it should be raised there rather than discovered during build. It is far smaller than the ingredient database and needs none of its four attributes, but it is real work and it is new.

**Why the cheap version is also the better one.** Apple Photos does this with an on-device model, scores a 5 on R1 for it — and scores a **1 on R5**, because a model cannot tell you why it matched. Cooksy's substitute is deterministic: canonical ingredient × preparation verb, matched in a named field. It is weaker at open-ended phrasing and **strictly better at explaining itself**, which is the only version compatible with mechanism 2. A semantic search would have broken the provenance row this benchmark is otherwise arguing for. **R1: 4 → 5.**

---

## 7. One that does not work: SuperCook's pantry **gate**

**The mechanism, verbatim:** *"SuperCook only shows you recipes that require the ingredients you already have. All the recipes you see on SuperCook are recipes you can make right now."*

It is the single most attractive idea in this benchmark. It scores SuperCook a 5 on R2 and it is the highest total in the table. **It must not be copied into Cooksy**, for three reasons that compound.

**1. It inverts the trust rule the brief already wrote.** §5.8 rule 1: *"Subtraction is always visible… An ingredient never vanishes without a trace — getting home without garlic because the app quietly assumed is the kind of failure users don't forgive."* A pantry-gated search commits exactly that failure one level up: **recipes vanish without a trace**, and it is strictly less recoverable, because a missing grocery line is discovered in the shop while a missing recipe is never discovered at all. You cannot tap *"actually, I'm out"* on a result you were never shown.

**2. It demands an inventory completeness §5.8 explicitly refuses to require.** SuperCook's model needs your whole kitchen — *"even that old bottle of Worcestershire sauce in the back of the fridge"* — and a 2,000-ingredient picker to enter it. Cooksy's staples tier deliberately holds **no quantities at all**, its tracked tier is **opt-in**, and the brief states plainly that tracked quantities *"drift out of date the moment you cook without telling the app, and no design fixes that."* Gating retrieval on a knowingly incomplete, knowingly stale inventory produces §7.3's silent wrongness — *"the only unrecoverable failure"* — and produces it on the screen where the user has the least chance of noticing.

**3. The economics are inverted, and this is the part that actually kills it.** SuperCook filters **11 million recipes you do not own**. Hiding is the only thing that makes that set usable, and a false negative costs nothing because there are four hundred more. Cooksy searches **sixty recipes you personally chose and corrected at review**. There is nothing to hide *from* — and at that size a filter that removes results removes the thing the user is looking for. §5.8's second rule already says it: *"The pantry never blocks anything."* Search is not an exception to that; it's the clearest case of it.

**The fix.** Keep the *shape* of SuperCook's ranking and drop everything it ranks against: **count the ingredients the user typed, not the ingredients they own** (§6.1). A recipe you can't cook tonight is still the recipe you were searching for — you'll cook it Thursday, and it belongs in the grocery list, which is the actual product.

**The PM review reached the same place from the other side, and that convergence is the strongest evidence in this document.** This section rejected pantry-gating on trust grounds — hidden results are silent wrongness. The review rejected it on input grounds: *search by a few ingredients, but without quantity, because Cooksy doesn't know anything about this.* Two independent arguments, one conclusion: **retrieval must not depend on inventory state.** §6's revision applies it to the input as well as the output, which is further than this section originally went.

**Runner-up rejection, revised:** Apple Photos' semantic natural-language search is the highest-ceiling mechanism here and is out on §4 — it needs either a model or a server, and Cooksy has neither. **§6.4 is the zero-budget substitute**, and per the argument there it is not merely a compromise: a semantic matcher cannot state why it matched, which is why Photos scores 1 on R5 and why adopting it would have cost the provenance row in §6.2.

---

## 8. Questions for PM — all closed, 21 July 2026

**None outstanding.** Five were raised and all five were answered the same day, in two rounds. The decision register is **§10.2 of [`CLAUDE.md`](../CLAUDE.md)**; the outcomes are recorded here against the findings that raised them, per the house rule in [`research.md`](./research.md).

| Raised | Decision | Where it landed |
|---|---|---|
| **Does the pantry feed search, and does it rank by coverage?** Raised as the largest single gap — R2 = 2. | **No, and the wire is not to be built.** Answered from two directions at once: this document rejected gating on trust grounds, the PM rejected quantities on input grounds. R2 stays at its floor **by decision**. | §5.13, §8 |
| **Where does the preparation vocabulary come from?** The only new data cost in this benchmark. | **Generated by a model, never queried through one.** Authoring-time generation adopted, import-time enrichment permitted, query-time inference ruled out — it would break §4, §5.12 and §5.13, and cost the provenance row §6.2 exists to win. | §10 |
| **What does the Library show before anything is typed?** Undefined; §6.1 of the brief said only "recipe grid/list". | **Frecency of cooking**, not of saving, and resettable. | §5.13 |
| **What happens on zero results?** Undefined. | **Partial matches are ranked, never discarded** — the empty state is replaced rather than designed. | §5.13 |
| **Saved searches — out for MVP, or unconsidered?** | **Out, and now recorded as a rejection** with its reasoning, the same treatment §8 gave cook mode. Frecency substitutes at sixty recipes. | §8 |
| **Does reading sub-recipe links for search violate §5.2.2?** | **Permitted.** Reading is not traversing; one hop, nothing crosses the link. §5.2.2 amended to say so. | §5.2.2, §5.13 |
| **Do the Dishes / Used in tiers apply to every search, or only description searches?** *(raised at review)* | **Universal** — and it doubles as the concrete form of §5.13's existing name-vs-ingredient promise, so it is one mechanism rather than two. | §5.13 |

**Projected outcome: 30 of 40.** Down from the ~32 the first draft claimed, and better earned — the earlier number was bought with a pantry join that made retrieval depend on an inventory the brief refuses to keep accurate. **R2 stays at 2 by decision**; the gain moves to R1 (4 → 5), R4 (3 → 4), R5 (3 → 5) and R8 (1 → 4).

**What this pass did not buy.** The scores above are still a desk assessment of a specification, not a measurement of a product — the standing caveat on all of `research/`. Two things would now genuinely test it: whether preparation search survives contact with real method text, which the parser bake-off could measure at the same time as the parse; and whether frecency-of-cooking is the right default order or merely the cheapest one, which cannot be known until a library has been cooked from for a month.

---

## Sources

- [supercook.com](https://www.supercook.com/) · [App Store listing](https://apps.apple.com/us/app/supercook-recipe-by-ingredient/id1477747816) · [Google Play](https://play.google.com/store/apps/details?id=com.supercook.app&hl=en_US) · [The Kitchn write-up](https://www.thekitchn.com/web-resource-supercook-55014)
- [eatyourbooks.com — quick tour](https://www.eatyourbooks.com/quick-tour) · [Arlington Public Library guide to EYB](https://library.arlingtonva.libguides.com/abouteyb) · [Baking Bites review](https://bakingbites.com/2011/09/search-all-your-cookbooks-with-eat-your-books/)
- [Raycast Manual — Search Bar](https://manual.raycast.com/search-bar) · [Raycast 1.40.0 — Fuzzy Search changelog](https://www.raycast.com/changelog/macos/1-40-0) · [Raycast Manual — Command Aliases & Hotkeys](https://manual.raycast.com/command-aliases-and-hotkeys)
- [Todoist — Introduction to filters](https://www.todoist.com/help/articles/introduction-to-filters-V98wIH) · [Todoist — 24 filters](https://www.todoist.com/inspiration/todoist-filters)
- [MacRumors — natural language search in Photos](https://www.macrumors.com/how-to/ios-use-natural-language-search-photos/) · [Apple's 2026 search infrastructure rebuild](https://letsdatascience.com/news/apple-rebuilds-search-infrastructure-powering-spotlight-and-b37590b7) · [AI CERTs — Spotlight/Mail/Photos search](https://www.aicerts.ai/news/apple-boosts-ai-search-features-across-spotlight-mail-photos/) · [Cambridge — *Between automated memory and history*](https://www.cambridge.org/core/journals/memory-mind-and-media/article/between-automated-memory-and-history-blocking-sensitive-locations-from-apple-memories/B9F494C0829A13A1E7A33D8328D758F5)
- [Paprika user guide — iOS](https://www.paprikaapp.com/help/ios/) · [tandoor.dev](https://tandoor.dev/) · [Tandoor search behaviour ⚠︎ secondary](https://www.blog.brightcoding.dev/2026/02/07/tandoor-recipes-the-ai-powered-kitchen-revolution-developers-love)
- [Cookpad — App Store](https://apps.apple.com/us/app/cookpad-recipes-homemade-food/id585332633) *(context only: ingredient-first search at 100M users, 23 countries)*

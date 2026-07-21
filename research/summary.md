# Research synthesis

**Date:** 21 July 2026
**Sources:** [`competitive-landscape.md`](./competitive-landscape.md) · [`comparison.md`](./comparison.md) · [`benchmark-retrieval.md`](./benchmark-retrieval.md) · [`ux-patterns.md`](./ux-patterns.md) · 20 screenshots in [`screens/`](./screens/)
**Decision register** — §10.1 of [`CLAUDE.md`](../CLAUDE.md). This document records **what the evidence said**, not what was decided.

**Sourcing rule.** Every fact carries a link or a screenshot. Where there is no source, it says so: **unverified**. Nothing is invented. The consolidated list of everything unsourced is in [section 5](#5-unverified).

**Keys used below.** `MP-1…MP-3` market patterns · `D-1…D-3` differences · `M-1…M-4` retrieval mechanisms · `P1…P5` interaction patterns (matching [`ux-patterns.md`](./ux-patterns.md)) · `G-1…G-8` gaps.

---

## 1. COMPETITORS

### 1.1 The matrix: 15 products × 5 axes × 3 tiers

Axes: **audience · product base · key mechanism · trust · monetization.** Full wording in [`comparison.md`](./comparison.md); condensed here.

#### Tier 1 — Hard (same product, same audience)

| Product | Audience | Product base | Key mechanism | Trust | Monetization | Source |
|---|---|---|---|---|---|---|
| **Paprika 3** | multi-device cooks who shop systematically | **recipe library**; plan and list derived from it | ingredient merge + aisle sort, **custom aisle order**, pantry tracking quantity / purchase date / expiry | "all of your data is stored locally", explicit offline, one-time purchase; **no household sharing at all** | **one-time, per platform**, $4.99 iOS | [paprikaapp.com](https://www.paprikaapp.com/) · [screen](./screens/t1-paprika.png) |
| **Fond** | enthusiasts, "2,400+ on the waitlist" | extracted recipes (URL/photo/social) over a normalised ingredient layer | "Save–Plan–Shop–Cook" plus **August**, an assistant scoped to *your* library rather than the open internet | sync across 4 platforms; offline, export and permissions — **unverified** | freemium, AI behind the paywall; prices unpublished | [fond.kitchen](https://fond.kitchen/vs/paprika/) · [screen](./screens/t1-fond.png) |
| **Samsung Food** | global cooks + health-goal seekers + communities | **content platform**; personal recipe box second | import from any site → drag-and-drop week → "one click" list → nutrition and Health Score | 4.8 rating, Webby nomination; against that, a hardware giant's account and AI plans | free + Food+ $59.99/yr — **not re-verified** (403s to fetchers) | [samsungfood.com](https://samsungfood.com/) · [screen](./screens/t1-samsung-food.png) |
| **Plan to Eat** | organised households, "if you love meal planning" | **planner-first**; the list is a by-product of the calendar | "Pick your meals, and we'll automatically build your grocery list". **User-reorderable categories**, per-store lists, Staples, separate pantry | 14-day trial without a card, testimonials; offline, export, privacy — **unverified** | subscription only: $5.95/mo or $49/yr | [plantoeat.com](https://learn.plantoeat.com/help/shopping-list) · [screen](./screens/t1-plan-to-eat.png) |
| **Tandoor** | self-hosters, "cooking enthusiasts with huge collections" | **ingredient / food database** — the only one of the fifteen built this way | import from thousands of sites, sort by supermarket, **editable unit conversions**, nutrition + pricing, live list sync | strongest data story in the set: OSS, self-host, "GDPR Compliant — Made in Germany", no tracking, 90-day export | OSS free + hosted €0 / €1.99 / €3.49 / **€4.99 "Premium AI"** | [tandoor.dev](https://tandoor.dev/) · [screen](./screens/t1-tandoor.png) · [app 🔒](./screens/t1-tandoor-app-restricted.png) |

#### Tier 2 — Soft (different product, same job) — **where recipes actually live today**

| Product | Audience | Product base | Key mechanism | Trust | Monetization | Source |
|---|---|---|---|---|---|---|
| **Apple Notes / Notion** | everyone — which is the point | **unstructured documents**: no schema, no quantities, infinite tolerance | instant capture from anywhere via the system share sheet; nothing to configure, nothing to correct | trusted because the product is *general* — no cooking vendor to outlive | Notes ships with the OS; Notion freemium | [Notion](./screens/t2-notion.png) · [Apple Notes 🔒](./screens/t2-apple-notes-restricted.png) |
| **Instagram / TikTok saves** | everyone under ~45; where recipes are **found** in 2026 | **someone else's video**; a save is a bookmark on content you don't own | infinite discovery + one-tap save. Capture is free, **retrieval is hopeless**: 114M reels on `#recipe` alone | none, structurally: no search, no export, no quantities | free, ad-funded | [`#recipe` tag](./screens/t2-instagram-recipe-tag.png) |
| **AnyList** | households coordinating a shop | **the list itself**: "the best way to create and share a grocery shopping list" | "Any changes made to a shared list will show up instantly to everyone" + automatic category grouping + Siri | sync across Mac/PC/iOS/iPad; offline, export, privacy — **unverified** | $9.99/yr individual · $14.99/yr household | [screen](./screens/t2-anylist.png) · [pricing](./screens/t3-anylist-complete-pricing.png) |
| **Apple Reminders / Google Keep** | everyone; zero effort | **generic checkable items**: no quantities, no ingredients, no semantics | shared list, checkbox, already installed, free, works everywhere | platform-grade sync and offline | free with the platform | [Google Keep 🔒](./screens/t2-google-keep-restricted.png) |
| **Cookpad / Pinterest** | discovery-seekers; Cookpad is "Japan's #1 recipe search" | **UGC content** and a **visual bookmark graph**; storage is a side effect of browsing | social proof as ranking: つくれぽ counts, "made 300,000+ times" | crowd validation substitutes for correctness: vast save rates, dismal cook-through | Cookpad freemium; Pinterest advertising | [Cookpad](./screens/t2-cookpad.png) · [Pinterest](./screens/t2-pinterest.png) |

#### Tier 3 — Aspirational (the craft bar)

| Product | Audience | Product base | Key mechanism | Trust | Monetization | Source |
|---|---|---|---|---|---|---|
| **Mela** | design-conscious Apple users | personal library, **no mandatory account** — a private iCloud container | **in-app browser with live recipe detection**: browse → auto-detect → preview → save. Plus RSS, OCR for physical books, import from YouTube / TikTok / Instagram descriptions | **strongest privacy position of the fifteen**: "Mela does not collect any data… does not depend on or use any third-party service" | free + one-time IAP, Mela+ $6.99 | [screen](./screens/t3-mela.png) |
| **Crouton** | people who cook *from the device* | "a home for your favourite recipes", on iCloud | **step-by-step cook mode**: tap an ingredient inside a step to get its quantity, hands-free advance, scaling by servings *or per ingredient*, self-naming timers | iCloud, household, Family Sharing. Weaker than Mela: email and user ID are linked | hybrid: $1.99/mo · $14.99/yr · **$24.99 lifetime** | [screen](./screens/t3-crouton.png) |
| **NYT Cooking** | subscribers | **editorial content library**; the personal Recipe Box is subscriber-gated | editorial authority — "tested and perfected" — plus community cooking notes | authority borrowed from the masthead, not built by the software | subscription; price **not shown** on any captured page | [screen](./screens/t3-nyt-cooking.png) · [Recipe Box 🔒](./screens/t3-nyt-recipe-box-restricted.png) |
| **AnyList** *(as sync benchmark)* | households mid-shop, in two different aisles | same product as tier 2; judged here on execution | shared-list sync so fast it reads as local; category assignment essentially always right | reliability as trust: it has never lost a checkoff | $9.99 / $14.99 per year | [pricing](./screens/t3-anylist-complete-pricing.png) |
| **Things 3 / Todoist** | outside the category — the list-craft reference | task objects | one-thumb ergonomics: instant writes, undo, gestures, empty states, flawless offline | Things: two Apple Design Awards. Todoist: roles and permissions at Business tier | Things one-time; Todoist freemium. **Numeric prices not rendered publicly** | [Things](./screens/t3-things.png) · [Todoist](./screens/t3-todoist.png) |

---

### 1.2 Three common market patterns

There are five in [`comparison.md`](./comparison.md#common-market-patterns). The three that most affect decisions:

**MP-1. Everyone sells capture; nobody sells correctness.**
All five hard competitors market import — "save from any website", "from wherever you find them". Not one markets quantity accuracy, unit integrity or an audit trail. The correction step is universally treated as a cost to hide, never a feature to sell.
→ **Consequence:** the mandatory review screen (§5.2) is **contrarian positioning**, not table stakes. That cuts both ways.
*Source:* [`comparison.md` §Common market patterns](./comparison.md#common-market-patterns), synthesised across the five tier-1 screens.

**MP-2. The grocery list is always derived, never authored.**
In every hard product the list is an output of the plan. Only **AnyList** treats it as a first-class object with a life of its own — and it is the one product households actually run their shop from. Paprika allows an item to exist in only one list at a time, so a half-finished shop is destroyed by planning next week.
→ **Consequence:** direct support for §5.9's "generating never destroys" and its dated, browsable history.
*Source:* [`comparison.md`](./comparison.md#common-market-patterns) · [`competitive-landscape.md` pain 3](./competitive-landscape.md#seven-structural-pains) · [AnyList screen](./screens/t2-anylist.png)

**MP-3. Trust is signalled socially, never demonstrated numerically.**
NYT borrows it from the masthead, Cookpad from "made 300,000+ times", Samsung from ratings and awards, Mela and Things from design awards. **Nobody proves a number by showing its parts.**
→ **Consequence:** auditability (§7.2) is an **unoccupied position in the entire category**, and the closest thing Cooksy has to a defensible wedge.
*Source:* [`comparison.md`](./comparison.md#common-market-patterns) · [`competitive-landscape.md` pain 4](./competitive-landscape.md#seven-structural-pains)

*The other two patterns — household sharing as table stakes, AI as the 2026 paywall — are in the source.*

### 1.3 Three differences

**D-1. Monetization shape predicts architecture, reliably.**
One-time (Paprika $4.99, Mela $6.99, Things) → local-first, offline, no server, **no sharing**. Subscription (Plan to Eat, Fond, Samsung, NYT) → server-side, sync, sharing, AI. Free/ad or OSS (Instagram, Keep, Tandoor self-host) → you're either the product or the sysadmin.
→ **Cooksy wants the offline guarantees of column one with the sharing and server-side import of column two** — the expensive corner of the matrix, while §8 rules out revenue. The PWA decision closes the *client* half of that corner for free; the server half (URL import, the read-only link, live sync) remains and is capped by free-tier hosting.
*Source:* [`comparison.md` §Key differences](./comparison.md#key-differences) · §3, §4 of the brief.

**D-2. Centre of gravity differs wildly — and only one product shares Cooksy's.**
Library (Paprika, Mela, Crouton) · planner (Plan to Eat) · list (AnyList) · content (Samsung, Cookpad, NYT) · **ingredient database (Tandoor, alone)**. Tandoor is the only one that shares Cooksy's ingredient-first centre, and it is comfortably the least approachable product in the set.
→ **The consequence, and the single most important sentence in the research:** the correct model has historically shipped inside the worst interface. The optimiser's real choice today is a good model behind Docker, or a good app that fudges the maths. That is the gap Cooksy is walking into.
*Source:* [`comparison.md`](./comparison.md#key-differences) · [`competitive-landscape.md` pain 7](./competitive-landscape.md#seven-structural-pains) · [tandoor.dev](https://tandoor.dev/)

**D-3. Everyone converts units; nobody constrains them.**
Crouton advertises metric/imperial conversion **as a feature** — it deliberately preserves both systems. Tandoor makes conversions user-editable. A cup of flour and a cup of sugar differ by roughly 80 g, and all fifteen products keep that ambiguity alive.
→ **Consequence:** the three-unit rule `g` / `ml` / `pcs` (§5.1) is **unique across all fifteen and validated by no one's shipped behaviour.** Simultaneously the sharpest idea in the brief and the least externally supported.
*Source:* [`comparison.md`](./comparison.md#key-differences) · [`competitive-landscape.md` pain 6](./competitive-landscape.md#seven-structural-pains) · [Crouton screen](./screens/t3-crouton.png)

---

## 2. BENCHMARK — retrieval from your own library

**Dimension:** the distance between "I want to cook something" and the right recipe **out of a library that is already yours**. Not capture, not discovery.
**Field:** five best-in-niche products from **outside the category** — SuperCook, Eat Your Books, Apple Photos, Raycast, Todoist — plus Paprika and Tandoor as the category floor. Eight criteria, 1–5 each.
**Source:** [`benchmark-retrieval.md`](./benchmark-retrieval.md).

**Where Cooksy stands: 23 of 40** — below Tandoor (25), on the dimension the research names as pain #1. Only two scores are earned outright: R6 = 5 (local, instant, offline — §5.12) and R3 = 4 (synonyms through §5.5). The failures are **R7 = 1** (no saved searches), **R8 = 1** (what the Library shows before you type, and what happens on zero results, are unspecified) and **R2 = 2**.

**Selection criterion for the top three:** a mechanism qualifies for MVP if it is **arithmetic over local data requiring neither a server nor a new dataset** (§4, zero budget). Exactly three of four pass.

### Top 3 mechanisms for MVP

**M-1. Multi-ingredient search, presence only — from SuperCook, with the pantry dependency stripped out.**
You type **names** with no amounts: `chicken lemon rice`. Results rank by **how many of the typed terms the recipe contains**: all three first, then two of three, then one. Every row states which terms hit and which missed.
**Why it works:** §5.13 already promises narrowing to recipes containing *all* the ingredients. The change is one line of behaviour — **near-misses are ranked, not discarded.** A strict AND returning nothing is a dead end; the same query returning four exact matches and then eleven two-of-three matches is an answer. It doubles as the zero-result recovery that does not exist today.
**Cost:** none — it resolves through the canonical ingredients of §5.5, already paid for.
**Moves:** R1 4→5 · R4 3→4 · R8.
*Source:* [supercook.com](https://www.supercook.com/) · [App Store](https://apps.apple.com/us/app/supercook-recipe-by-ingredient/id1477747816) · [`benchmark-retrieval.md` §6.1](./benchmark-retrieval.md)

**M-2. Match provenance on every result row — from Eat Your Books.**
EYB doesn't say *this book matches*. It says **which book and which page** — evidence precise enough to act on without opening anything. The index would be worthless without it, because you cannot cook from a book title.
**In Cooksy — three fields per row:** what matched (the canonical ingredient) · the amount the recipe needs (`400 g`, at **base servings**, labelled as such) · the group, where the recipe has one. The full row reads: `matched: aubergine · 400 g · in "For the sauce"`.
**Why it works:** it is §7.2 one step upstream — not on the grocery line but on the search result. And it fills exactly the vacancy identified in **MP-3**: three of the five best-in-niche products score R5 ≤ 3.
**Cost:** none — all three fields are already computed.
**Moves:** R5 3→5.
*Source:* [eatyourbooks.com/quick-tour](https://www.eatyourbooks.com/quick-tour) · [Arlington Public Library guide](https://library.arlingtonva.libguides.com/abouteyb) · [`benchmark-retrieval.md` §6.2](./benchmark-retrieval.md)

**M-3. Frecency as the default order, so the empty box is never empty — from Raycast.**
Raycast's published ranking ends in a "Frecency (a blend of frequency and recency) score", and the **pre-query** list is already sorted by it: you open the bar and what you want is usually visible before you type. **Reset Ranking** exists so the learning is never a trap.
**In Cooksy:** the Library's default order is frequency and recency of **cooking**, not of saving. The planner (§5.7) and list history (§5.9) already date every cook, so this costs one sort key. §5.7 itself observes that households rotate through the same fifteen dishes — those fifteen belong at the top, unasked.
**Why it works:** it fixes the pre-query half of R8 for the price of a sort key **and substitutes for R7 at this library size.** Todoist needs a filter language because a task list holds thousands of items; a household with sixty recipes needs the fifteen at the top, not operators.
**Moves:** R8 1→4 · substitutes for R7 (which stays at 1, knowingly).
*Source:* [Raycast Manual — Search Bar](https://manual.raycast.com/search-bar) · [Todoist — filters](https://www.todoist.com/help/articles/introduction-to-filters-V98wIH) · [`benchmark-retrieval.md` §6.3](./benchmark-retrieval.md)

**Together: 23 → 30 of 40.** R1 +1, R4 +1, R5 +2, R8 +3.

### The fourth mechanism, and why it sits outside the top three

**M-4. Description and process search, in two tiers — from Apple Photos.** `fried chicken` returns first the dishes that *are* fried chicken (tier **Dishes** — title, tags), then every meal where frying chicken is part of the process (tier **Used in** — method steps, linked sub-recipes §5.2.2).

It is excluded for two independent reasons:

1. **It is the only mechanism carrying a new data cost.** For `fried` to reach *fry*, *frying*, *pan-fried*, a small controlled vocabulary of cooking verbs is needed — **a second dataset alongside the open question in §10**. Smaller than the ingredient database, but real new work.
2. **On the R1–R8 scale it adds no points beyond M-1** — both lift R1 from 4 to 5. That is the rubric running out of cells rather than a verdict on the mechanism: two tiers of results is a new capability the criteria simply have no column for.

*Source:* [MacRumors — natural language search in Photos](https://www.macrumors.com/how-to/ios-use-natural-language-search-photos/) · [`benchmark-retrieval.md` §6.4](./benchmark-retrieval.md) · the decision on where the vocabulary comes from is §10 of the brief.

### One mechanism that will not work: **SuperCook's pantry gate**

**Verbatim:** *"SuperCook only shows you recipes that require the ingredients you already have. All the recipes you see on SuperCook are recipes you can make right now."* It is the single most attractive idea in the benchmark: it scores SuperCook a 5 on R2 and the highest total in the table, 34.

**It must not be copied, for three compounding reasons:**

1. **It inverts the trust rule the brief has already written.** §5.8: *"subtraction is always visible… an ingredient never vanishes without a trace."* A pantry-gated search commits exactly that failure one level up: **recipes vanish**, and it is strictly less recoverable — a missing grocery line is discovered in the shop, a missing recipe is never discovered at all. You cannot tap *"actually, I'm out"* on a result you were never shown.
2. **It demands an inventory completeness §5.8 explicitly refuses to require.** SuperCook needs the whole kitchen — *"even that old bottle of Worcestershire sauce"* — and a 2,000-ingredient picker to enter it. Cooksy's staples carry no quantities at all, the tracked tier is opt-in, and the brief states plainly that tracked quantities drift the moment you cook without telling the app. Gating retrieval on a knowingly incomplete, knowingly stale inventory is §7.3's silent wrongness, on the screen where it is hardest to notice.
3. **The economics are inverted, and this is what actually kills it.** SuperCook filters **11 million recipes you do not own**: hiding is the only thing that makes that set usable, and a false negative costs nothing because there are four hundred more. Cooksy searches **sixty recipes you personally chose and corrected at review**. There is nothing to hide *from* — and at that size, a filter that removes results removes the thing you were looking for.

**What to take instead:** the *shape* of SuperCook's ranking, and nothing it ranks against. **Count the ingredients the user typed, not the ingredients they own** (M-1). A recipe you can't cook tonight is still the recipe you were searching for — you'll cook it Thursday, and it belongs in the grocery list, which is the actual product.

*Source:* [supercook.com](https://www.supercook.com/) · [The Kitchn on SuperCook](https://www.thekitchn.com/web-resource-supercook-55014) · [`benchmark-retrieval.md` §7](./benchmark-retrieval.md) · §5.8, §7.3 of the brief.

---

## 3. PATTERNS

### 3.1 The question a pattern answers

Not "what does the screen look like", but **what the app treats as its primary object, and who holds the structure.** Everything that can be computed follows from that answer.

Five were considered — not five ways to draw a list, but five different answers:

| | Pattern | Primary object | Who holds the structure | Examples |
|---|---|---|---|---|
| **P1** | **Typed record** | a row in a database | the app, at capture | Paprika, Grocy, Airtable |
| **P2** | **Document** | a note | nobody — the human, in their head | Apple Notes, Obsidian, a box of index cards |
| **P3** | **Index** | the query | the index, at search time | Gmail, Spotlight, Apple Photos |
| **P4** | **Output artifact** | the grocery list | the artifact itself, for one week | AnyList, Bring!, a whiteboard on the fridge |
| **P5** | **Conversation** | the utterance | a model, on demand | ChatGPT, Alexa lists |

### 3.2 One scenario, run through all five

The fastest way to see the difference is to run a single case.

> **Scenario.** You save a recipe that says "2 onions". Three days later you want to **double the portions** and produce **one grocery list** together with another recipe that says "200 g onion".

| | What gets stored | Doubling | Merging the two recipes |
|---|---|---|---|
| **P1** typed record | `2` · `pcs` · `onion` *(canonical ingredient)* | `4 pcs` — automatically, reflowing live | `onion — 200 g + 4 pcs`; the line opens to show which recipes contributed what |
| **P2** document | the text "2 onions" | in your head | by hand, on a scrap of paper |
| **P3** index | anything; the point is to find it | **the index doesn't do this** — it answers "where", not "how much" | doesn't do it |
| **P4** output artifact | nothing: "2 onions" goes straight onto this week's list | **nothing to apply it to** — no base serving count exists | the list *is* the merge, but next week you type it all again |
| **P5** conversation | text, as the model understood it | the model says "4 onions" | the model states a number — **where it came from cannot be checked**; and in the shop with no signal there is no answer at all |

**What the table shows.** The entire product loop (§1) — *save → set portions → plan → get one list* — is four operations **on structure**. The "doubling" and "merging" columns are filled in for exactly one pattern.

### 3.3 Adopted: P1, the typed record

**What it means concretely.** An ingredient is stored not as a phrase but as **a set of fields with known types**: quantity (number), unit (one of three: `g`/`ml`/`pcs`), ingredient (a reference to a canonical record), note, a non-scalable flag. Capture is a funnel ending in a form: paste → parse → **review and correct** → save. And everything the user sees afterwards — the recipe card, the rescaled list, the merged shop, the calorie figure — is **not a set of separate features but projections over those rows**.

**Three reasons:**

**1. Everything Cooksy displays is arithmetic, and arithmetic requires types.**
The weight model (§5.3), live portion rescaling (§5.4), kcal/100 g (§5.6), the grocery merge (§5.9) — these are not features you can "add". They are computations that either have typed rows underneath them or do not exist. §5.1 is the same decision seen from the other side: a product that **banned tablespoons** to guarantee a type has already chosen this pattern. The rest is consequence.

**2. The canonical ingredient is a join key, and only this pattern has anything to join on.**
**Four** features resolve through one record: the grocery merge, calories, the pantry, ingredient search. In P2, "onion" is a string, and those same four features become four separate heuristics, each failing differently on "2 large yellow onions". The brief's own *"every hour spent here pays out four times"* is a description of a normalised schema — the 4× exists precisely because there is one table to join against.

**3. The promise to show a number's parts requires stored provenance.**
§7.2 and §7.3 are unreachable in P3 and P5: both an index and a model return results they **cannot explain** — which is exactly the ground on which §10 ruled out a model at query time. This is also the only pattern where §5.12 comes free: records on the device plus arithmetic is a local read, with no spinner and no network.

**The cost, and where it lands.** P1 has exactly one weakness — **the cost of capture**. The brief pays it deliberately, and twice over: review stayed mandatory on every path (§5.2), and share-sheet capture moved to post-MVP (§8.1), leaving paste as the only road into the product. The conclusion follows directly: **the review screen and parser speed are the highest-risk surfaces in MVP**, not the planner and not the pantry. The mitigation already in the brief is the right one — *make correcting a row faster than typing it from scratch.*

### 3.4 Verdicts on the rest — one line each

| | Pattern | Verdict | Why |
|---|---|---|---|
| **P2** | Document | **Rejected** | The incumbent, and the reason Cooksy exists. It wins on the only axis where it can't be beaten — capture speed — and loses **everything downstream at once**: §1's loop doesn't work, §5.5's join is impossible, M-2's evidence row is impossible. **The document is the fastest way to store a recipe and the slowest way to use one.** §2's audience already owns the notes app; what they resent is exactly the residue it leaves. |
| **P3** | Index | **Absorbed** | §5.13 has already taken its useful half: two tiers of results with stated evidence, and frecency ordering. Query syntax and saved searches are rejected (§8) — at sixty recipes a filter language isn't needed, and operators are a keyboard-and-desk interaction while §7.4 specifies wet hands and one thumb. |
| **P4** | Output artifact | **Reserve** | Plan B under condition X — see **G-2**. The pivot is cheap: tab order and the primary action change, **the data model does not move**. |
| **P5** | Conversation | **Split** | §10 permits a model at authoring and import time and **forbids it at query time**. A model may *write* the data; it never stands between a keystroke and a result. |

**The board / canvas** (Trello, Miro) was considered and left out of the five: Cooksy already uses it where it belongs — the week grid (§5.7) *is* a board — and as a *library* pattern it is browse with worse density plus the precision gestures §7.4 forbids.

**Sourcing for this section.** The products named as examples have sources in section 1 or screenshots. **The P1–P5 classification itself is this research's own analytical frame; it has no external source.** Full version: [`ux-patterns.md`](./ux-patterns.md).

---

## 4. CONCLUSIONS — gaps, hypotheses, provenance

For each gap: a **falsifiable hypothesis**, **which section above it follows from**, and **how to test it**.

### G-1 · Capture speed

**Hypothesis.** If `paste → review → save` takes longer than pasting the same text into Apple Notes, the library never accumulates — and **no mechanism downstream fires, because there is nothing for it to fire on**.
**Follows from:** section **1** (MP-1: everyone sells capture, nobody sells correctness; tier 2 sets the speed bar) + section **3** (P1's only weakness is precisely the cost of capture).
**Test.** The parser bake-off: the same 10 real URLs (at least 3 in cups/ounces, 2 with ingredient groups) through Samsung Food, Paprika and Mela, measuring how much correction each demands. Today this is an **assertion, not a measurement**, and it is named the most valuable outstanding item in the research.
**Status:** not run.

### G-2 · Condition X: whether the library reaches critical mass at all

**Hypothesis.** If after 4 weeks the library holds fewer than 15 recipes and the median times-cooked is 1, the archive is not earning its capture cost — and the product's primary object should become the list (P4), not the library.
**Follows from:** section **3** (P4 as reserve) + section **1** (MP-2: only AnyList treats the list as a first-class object, and it is the one households actually shop from).
**Test.** Two metrics from week one: library size and median times-cooked. The threshold of 15 is not arbitrary — §5.7 itself asserts that households rotate through fifteen dishes.
**Cost of being wrong is low:** the pivot changes tab order and the primary action; it does not touch the data model.

### G-3 · Auditability as a wedge

**Hypothesis.** If every aggregate number can be opened to show its parts, the optimiser stops re-checking by hand — and this is the one position nobody in the category has taken.
**Follows from:** section **1** (MP-3: trust is signalled socially, never proven numerically) + section **2** (M-2: three of five best-in-niche products score R5 ≤ 3; the products that find best explain least).
**Test.** Not tested, and **not testable by desk research**: the conclusion is drawn from *absence* in marketing, not from observing anyone. It needs people on a real shop.
**Status:** that a tool you verify by hand has negative ROI is logic, not data. **Unverified.**

### G-4 · The three units

**Hypothesis.** Strict `g`/`ml`/`pcs` removes an entire class of silent error from scaling, merging and calories — and that benefit exceeds the cost, which lands on the parser (conversions, densities, unit weights).
**Follows from:** section **1** (D-3: everyone converts, nobody constrains — the rule is unique across the fifteen and validated by none of them).
**Test.** The same bake-off as G-1, with one added counter: **what share of rows across 10 recipes require a density or unit weight to be entered by hand.** That measures the cost of §5.1 and the coverage of §10 in a single pass.

### G-5 · Where the canonical ingredient data comes from

**Hypothesis.** A few hundred curated ingredients will cover most home cooking; the remainder falls to the review screen, where the user supplies the number once. An open nutrition dataset gives kcal but **not density, average unit weight or aisle category** — three of the four attributes needed.
**Follows from:** section **2** (M-1 and M-2 both resolve through §5.5) + section **1** (Tandoor, the only ingredient-first product, builds on Open Food Facts).
**Test.** On the same 10 recipes, count the share of rows that resolve automatically. The fallback is fixed regardless of source: an unmatched ingredient **never blocks saving a recipe**.
*Source for the constraint:* [tandoor.dev](https://tandoor.dev/) · [`competitive-landscape.md` §Tandoor](./competitive-landscape.md)

### G-6 · Aisle order for a European supermarket

**Hypothesis.** One fixed walking order is good enough for a home cook — but since reordering is rejected (§8), it is **the only order the user will ever get**, so it had better be right for the shops they actually walk.
**Follows from:** section **1** (tier 1: Paprika, Plan to Eat and AnyList all ship reordering — it is the category default, not one product's quirk).
**Test.** Walk a real European supermarket with the current §5.5 order and count the backtracks. The research is **entirely US-centric**; aisle taxonomies are unvalidated against a European store.
**Status:** the cheapest thing on this list to reverse if a real shop proves it wrong.

### G-7 · The pantry as a graveyard feature

**Hypothesis.** The two-tier pantry (staples without quantities + opt-in tracking) survives drift precisely because neither tier is mandatory: skip it entirely and Cooksy behaves as if the pantry were empty.
**Follows from:** section **2** (the rejected mechanism: retrieval must not depend on inventory state) + section **1** (Paprika's pantry is the years-proven shape of §5.8).
**Test.** **Nobody has watched how pantry implementations actually die.** It needs a month of real upkeep — our own, or a Paprika teardown. Named the cheapest available upgrade to the evidence base.
**Status:** unverified.

### G-8 · Whether frecency is the right default order

**Hypothesis.** Frequency × recency of **cooking** (not saving) surfaces the fifteen dishes a household actually rotates through — and substitutes for saved searches at a library of sixty.
**Follows from:** section **2** (M-3, from Raycast; and the deliberate refusal of Todoist's filter language).
**Test.** Impossible until a library has been cooked from for a month. Whether this is the right default order or merely the cheapest is open. The risk is pre-empted: the order is **resettable**, so the learning never becomes a trap.

---

## 5. Unverified

Everything in this synthesis with no source, or only a weak one. None of it is invented.

**On competitors:**
1. **Fond** — offline, export and permissions are not stated anywhere on the site; the product reads as pre-launch (waitlist, "Coming soon"). The *owner / editor / viewer* roles model from an early draft has been **withdrawn as unverified**, and §5.10 no longer rests on it.
2. **Samsung Food** — $59.99/yr is carried over from prior desk research and **not re-verified**: the site returns 403 to server-side fetchers.
3. **Plan to Eat** — offline, export and privacy are absent from the site.
4. **AnyList** — offline, export and privacy are not addressed on the site.
5. **Prices are not rendered publicly** by Fond, NYT Cooking, Things or Todoist — those cells say so rather than guess.
6. **Tandoor** — trigram search (`chkn` → chicken) is confirmed by a **secondary source only**; the official search documentation page returns 404.
7. **Apple Notes as the most common place recipes are stored** — plausible, but it is our own assumption with no data behind it.
8. **Four screenshots sit behind logins** and are watermarked ACCESS RESTRICTED rather than faked: [Tandoor app](./screens/t1-tandoor-app-restricted.png) · [Apple Notes](./screens/t2-apple-notes-restricted.png) · [Google Keep](./screens/t2-google-keep-restricted.png) · [NYT Recipe Box](./screens/t3-nyt-recipe-box-restricted.png). Instagram's personal saves collection is unreachable without an account; the public `#recipe` tag page was captured instead, which is where the 114M figure comes from.

**On method generally:**
9. **This is not observed user pain.** The entire picture is inferred from vendor marketing, App Store copy, and what fifteen products chose to build or omit. **No teardowns, no interviews.** Absence in marketing is real signal, and convergence across three independent tiers is worth something, but it is an assertion, not a measurement.
10. **The benchmark scores** are an assessment of a *specification* against documentation, not a measurement of a working product. 23/40 and the projected 30/40 carry that same status.
11. **Parser quality** is an assertion. The bake-off has not been run, even though mandatory review was reaffirmed on reasoning alone.
12. **Aisle order** is unvalidated against a European supermarket.
13. **The P1–P5 pattern classification** is this research's own analytical frame; it has no external source.

---

## What to do next

One item closes three gaps at once. The **parser bake-off** (10 real URLs × 3 products) measures G-1 (capture speed), G-4 (the cost of three units) and G-5 (ingredient database coverage) in a single pass — and it targets exactly the surface section 3 independently identifies as MVP's riskiest.

Second by payoff: **two metrics from week one** for G-2 — library size and median times-cooked. They cost the sort key M-3 already requires, and they answer whether the product's primary object was chosen correctly.

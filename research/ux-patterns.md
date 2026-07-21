# Patterns — storing and retrieving a recipe

**Date:** 21 July 2026
**Dimension:** **organising principle** — what the interface treats as its primary object, and where structure comes from.
**Not** a feature comparison (that is [`comparison.md`](./comparison.md)) and **not** a retrieval score (that is [`benchmark-retrieval.md`](./benchmark-retrieval.md)). This document asks the question one level up: *of the fundamentally different ways to build a thing that stores recipes and hands you an ingredient list, which one is Cooksy?*

**Why now.** The brief has locked the stack (§3), the units (§5.1), the review step (§4) and the build order (§11) without ever naming the pattern those decisions add up to. Naming it is worth one document, because the name is what tells you which failure mode you have signed up for — and every pattern has exactly one.

**Method:** five archetypes, each with the same four-part anatomy so they are comparable rather than five essays that happen to sit together. Judged against `CLAUDE.md` only. No hands-on teardown of the named products — same standing caveat as the rest of `research/`.

---

## 1. The field

Five patterns, differing on two axes: **what the primary object is**, and **where structure lives**. Pattern keys `P1`–`P5` are local to this document — `§` refs point at `CLAUDE.md`.

| Key | Pattern | Primary object | Where structure lives | Verdict |
|---|---|---|---|---|
| **P1** | **Typed record** | the record | at capture, enforced by the app | **Adopted** |
| **P2** | **Document** | the note | nowhere — the human holds it | **Rejected** |
| **P3** | **Index** | the query | deferred to query time | **Absorbed** |
| **P4** | **Output-first** | the list | in the artifact being produced | **Reserve** |
| **P5** | **Conversational** | the utterance | in a model, on demand | **Split** |

**Set aside, not counted:** the board or canvas (Trello, Miro, fridge magnets). Cooksy already uses it exactly where it belongs — the week grid (§5.7) *is* a board — and as a *library* pattern it is browse with worse density plus the precision gestures §7.4 forbids.

---

## 2. P1 — The typed record

*Schema-first library.*

**How it works.** The unit is a record with named fields of known type: qty (number), unit (enum), item (foreign key), note, flags. Capture is a funnel that ends in a form — raw input → parse → confirm → commit. Everything the user sees afterwards is a **projection** over those rows: the recipe card, the scaled list, the merged shop, the calorie figure. The ingredient list is computed, never authored.

**Where it's used.** Paprika, Grocy, Airtable and Notion databases, Jira, MyFitnessPal's food log, every accounting application ever built.

**Works when** the value lives *downstream* of capture — the app must sum, scale, dedupe, convert, group or audit. When a capture error is expensive but checkable, so a confirm step earns its keep. When several features consume the same atom, so the schema is paid for once and cashed many times.

**Breaks when** capture is the bottleneck. The bill comes due at the worst moment: the user is enthusiastic, has a URL, and now has a form. Field-hunting is where libraries die at eleven recipes. It also breaks against reality's long tail — no schema has a cell for *a splash*, so every such row is a lie or a special case. And a wrong schema chosen early is not a migration, it is re-entering sixty recipes.

---

## 3. P2 — The document

*The notebook.*

**How it works.** A recipe is a blob. Whatever structure exists is typographic — a blank line, a dash, a bold heading — legible to a human and to nothing else. Organisation is hand-applied folders and tags; retrieval is full-text plus recognition. "Getting a shopping list" means reading the top half and writing things down.

**Where it's used.** Apple Notes — plausibly where more recipes live than in every dedicated app combined ⚠︎ — plus Obsidian, Google Docs, a WhatsApp thread with yourself, a shoebox of index cards.

**Works when** capture cost must be near zero and input is wildly heterogeneous: a photo, a paragraph, three words and a link. When the only consumer is a human who already knows what they meant, and the corpus is small enough that recognition beats retrieval. It never blocks, never mis-parses, never has an opinion. That is why it wins by default.

**Breaks when** a machine has to do arithmetic on it. Doubling is your problem; merging two recipes' onions is your problem. It degrades silently as it grows — two hundred inconsistently formatted notes are unqueryable except by full-text — and it produces no history you can compute over.

---

## 4. P3 — The index

*Search-first, no filing.*

**How it works.** Capture is a dump, there is no hierarchy to maintain, and the index **is** the organisation. All navigation collapses into one query box. Investment moves from the user's filing discipline to the retrieval layer: synonyms, stemming, fuzzy matching, ranking, sometimes operators.

**Where it's used.** Gmail and Superhuman, Spotlight, Apple Photos, Todoist's filter language, SuperCook across eleven million recipes.

**Works when** the corpus genuinely outgrew browsing, the user can name what they want, and the index has enough semantic depth that queries survive synonyms. It is the correct answer to a collection that outgrew its own taxonomy.

**Breaks when** N is small. At sixty items, looking is faster than typing, and an empty search box is a worse home screen than a list of sixty things. It breaks when the user cannot name it — *that aubergine thing, from autumn*. And the best modern indexes break on **explanation**: Apple Photos finds the picture and cannot say why it matched. Fine for photos, fatal for anything you must verify — the vacancy [`comparison.md`](./comparison.md#common-market-patterns) records as pattern 5.

---

## 5. P4 — The output-first artifact

*The list is the app.*

**How it works.** Invert ownership. The primary daily object is the **output** — this week's list, this week's plan — and recipes are inputs consumed on the way to it. You open the app in the shop, not at your desk. Capture is just-in-time and disposable; the archive, if any, is a by-product. The interface optimises the moment of use, not the moment of authorship.

**Where it's used.** Bring!, AnyList, Out of Milk, Instacart, Mealime, a whiteboard on the fridge.

**Works when** the artifact has a short half-life and high frequency — you shop weekly and last month's list is worthless. When the population that *opens* the app is larger than the population that authors content (the housemate who only ever ticks things off). When it must survive one thumb and no attention. And it has almost no cold-start problem: an empty list is usable, an empty library is a chore.

**Breaks when** you want memory. Recipes buried in past lists are unfindable, so re-use — the thing that makes cooking cheap — is redone by hand every week. Scaling has nowhere to live, because a recipe was never a first-class object with a base serving count. And it can never answer *what can I make with the aubergine*, having never modelled what a recipe **is**.

---

## 6. P5 — The conversational agent

*Say it, it sorts it out.*

**How it works.** The interface is language. You paste, dictate or describe; a model does the structuring, storing and retrieving; the answer returns as prose. No schema the user can see, no filing, often no screen worth speaking of. Structure exists — it is the model's, produced on demand.

**Where it's used.** ChatGPT as a de facto recipe box, Alexa and Siri lists, SMS and WhatsApp bots, and increasingly every note app's *ask* tab.

**Works when** capture is the binding constraint and input is unpredictable — it absorbs anything, including what no schema anticipated. When queries are fuzzy or compositional. And it is unbeatable on vocabulary: it knows *velveted* is a frying concept without anyone enumerating it, which is exactly the problem §10 hands it.

**Breaks** three ways, and they compound. It cannot state its evidence — you get an answer, not a derivation. It costs per use, and the cost scales with how much the product is used, which is the wrong direction. And it needs a network at exactly the two moments — kitchen, shop — that do not have one. Nothing gets faster with practice either: there is no spatial memory, so the thousandth retrieval costs what the first did.

---

## 7. Verdict — P1, the typed record

**With mandatory review as the load-bearing part.** Three reasons.

**1. Everything Cooksy sells is a projection, and projections need types.** §5.3's weight model, §5.4's live rescale, §5.6's kcal/100 g, §5.9's merge — these are not features you build, they are arithmetic that either has typed rows underneath it or does not exist. §5.1 is the same decision seen from the other side: a product that has **banned tablespoons** to guarantee a type has already committed to this pattern. The rest is consequence.

**2. §5.5's canonical ingredient is a join key, and this is the only pattern with joins.** Four features resolve through one record. In P2, `onion` is a string and merge, calories, pantry and ingredient search become four separate heuristics that each fail differently on `2 large yellow onions`. The brief's own *"every hour spent here pays out four times"* is a description of a normalised schema — the 4× exists **because** there is one table to join against.

**3. §7.2 and §7.3 require derivability, which requires stored provenance.** *Merged numbers are always auditable* and *silent wrongness is the only unrecoverable failure* are unreachable in P3 and P5, both of which return results they cannot explain — §10 ruled the model out at query time on precisely this ground. A grocery line that opens to show which recipes contributed what is a foreign key. This is also the only pattern where §5.12 is free: records on device plus arithmetic is a local read, no spinner, no radio.

**The failure mode is priced in, not overlooked.** P1's known weakness is capture cost, and the brief spends its risk budget there deliberately: mandatory review (§4, §5.2) is choosing to pay the schema's bill on every path in exchange for a downstream that never lies. The mitigation is already correct — *make correcting a row faster than typing it from scratch*.

---

## 8. Second — P4, under condition X

> **X = the library never reaches critical mass.** Capture cost exceeds re-use value, the archive stalls at eleven recipes, and what actually gets opened weekly is the plan and the list.

**This is the live risk, not a hypothetical.** Four of §9's five success criteria are about the *list*, not the library — a planned week taken to a shop, one pass through the store, nothing bought that was already in the cupboard, nothing missed because the app assumed. Only one is about capture. And §5.2 concedes the fast path is deferred on iOS, so MVP capture is paste: *"paste is not a fallback in MVP, it is the main road."* The library-first bet is that people type in sixty recipes over the slow input. If they do not, the home screen is an empty shelf.

**The tell that this is the genuine second: the pivot needs no rewrite.**

- Tab order changes — list first, library third (§6)
- §5.9's already-specified ad-hoc generation becomes the main road instead of the planner
- §5.9's manual lines carry the recipes that were never captured
- **The data model does not move**

**Trigger to watch.** §5.7 observes that households rotate through fifteen dishes. If after four weeks the library holds fewer than fifteen and the median recipe has been cooked once, the archive is not earning its capture cost.

**Under a different condition** — the library grows past a few hundred — the second would be **P3**. But §5.13 has already annexed its useful half: two-tier results with stated evidence, frecency default order, no query syntax (§8). It is not a separate destination, it is a layer Cooksy already wears.

---

## 9. Does not fit — P2, the document

It is the incumbent, and naming why it loses is the same as naming why Cooksy exists. It wins on the one axis Cooksy cannot beat it on — capture — and loses everything downstream at once:

- **§1's loop is four operations on structure.** A blob supports none of them. Notes can *hold* a recipe; it cannot rescale one.
- **§5.5's join is impossible**, so merge, calories, pantry and ingredient search fail together. The 4× payout inverts into a 4× failure.
- **§5.13's *"every row states its evidence"* is unmeetable.** Full-text can say a document contains `aubergine`, never that the recipe needs 400 g of it in the sauce group — and the amount is the answer.
- **Its failure mode is the one §7.3 calls unrecoverable.** A stale note does not announce itself; it is just quietly wrong.

> **The document is the fastest way to store a recipe and the slowest way to use one.**

§2's optimisers already own the notes app. What they resent is precisely the residue it leaves — the retyping, the portion maths in the head, the three laps of the supermarket. Shipping P2 with a nicer skin ships them their current problem.

---

## 10. One clarification, so it is not misread later

**P5 is half-adopted, not rejected.** §10 permits a model at authoring and import time and rules it out at query time. It may write the data; it never stands between a keystroke and a result.

---

## 11. What this changes in the brief

**Nothing.** That is the finding. Every decision already locked in `CLAUDE.md` is consistent with P1, and the two patterns with a claim on the product (P3, P5) are already scoped into it at exactly the depth they can be trusted at. The value of this document is the **name** and the **trigger**:

- The pattern is **P1, typed record**, and its one failure mode is **capture cost** — which is why §5.2's paste box and §5.2's review screen are the two highest-risk surfaces in MVP, not the planner or the pantry.
- **Condition X is measurable and worth measuring** from week one: library size and median times-cooked. It is the only reading that would justify reordering §6's tabs, and it costs nothing to watch.

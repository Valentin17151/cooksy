# Personas

**Date:** 25 July 2026
**Basis:** the people-observations extracted from [`competitive-landscape.md`](./competitive-landscape.md), [`comparison.md`](./comparison.md), [`ux-patterns.md`](./ux-patterns.md), [`benchmark-retrieval.md`](./benchmark-retrieval.md) and [`summary.md`](./summary.md). Every block cites its source or screen.

**Method caveat, load-bearing.** The corpus states of itself: *"no hands-on teardown, no user interviews"* ([`competitive-landscape.md` §How good is this evidence](./competitive-landscape.md#how-good-is-this-evidence), [`summary.md` §5.9](./summary.md#5-unverified)). These personas are reconstructed from vendor-declared audiences and from what fifteen products chose to build or omit. **Each persona is a falsifiable hypothesis about a user, not a measured segment.** Where data is absent the block says **[?]** and is phrased as a hypothesis.

**On the voice quotes.** The research contains **no real user reviews and no forum material** — only vendor copy, App Store listings and the research's own synthesis. Every *Voice* line below is therefore **[?]**, substituted with the closest **verbatim line that actually exists in the corpus**, labelled for what it is. None of them is a user speaking, and none should ever be quoted as one.

**Evidence classes**, carried over from the observation pass: *(vendor copy)* — a product's own site or listing · *(screen)* — captured screenshot in [`screens/`](./screens/) · *(correlation)* — desk-research pattern across products · *(assertion)* — the research's or brief's own claim with no external source.

---

## The set

| # | Persona | Status | Anchored in |
|---|---|---|---|
| **P-1** | **The Systematic Optimiser** | **Primary** | Paprika's declared audience, pains 1 · 4 · 6 · 7, the §9 success criteria |
| **P-2** | The Household Logistics Lead | Secondary | Plan to Eat / AnyList audiences, market pattern 3, pains 2 · 3 |
| **P-3** | The Reel Hoarder | Secondary — the risk persona | Instagram/TikTok tier, the meta-pain, Condition X |
| **P-4** | The Data Sovereign | Secondary — the edge | Tandoor's audience, pain 5, pain 7 |

**Why P-1 is primary — three reasons, all sourced.**

1. **The product loop is theirs.** Four of §9's five success criteria (a real shop, trusted scaling, one pass through the store, nothing bought twice) are P-1's jobs almost verbatim, and every wedge the research found — auditability as an unoccupied position ([MP-3](./summary.md#12-three-common-market-patterns)), the unique three-unit rule ([D-3](./summary.md#13-three-differences)), the ingredient-first centre ([D-2](./summary.md#13-three-differences)) — attacks a P-1 pain specifically.
2. **The category default already targets them**, which is the strongest external evidence any of these personas has: Paprika's audience is *"multi-device home cooks who shop systematically"* *(vendor copy)* — [`comparison.md` tier 1](./comparison.md#tier-1--hard), [screen](./screens/t1-paprika.png).
3. **Each of the other three hits a structural block in MVP.** P-2 waits on household sharing, deliberately build step 8 of 8 (§11 of the brief). P-3's entry path — the share sheet — is deferred post-MVP (§5.2/§8.1). P-4 collides with day-one cloud accounts and deferred export. Only P-1 is fully served by MVP as scoped.

---

## P-1 · The Systematic Optimiser — PRIMARY

### Context

Cooks regularly and **already knows what they want to cook** — needs a home recipe book that makes the logistics disappear: scaling, merging, one list, no re-typing. The category describes this person only behaviourally: *"multi-device home cooks who shop systematically. No demographic claimed; the UI selects for tolerance"* *(vendor copy)* — [`comparison.md` tier 1](./comparison.md#tier-1--hard) · [screen](./screens/t1-paprika.png).

- Where their recipes live today: **[?]** — hypothesis: a notes app plus browser bookmarks, per the research's own flagged assumption that Apple Notes is *"plausibly where more recipes live than in every dedicated app combined"* *(assertion, listed as unverified)* — [`summary.md` §5.7](./summary.md#5-unverified), [`ux-patterns.md` §3](./ux-patterns.md).
- Demographics (age, country, income): **[?]** — nothing in the corpus.
- **Not a diet persona.** They want to know what a dish *is*, not track goals — "health-goal seekers" are Samsung Food's declared audience and explicitly out of Cooksy's scope *(vendor copy)* — [`comparison.md` tier 1](./comparison.md#tier-1--hard), §5.6/§8 of the brief.

### Jobs

- Get a recipe into the system **faster than retyping it** — the bar is set by pasting into a note ([`competitive-landscape.md` tier 2](./competitive-landscape.md#tier-2--soft))
- Rescale portions **without doing arithmetic** (§5.4 of the brief; Crouton's inline scaling is the category's aspirational bar — [`comparison.md` tier 3](./comparison.md#tier-3--aspirational), [screen](./screens/t3-crouton.png))
- Walk the store **once**, off one merged, aisle-ordered list (§9 of the brief)
- Query their own library by what's in the fridge — the *"what can I make with the aubergine"* job, pain #1 in the corpus ([`competitive-landscape.md` pain 1](./competitive-landscape.md#seven-structural-pains), [`benchmark-retrieval.md`](./benchmark-retrieval.md))
- **Verify any merged number** before trusting it ([`competitive-landscape.md` pain 4](./competitive-landscape.md#seven-structural-pains))
- Confirm the data can leave **before** typing sixty recipes in ([`competitive-landscape.md` pain 5](./competitive-landscape.md#seven-structural-pains))

### Pains (ranked)

1. **Retrieval from their own hoard.** *"Storage is solved everywhere; usable storage nowhere."* *(correlation)* — [`competitive-landscape.md` pain 1](./competitive-landscape.md#seven-structural-pains)
2. **Numbers nobody shows the parts of** — so they re-check merged quantities by hand. *(assertion — the corpus itself grades this "logic, not data")* — [`competitive-landscape.md` pain 4](./competitive-landscape.md#seven-structural-pains), [`summary.md` G-3](./summary.md#g-3--auditability-as-a-wedge)
3. **Quantity chaos.** A cup of flour vs a cup of sugar differ by ~80 g and all fifteen products preserve the ambiguity. *(correlation)* — [`competitive-landscape.md` pain 6](./competitive-landscape.md#seven-structural-pains), [`comparison.md` D-5](./comparison.md#key-differences)
4. **The notes-app residue**: retyping, portion maths in the head, three laps of the supermarket. *(assertion — the brief's persona restated in research, no data)* — [`ux-patterns.md` §9](./ux-patterns.md)
5. **The forced trade**: *"a good model behind Docker, or a good app that fudges the maths."* *(correlation)* — [`competitive-landscape.md` pain 7](./competitive-landscape.md#seven-structural-pains)

### Trust triggers

| Convinces | Repels |
|---|---|
| Local data, explicit offline, one-time purchase — the Paprika precedent users demonstrably tolerate an ageing UI for *(vendor copy + assertion)* — [`competitive-landscape.md` Paprika](./competitive-landscape.md#paprika-recipe-manager-3) | Subscriptions — the one-time column of the market exists and holds *(correlation)* — [`comparison.md` D-1](./comparison.md#key-differences) |
| An export path before commitment — the two strongest data stories (Mela, Tandoor) correlate with the most evangelical users *(correlation; "evangelical" itself unmeasured)* — [`competitive-landscape.md` pain 5](./competitive-landscape.md#seven-structural-pains), [screen](./screens/t3-mela.png) | AI/content bloat — Samsung Food's drift toward feeds and Health Scores is named as the opposite of this audience *(correlation)* — [`competitive-landscape.md` Samsung Food](./competitive-landscape.md#samsung-food-formerly-whisk) |
| Numbers that open to show their parts — an unoccupied position in the entire category *(correlation)* — [`summary.md` MP-3](./summary.md#12-three-common-market-patterns) | **[?]** hypothesis: one visibly wrong number ends the relationship — *"an optimiser will abandon the product the moment the maths is wrong"* is the brief's claim (§2), unmeasured |

### Voice

**[?] — no user quote exists anywhere in the corpus.** Closest verbatim line, labelled: *"an optimiser re-checks the merged quantity by hand — and a tool you verify by hand has negative ROI"* — **the research's own synthesis, not a user speaking** ([`competitive-landscape.md` pain 4](./competitive-landscape.md#seven-structural-pains)).

### Open questions for this persona

- Does the segment exist at any measurable size? **[?]** — it is the brief's construct; the research never sizes it.
- Will they tolerate mandatory review? **[?]** — G-1, bake-off not run ([`summary.md` G-1](./summary.md#g-1--capture-speed)).
- Will they build a sixty-recipe library over paste alone? **[?]** — G-2 / Condition X ([`summary.md` G-2](./summary.md#g-2--condition-x-whether-the-library-reaches-critical-mass-at-all)).

---

## P-2 · The Household Logistics Lead — secondary

### Context

Runs the food logistics for a shared household — the plan, the shop, the split. The market's words for them: *"organised households, busy families… if you love meal planning and staying organized"* *(vendor copy)* — [`comparison.md` tier 1](./comparison.md#tier-1--hard), [screen](./screens/t1-plan-to-eat.png); *"households coordinating a shop"*, later *"households mid-shop, in two different aisles"* *(vendor copy)* — [`comparison.md` tiers 2–3](./comparison.md#tier-2--soft), [screen](./screens/t2-anylist.png). Household size 2–4 is **the brief's assumption (§5.10), not research data — [?]**. The household contains a second member type who never authors anything and only ticks items off *(assertion)* — [`ux-patterns.md` §5](./ux-patterns.md). Needs the app as one shared source of truth, replacing a shared Keep list that *"has no quantities, no ingredients, no semantics"* *(correlation)* — [`comparison.md` tier 2](./comparison.md#tier-2--soft).

### Jobs

- Keep **one shared plan and one live list** the whole household sees ([`comparison.md` pattern 3](./comparison.md#common-market-patterns))
- Split a shop in real time — two people, two aisles, basement signal ([`competitive-landscape.md` pain 2](./competitive-landscape.md#seven-structural-pains), [AnyList as sync benchmark](./competitive-landscape.md#anylist-second-appearance))
- Get portions × people right when different people eat different meals — **[?]** hypothesis: the member-assignment mechanic is the brief's design (§5.7), no researched demand behind it
- Hand the list to the household member who won't install anything — Keep/Reminders are named as the export target ([`competitive-landscape.md` tier 2](./competitive-landscape.md#tier-2--soft))

### Pains (ranked)

1. **The honest one first: the pain may not be felt.** *"A household with a working shared Keep list has no felt problem for Cooksy to solve."* *(assertion)* — [`competitive-landscape.md` tier 2](./competitive-landscape.md#tier-2--soft)
2. **The category default offers them nothing** — Paprika has no household sharing at all; its absence is now a defect *(vendor copy + correlation)* — [`competitive-landscape.md` Paprika](./competitive-landscape.md#paprika-recipe-manager-3), [`comparison.md` pattern 3](./comparison.md#common-market-patterns)
3. **A half-finished shop gets destroyed** when next week is planned — Paprika's one-list-at-a-time, *"a known complaint"* (whose complaint is unsourced) — [`competitive-landscape.md` pain 3](./competitive-landscape.md#seven-structural-pains)
4. **Lost or laggy checkoffs mid-shop** — the bar is AnyList, which *"has simply never lost a checkoff"* *(assertion)* — [`comparison.md` tier 3](./comparison.md#tier-3--aspirational)

### Trust triggers

| Convinces | Repels |
|---|---|
| Sync so fast it reads as local *(assertion, AnyList benchmark)* — [`comparison.md` tier 3](./comparison.md#tier-3--aspirational) | **[?]** hypothesis: roles/permissions ceremony — "households run on trust that already exists offline" is the brief's own reasoning (§5.10), reaffirmed without competitor evidence ([`competitive-landscape.md` Fond](./competitive-landscape.md#fond)) |
| Household priced at almost nothing — AnyList charges +$5/yr for a whole household *(vendor copy)* — [screen](./screens/t3-anylist-complete-pricing.png), [`comparison.md` pattern 3](./comparison.md#common-market-patterns) | **[?]** hypothesis: per-seat pricing would read as a tax on the family |
| Joining with zero ceremony — Crouton ships household via Family Sharing *(vendor copy)* — [`comparison.md` tier 3](./comparison.md#tier-3--aspirational) | Any household UI leaking into solo use — §5.10's rule, untested against users **[?]** |

### Voice

**[?] — no user quote exists in the corpus.** Closest verbatim line, labelled: *"Any changes made to a shared list will show up instantly to everyone sharing the list"* — **AnyList's vendor copy**, i.e. the promise this persona is being sold, not their own words ([`comparison.md` tier 2](./comparison.md#tier-2--soft)).

### Why secondary

Household sharing is deliberately the **last** build step (§11.8 of the brief), and the market evidence says this persona's core job is already the best-served one in the category — AnyList exists, works, and is the product *"households actually run their shop from"* ([`summary.md` MP-2](./summary.md#12-three-common-market-patterns)). The wedge for P-2 is thinner than for P-1.

---

## P-3 · The Reel Hoarder — secondary, the risk persona

### Context

Finds recipes where recipes are found in 2026 — Instagram and TikTok — and saves them in one tap: 114M reels under `#recipe` alone *(screen)* — [`comparison.md` tier 2](./comparison.md#tier-2--soft), [screen](./screens/t2-instagram-recipe-tag.png). Age *"under ~45"* is **the research's own unsourced estimate — [?]**. The overflow lands in screenshots and notes, where *"most 'I'll organise it later' recipes die"* *(assertion)* — [`competitive-landscape.md` tier 2](./competitive-landscape.md#tier-2--soft). Needs the app because **saving is solved and everything after saving is broken**.

### Jobs

- Capture in **one gesture without leaving the video or page** — the share-sheet job, which MVP explicitly defers (§5.2/§8.1 of the brief; [`comparison.md` question 6](./comparison.md#questions-for-pm--answered-21-july-2026))
- Actually **find** a saved recipe weeks later ([`competitive-landscape.md` meta-pain](./competitive-landscape.md#the-meta-pain-saving-is-not-cooking))
- Turn a saved blob into something cookable — portions, a list
- **Own** the save — platform content can vanish, exports nothing, saves are login-gated *(correlation)* — [`comparison.md` tier 2](./comparison.md#tier-2--soft)

### Pains (ranked)

1. *"Capture is effortless; **retrieval is hopeless**."* *(correlation)* — [`comparison.md` tier 2](./comparison.md#tier-2--soft)
2. A save is **a bookmark on content you don't own** — no search, no export, no quantities *(correlation)* — [`comparison.md` tier 2](./comparison.md#tier-2--soft)
3. Video carries no pasteable text — and video import is rejected for MVP, so Cooksy's answer to their #1 source is "screenshot and retype" ([`competitive-landscape.md` tier 2](./competitive-landscape.md#tier-2--soft), §8 of the brief)
4. Forms kill them fastest: *"field-hunting is where libraries die at eleven recipes"* *(assertion)* — [`ux-patterns.md` §2](./ux-patterns.md)

### Trust triggers

| Convinces | Repels |
|---|---|
| Zero setup, nothing to configure, nothing to correct — the Notes bar *(correlation)* — [`comparison.md` tier 2](./comparison.md#tier-2--soft) | Anything that reads as a form — see pain 4 *(assertion)* |
| Capture speed above all — the whole market leads with it *(correlation)* — [`comparison.md` pattern 1](./comparison.md#common-market-patterns) | **[?]** hypothesis: the mandatory review screen itself — no competitor ships a forced correction step, and whether this persona walks at the sight of one is exactly what the unrun bake-off (G-1) would measure |

### Voice

**[?] — no user quote exists in the corpus.** Closest verbatim line, labelled: *"capture is effortless; retrieval is hopeless"* — **the research's own synthesis** of the tier, not a user ([`comparison.md` tier 2](./comparison.md#tier-2--soft)).

### Why secondary — and why "risk persona"

MVP is weakest exactly at their front door: share-sheet deferred, video rejected, *"the paste box carries the whole load"* ([`competitive-landscape.md` tier 2](./competitive-landscape.md#tier-2--soft)). Whether a hoarder ever converts into a library-builder is **Condition X** — the named live risk with defined metrics and no data ([`ux-patterns.md` §8](./ux-patterns.md), [`summary.md` G-2](./summary.md#g-2--condition-x-whether-the-library-reaches-critical-mass-at-all)). And chasing them first would turn Cooksy into a capture product — the position the entire market already occupies ([`comparison.md` pattern 1](./comparison.md#common-market-patterns)).

---

## P-4 · The Data Sovereign — secondary, the edge

### Context

Technical, with a large collection: *"cooking enthusiasts with huge collections" — self-hosters* *(vendor copy)* — [`comparison.md` tier 1](./comparison.md#tier-1--hard), [screen](./screens/t1-tandoor.png). Today they either run Tandoor behind Docker or refuse the category entirely, because the only ingredient-first product is *"comfortably the least approachable of the fifteen"* *(correlation)* — [`competitive-landscape.md` pain 7](./competitive-landscape.md#seven-structural-pains). Needs the app if it offers Tandoor's model honesty **without the sysadmin tax**.

### Jobs

- **Own and export everything**; GDPR-grade privacy — the Tandoor trust bar: OSS, self-host, no tracking, 90-day export *(vendor copy)* — [`comparison.md` tier 1](./comparison.md#tier-1--hard)
- Get **ingredient-level correctness** — a real food database, editable conversions ([`competitive-landscape.md` Tandoor](./competitive-landscape.md#tandoor-recipes))
- Pay once, or not at all *(correlation)* — [`comparison.md` D-1](./comparison.md#key-differences)

### Pains (ranked)

1. The correct model ships inside the worst interface, and the setup cost keeps it technical *(correlation)* — [`competitive-landscape.md` pain 7 + Tandoor entry](./competitive-landscape.md#seven-structural-pains)
2. Cloud competitors won't state offline, export or privacy anywhere on their sites — Fond, Plan to Eat, AnyList all silent *(correlation)* — [`summary.md` §5.1–5.4](./summary.md#5-unverified)

### Trust triggers

| Convinces | Repels |
|---|---|
| *"GDPR Compliant — Made in Germany"*, self-host, 90-day export *(vendor copy)* — [`comparison.md` tier 1](./comparison.md#tier-1--hard) | **A mandatory cloud account** — which Cooksy requires from day one (§4 of the brief). Honest collision, unresolved. **[?]** hypothesis: this alone disqualifies Cooksy for the strict end of this persona |
| *"Mela does not collect any data… does not depend on or use any third-party service"* *(vendor copy)* — [`comparison.md` tier 3](./comparison.md#tier-3--aspirational), [screen](./screens/t3-mela.png) | Export deferred to post-MVP (§8.1) — the corpus itself calls pain 5 *"knowingly left on the table"* ([`competitive-landscape.md`](./competitive-landscape.md#the-uncomfortable-part)) |
| The strongest data stories correlate with the most evangelical users *(correlation)* — [`competitive-landscape.md` pain 5](./competitive-landscape.md#seven-structural-pains) | Subscription of any kind *(correlation)* — [`comparison.md` D-1](./comparison.md#key-differences) |

### Voice

**[?] — no user quote exists in the corpus.** Closest verbatim line, labelled: *"GDPR Compliant — Made in Germany"* — **Tandoor's vendor copy**, the promise this persona organises around, not their own words ([`comparison.md` tier 1](./comparison.md#tier-1--hard)).

### Why secondary

Segment size is **[?]** and plausibly the smallest of the four, and two locked MVP decisions — day-one cloud accounts (§4) and deferred export (§8.1) — point directly away from them. Serving them first would mean reopening locked decisions; serving them *eventually* is cheap, because full export is already a recorded post-MVP obligation.

---

## Anti-personas — deliberately not served

One line each, because the boundary is as load-bearing as the personas:

- **The health-goal tracker** — Samsung Food's declared audience segment; macros, goals and diet tracking are rejected in §5.6/§8 of the brief *(vendor copy)* — [`comparison.md` tier 1](./comparison.md#tier-1--hard)
- **The discovery-seeker** — Cookpad/Pinterest's audience; browsing for inspiration, social proof as ranking; the feed is rejected in §8 *(vendor copy + screen)* — [`comparison.md` tier 2](./comparison.md#tier-2--soft), [screen](./screens/t2-cookpad.png)

---

## Validation — what would make these personas real

In priority order, matching the corpus's own next steps ([`summary.md` §What to do next](./summary.md#what-to-do-next)):

1. **The parser bake-off** (G-1) tests P-1's and P-3's tolerance for mandatory review — the single riskiest assumption shared by the primary and the risk persona.
2. **The two week-one metrics** (G-2: library size, median times-cooked) decide between P-1 and P-3 as the real centre of the product — Condition X made measurable.
3. **A month of real pantry and cooking use** (G-7, G-8) tests P-1's ranked pains against lived behaviour.
4. **Any five user interviews would outweigh everything in this file.** The corpus contains none ([`summary.md` §5.9](./summary.md#5-unverified)).

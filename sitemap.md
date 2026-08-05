# Cooksy — sitemap

**Status:** draft. Three passes, in the order they have to happen: **[entities](#entities) → [screens](#screens) → [navigation](#navigation)**. A screen is a view onto objects, so the objects are agreed first; navigation is an argument about frequency, so the screens exist before it starts. The flows drawn over all of it live in [`flows.md`](./flows.md).

---

## Entities

**Date:** 5 August 2026 · five passes, sixteen decisions, none left open
**Derived from:** [`research/jtbd.md`](./research/jtbd.md) and [`research/personas.md`](./research/personas.md), then cut and extended by product decisions taken the same day.

### Method, and what it deliberately is not

The list was built **from the jobs, not from the feature spec.** [`CLAUDE.md`](./CLAUDE.md) was consulted only for *what fields an object would carry* once a job had already established that the object exists.

**That is the origin, not the authority.** The second pass on 5 August removed four objects the jobs supported and added seven the jobs do not. Where an object is in the model **by decision rather than by job**, it says so. Both facts are worth keeping side by side: the jobs say what the evidence supports, the decisions say what is being built.

**Standing caveat, inherited.** The corpus behind these jobs contains no interviews, no teardowns and no user reviews ([`research/critique.md`](./research/critique.md)). Every job is inferred, so every object resting on one is inferred too.

### How to read this

| Marker | Meaning |
|---|---|
| **[?]** | **The object, or that part of it, is assumed.** Nothing establishes it; it is here because something downstream needs it |
| **J-n · E-n · S-n · H-n** | Job IDs from [`research/jtbd.md`](./research/jtbd.md). **H-n** jobs are hypotheses — evidenced by nothing external |
| **by decision** | In the model because it was chosen, not because a job produces it |
| **retired** | Was in the first pass, removed on 5 August. Kept as a tombstone with its consequences |

---

### The set — twelve objects

| # | Entity | One line | Basis |
|---|---|---|---|
| **E1** | **Recipe** | One dish, in the state its owner actually cooks it | J-6, J-1, J-2, J-3 |
| **E2** | **Ingredient line** | One row of one recipe — an amount of one thing | J-3, J-4, J-2 |
| **E3** | **Canonical ingredient** | "Onion" as a thing in the world, independent of any recipe | J-2, J-3, J-4, E-2 |
| **E4** | **Capture** — *transient* | Pasted text, parsed, in front of you. Never stored | J-1, H-3 |
| **E5** | **Cook list** | A flat list of dishes the person intends to cook | J-0 |
| **E6** | **Cook list entry** | One dish on that list, for a stated number of portions | J-3, J-0 |
| **E7** | **Grocery list** | A dated document of what to buy | J-0, J-4, S-2 |
| **E8** | **List line** | One thing to buy, and the record of where it came from | J-4, J-0, H-1 |
| **E12** | **Account** | The identity that owns everything and carries it between devices | J-6, E-1, E-3 |
| **E13** | **Tag** | A label the person puts on recipes | **by decision** · nearest job J-2 |
| **E14** | **Shared recipe** | A frozen, read-only copy of one recipe, reachable by link | **by decision** · supply side of someone else's J-1 |
| **E15** | **Personal ingredient** | What *you* know about an ingredient the shared data does not | J-3, E-2 |

**Retired on 5 August:** E9 Pantry item · E10 Household · E11 Person. IDs are not reused — see [Retired](#retired--5-august-2026).

---

### E1 · Recipe

One dish, in the state its owner actually cooks it — not the state the blog wrote it in.

**Parts**

- **servings** — **a number the user sets.** An input, never a fixed property inherited from a source; the ingredient amounts on screen are always computed from it
- **title** — named by the person first, because a name is the one field they always have
- ordered **ingredient lines** (E2), optionally under **group headings** — *for the dough*, *for the sauce*. A heading is a label on a row, not a container: it changes display and nothing else
- numbered **steps**, free text. **Formatted by a model at creation, and editable word by word** — see E4
- **source** — free text, and it may be a URL the person pasted as a note. **Nothing fetches it** — see E4
- **photos** — **one or several.** Optional, added at creation before anything is parsed
- **prep + cook time**
- **tags** (E13) — proposed by the model, then added, renamed or removed by the person
- **draft** — **whether anything about this recipe is still unconfirmed.** Not a lifecycle stage and not a lesser kind of recipe: a draft is fully usable, cookable and searchable. It is **shown and highlighted**, on itself and in the Library, until the person has settled it. Three things raise it, and they are three different sentences on screen:

  | Cause | What the person sees |
  |---|---|
  | **Never formatted** — saved offline as text, no ingredient rows | *Not formatted yet. It cannot be shopped for until it is* |
  | **Formatted, but rows are flagged** — saved with its doubts attached | *Some amounts are unconfirmed* |
  | **Formatted while you were away** — the queue caught up and the model ran without you | *This was processed while you were offline. Check it* |

- **finished-dish weight** — optional. Cooking drives off water, so raw weight overstates yield; weighing the pot once makes the estimate honest
- **kcal per 100 g** — derived, scale-invariant, the number worth putting on the card
- **portion size in grams** — **derived**, not entered: yield weight ÷ servings. Servings is the input, so this is its output
- **kcal per portion** — derived from the two above

**Job.** **J-6** primary — *"I want that version kept somewhere that is properly mine, in the state I actually cook it in."* Also **J-1**, **J-2**, **J-3**.

**Relations**

- **has many** Ingredient lines (E2) — they have no life outside it
- **belongs to** one Account (E12). There is no shared library
- **referenced by** Plan slots (E6), many-to-one — cook once, eat twice
- **created from** a Capture (E4), or typed directly, or saved from a Shared recipe (E14), **or copied as a variant** — see below
- **links to** other Recipes — *"uses: basic tomato sauce"*, a tappable reference. **Navigation only:** no ingredients, quantities or portions cross the link, and nothing downstream traverses it

**Variants — a swap saved as a copy.** Replacing an ingredient (see [Replace ingredient](#-replace-ingredient--j-6-j-0--p-1)) can be kept as **a second, independent recipe**: pancakes, and pancakes the diet way. The copy has **no thread back to the original** — the same rule a saved Shared recipe already follows. A variant tied to its parent would mean an edit to one silently reaching the other, which this product refuses to do anywhere else.

> **The anchor the person barely meets.** Stored amounts have to be anchored to *some* count or there is nothing to scale from. Until 5 August that anchor was invisible, set silently at review. **The model now estimates it, and the person confirms or changes it once, at creation.** That is a better arrangement than assuming it — but note precisely what it is not: it is *not* the number that reaches the shop. That one is still typed, on the cook list entry (E6), and nothing guesses it.

> **Not an entity: the Library.** It is the set of Recipes belonging to an Account. No fields of its own; its default order is a view, not a stored property — and it can no longer be frecency of *cooking*, because nothing records cooking. See [Resolved](#resolved).

---

### E2 · Ingredient line

One row of one recipe: an amount of one thing.

**Parts**

- **amount**
- **unit** — exactly one of `g` · `ml` · `pcs`
- **the canonical ingredient it resolves to** (E3), or none, flagged
- **the text as written** [?] — so a correction screen can show what it is correcting, and an unmatched row still reads as something
- **preparation note** — *"finely chopped"*
- **non-scalable flag** — *"salt to taste"*, *"1 bay leaf"*, *"oil for frying"*
- **group label** — which heading it sits under, where the recipe has any
- **doubt flag** — unresolved ingredient · inferred conversion · vague amount. **This now persists on the saved row**, because a recipe can be saved before its doubts are settled. It clears when the row is corrected

**Job.** **J-3** — this is where amounts live, and the object that has to be right when six people sit down to a dish written for four. Also **J-4** and **J-0** (what merges into a list line) and **J-2** (what an ingredient search matches).

**Relations**

- **belongs to** exactly one Recipe (E1)
- **resolves to** one ingredient record — a Canonical ingredient (E3), or a Personal ingredient (E15) where the person has supplied one, **or to none at all**, flagged and still saveable
- **contributes to** one List line (E8) per generated list, and the contribution is stored rather than recomputed

---

### E3 · Canonical ingredient

"Onion" as a thing in the world — one record that `onion`, `onions`, `yellow onion` and `1 large onion` all point at.

**Parts**

- **display name** · **aliases**
- **aisle category** — one of ten fixed values
- **density**, g per ml
- **average unit weight**, g per pc
- **kcal per 100 g**
- **provenance and coverage** [?] — which of the above are actually present, since a missing value has to be reportable rather than guessed

**Job.** Four jobs join here, which makes it the most load-bearing object in the set.

- **J-2** — *"I cannot remember what I made with it."* Only works if `aubergine` reaches the recipe that said `eggplant`. Without it this is string matching, which fails on every synonym
- **J-3** — the three-unit rule is arithmetic over density and average unit weight
- **J-4** — the merge keys on identity, the walk keys on aisle category
- **E-2** — this record *is* the "good model behind Docker" the research finds only in Tandoor. Being careful about food without being technical means having it and not making the person run it

**Relations**

- **referenced by** Ingredient lines (E2) and List lines (E8)
- **owned by no one** — shared vocabulary, not user data
- **overlaid by** Personal ingredients (E15). Decided 5 August: when the person supplies a value the shared record lacks, it becomes their own record, and **theirs always wins on read**

---

### E4 · Capture — transient

**A name, optional photos, and pasted text — formatted, in front of you.** It exists for the length of one review and **is never stored** — decided 5 August.

**Parts**

- **the title**, typed first
- **photos**, one or several, optional
- **the raw input** — text the person pasted or typed. **Nothing else.** URL import was cut: a recipe may be copied *from* a website, but it arrives as text
- **what the model proposes** — formatted steps · tags · ingredient rows · an estimated portion count. All four are proposals, all four are editable, and rows can be added or deleted outright
- **flags**: unrecognised ingredient · inferred unit conversion · missing density · vague amount (*"a splash"*, *"a handful"*) · detected group heading

**The parser is a model, and it lives on a server.** Decided 5 August. §10 of the brief already permitted a model at import time and forbade one at query time; this puts it at the centre of import rather than at the edge. **The cost is that capture now has a network dependency it did not have** — and the offline answer falls out of decisions already taken rather than needing a new one:

> **With no signal, the name, photos and raw text save as a real recipe with no ingredient rows** — a **draft** (E1). It is the same shape as a parse that found nothing, and the same *fix it later* the product already allows. It can be cooked from and found by name and step text; **it cannot be shopped for until it is formatted.**

**And it does not wait to be asked.** An unformatted recipe **queues**, and when the connection comes back **the model runs on it in the background.** The next time the person opens the app they are told: *this was processed while you were offline — check it.* The recipe stays a **draft** until they have.

**This looks like it breaks "nothing saves silently", and it does not.** The recipe was already saved, by the person, deliberately — what the queue adds is structure to something that already exists. **Nothing is ever *confirmed* without the person**, which is the half of the rule that carries the weight. The draft flag is what keeps the promise: the app can propose in your absence, and only you can settle it.

**One consequence, which fell out of combining this with the empty-contribution rule below.** If a draft was already on the cook list and a grocery list was generated from it, that list holds a **placeholder line** saying the recipe had nothing to contribute. When the queue later formats the recipe, **the list is not rewritten** — recipe edits never rewrite a generated list. Instead the placeholder changes what it offers: *this recipe has been formatted — add its ingredients?* An explicit tap, never an automatic rewrite of a document you are already shopping from.

**Job.** **J-1** — *"I want to keep it in the seconds before it is gone."* **H-3** sits on top of it: whether entering something properly costs more than scribbling it down is decided by how much work this hands back.

**Relations**

- **becomes** one Recipe (E1) on save; its rows become Ingredient lines (E2)
- **its flags do not disappear on save — they move onto the rows** (E2) and stay visible on the recipe until corrected

**Why it is transient, and what that buys.** The alternative was a stored draft, and a stored draft is a second screen full of things you meant to get to — the graveyard the research names in three separate places. **Saving with the doubts still attached removes the need for one.** Review stays mandatory in the sense that carries the weight: nothing saves *silently*, every doubt is visible, nothing is guessed behind your back. What it drops is the part that was never load-bearing — that every doubt must be settled *now*.

**Consequence of cutting URL import.** The parser has **one** input, and paste is not the main road — it is the only road. It also means the review screen never receives clean `schema.org` markup, so **every recipe arrives at the same quality**, which at least makes the correction step uniform.

**What the library now holds.** Recipes with known-wrong rows — visibly wrong, never silently. That is a deliberate trade against design principle 3, and it holds only as long as the flag is impossible to miss on the recipe itself.

---

### E5 · Cook list

A flat list of dishes the person intends to cook. **No seven-day grid, no days, no meal positions** — decided 5 August.

**Parts**

- its **entries** (E6)
- **the date it was made** — the only date on the object, and it exists for one reason: it is the sort key that orders the library by what has been cooked most and most recently
- the **grocery lists generated from it** (E7)

**Job.** **J-0** — the main job's situation clause *is* this object: *"when I have decided what we are eating over the next few days."* Note that the job says *days* and the object no longer does; the plan is a set of intentions, and when each one happens is the person's business.

**Relations**

- **belongs to** one Account (E12)
- **contains** Cook list entries (E6)
- **produces** Grocery lists (E7), one-to-many — a second list from the same cook list is allowed, and the two stay linked both ways
- **copied from** a past Cook list — *cook this again*. In by decision; **H-4** remains its only job basis, and H-4 is a hypothesis
- **kept, not consumed.** Generating a grocery list does not spend the cook list. It has to survive, or the pointer back from a past grocery list dangles — see the [Cook list screen](#-cook-list--j-0-j-3--p-1)

**Renamed, because the old name lied.** "Plan slot" meant a cell in a grid, and there is no grid. The vocabulary is now the one the product actually uses: a **cook list** feeds a **grocery list**.

**What the flat shape costs.** With no days, there is nothing for a daily calorie average to average over, so the plan-level calorie number is gone. `kcal / 100 g` and `kcal / portion` survive untouched on the recipe, where they were the honest numbers anyway.

---

### E6 · Cook list entry

One dish on that list, for a stated number of portions. After the flattening it holds two things, and that is the entire object.

**Parts**

- **the recipe** (E1)
- **servings** — **the whole point of the object.** A plain number the person types. It may be the number of guests, or the number of meals when cooking three days ahead. Either way it is just the number the ingredients are recomputed against.
  **Changeable at any time, in place** — decided 5 August — **and the change reaches the grocery list already generated from this cook list.** See [what propagates](#what-propagates-into-a-generated-list-and-what-does-not)
- **substitutions for this occasion** — zero or more pairs: *sour cream → greek yoghurt*. **This is where a swap lands when its scope is "just this time"**, which is why the recipe stays untouched and the grocery list still buys yoghurt. Same shape as the servings count: transient while you are reading a recipe, stored the moment it carries into an entry

**Job.** **J-3** — *"cooking for the number of people actually eating."* That number is a property of this occasion, not of the recipe, which is why the entry stores its own count rather than borrowing one. Also **J-0**.

**Relations**

- **belongs to** one Cook list (E5)
- **points at** one Recipe (E1) — many entries to one recipe, deliberately: the same dish twice at different counts is two entries
- **its recipe's ingredient lines × its servings become** List lines (E8). **One multiplier, and only one**

---

### E7 · Grocery list

A dated document of what to buy.

**Parts**

- **the date it was made**
- **what generated it** — one Cook list, or an ad-hoc set of Recipes
- its **lines** (E8)
- **[?] a state** — in progress / done. No job asks for it, but two lists both in progress is exactly the condition the documented pain describes

**Job.** **J-0** (everything in one go), **J-4** (walk it once, in the order the shop is laid out), **S-2** (hand it to someone who does not live in my tools).

**Relations**

- **belongs to** one Account (E12)
- **generated from** one Cook list (E5) **or** N Recipes (E1)
- **composed of** List lines (E8)
- **linked to its Cook list** in both directions
- **shared outward as plain text.** A snapshot, not a session: the recipient reads it, and nothing they do comes back. This is S-2 exactly — *"whatever form already reaches them"*

**Generating never destroys.** A list is a dated document, not a scratchpad the next generation overwrites. Generating while one is in progress asks whether to add to it or start a new one; merging re-runs the maths across the combined set rather than appending duplicate lines.

**[?] one assumption stated plainly.** Checking items off is kept for the person's *own* list — it is the core of J-4 and costs nothing locally. What was cut on 5 August is the **live shared** list, not the tick.

---

### E8 · List line

One thing to buy — and the record of where it came from.

**Parts**

- **the canonical ingredient** (E3), or free text for a manual line — bin bags, coffee
- **total amount + unit**
- **aisle category** — read off E3, never stored here
- **checked / unchecked**
- **its contributions** — which recipes, in what amounts

**Job.** **J-4** (the object that gets checked off, in walking order) and **J-0**.

The **contributions** part belongs to **H-1** — *"open it up and see what it is made of."* Worth restating: this is the least-evidenced job in the corpus, and the one the product's only defensible wedge is built on. It stays because the position is empty, not because anyone has been watched wanting it.

**Merging rule.** Two rows merge only if the canonical ingredient matches **and** the units are compatible. `200 g tomatoes` + `3 pcs tomatoes` shows as `tomatoes — 200 g + 3 pcs`, never as a guess.

**Relations**

- **belongs to** one Grocery list (E7)
- **derived from** N Ingredient lines (E2) across N Recipes (E1) — and it **keeps** the derivation rather than recomputing it, so that editing a recipe never rewrites a list you already generated
- **recomputed** when a Cook list entry's servings change, because that number describes the occasion the list exists to serve. **The two rules are not in conflict** — see [what propagates](#what-propagates-into-a-generated-list-and-what-does-not)
- **a manual line** has no contributions and [?] no canonical ingredient

**What an unresolved row becomes here.** A recipe saved with a flagged row still generates a list. A row with no ingredient record has no identity to merge on and no aisle to sort into, so it **stands as its own line, in *other*, carrying its flag forward.** It is never dropped and never guessed at — which is the same rule the row itself follows, applied one screen later.

**And what a recipe with *no rows at all* becomes — the rule that stops a list being quietly short.** A draft that was never formatted contributes nothing. Contributing nothing must never look like contributing correctly:

> **Every cook list entry appears in the generated list, even when it has nothing to give.** A draft with no ingredient rows produces a **placeholder line** naming the dish and saying plainly that its ingredients are not known yet. It sits at the foot of the list, it cannot be ticked as if it were shopping, and it offers the two ways out: *format it now*, or *add what it needs by hand*.

Without this, four dishes planned and three shopped for looks identical to four dishes planned and four shopped for. **That is the one unrecoverable failure**, arriving through the newest door in the product.

---

### E12 · Account

The identity that owns everything and carries it between devices. **After 5 August it owns things directly** — recipes, cook lists, grocery lists and tags — because there is no household between them and it.

**Parts**

- **sign-in settings** — the address it is held under, how you signed in, changing it, signing out
- **who you are** — a display name, and [?] whether anything else about a person is worth storing when nobody else can see it
- **this device** — what is on it, what is still syncing, and when it last succeeded

**Job.** **J-6**'s *"properly mine"* clause, **E-1** (*"someone else's hands"*), **E-3**. **None of them is closed here** — the traceability matrix records it as a screen with zero jobs, accepted because the architecture needs it.

**Relations**

- **owns** every Recipe, Cook list, Grocery list, Tag and Personal ingredient
- **publishes** Shared recipes (E14), and **saves** recipes from other people's

**E-1 wants this object to be able to hand back everything it holds, and it will not.** Bulk export was declined on 5 August, so this stays a screen that no job produces — kept because the architecture requires an identity, not because a person needs the screen. See [Jobs with nothing to answer them](#jobs-with-nothing-to-answer-them).

---

### E13 · Tag — by decision

A label the person puts on recipes.

**Parts**

- **name**. Nothing else

**Basis.** **In by decision, 5 August.** No job produces it as an object: the evidenced form of *"what can I make with this"* is ingredient-first, and E3 already answers that. The nearest job is **J-2**, and the honest statement is that tags are a second, weaker route to the same place.

**Relations**

- **belongs to** one Account (E12)
- **applied to** many Recipes (E1), many-to-many
- **composes with search** rather than replacing it — a filter narrows a result set, it is not a separate mode

---

### E14 · Shared recipe — by decision

A frozen, read-only copy of one recipe, reachable by link. **After 5 August this is the only way anything moves between two people.**

**Parts**

- **the recipe content at the moment of sharing** — title, ingredients, steps, servings as set
- **the link**
- **no lifetime.** Decided 5 August: the copy is **frozen** and the link **cannot be revoked.** It resolves to the same snapshot for as long as it exists

**Basis.** **In by decision, 5 August.** It closes no job of the person who taps *share* — but it is the **supply side of somebody else's J-1**: a recipe going past them, in a form that survives three weeks. That is a real job held by a real person who is not the account holder.

**Relations**

- **published from** one Recipe (E1) by one Account (E12)
- **saved into** another Account's library as **a new, independent Recipe.** The copy has no link back: the sender can edit theirs and the receiver keeps what they were given
- **opens read-only for anyone**, account or not; saving is what needs one

**One consequence, recorded once and not argued.** A frozen, unrevocable link is **the only irreversible action in the product.** Everything else — a deleted recipe, an overwritten list, a wrong count — is recoverable or repeatable; a shared link is not. That is a coherent choice for a snapshot whose whole value is that it keeps working, and it is worth the person knowing at the moment they tap share rather than afterwards.

---

### E15 · Personal ingredient

What *you* know about an ingredient that the shared data does not. Decided 5 August, and it covers two situations with one object.

**Parts**

- **name and aliases**
- **the shared record it overlays** (E3) — **or none**, where the ingredient does not exist in the shared data at all
- **the values supplied** — any of: density g/ml · average unit weight g/pc · kcal per 100 g · aisle category
- **belongs to** one Account (E12)

**Job.** **J-3** — the three-unit rule cannot convert `200 ml cream` without a density, so a recipe stalls exactly where the data is thin. **E-2** — this is what stops precision being a privilege of people willing to maintain a food database.

**Two situations, one object**

| | What happened | What E15 does |
|---|---|---|
| **Gap** | The shared record exists but lacks a value — cream, but no density | Supplies the missing value |
| **Absence** | There is no shared record at all — nduja, a regional flour, something homemade | **Is** the record, standing on its own |

**Rules**

1. **Yours always wins on read.** A later data update never silently overwrites an answer you gave. It also means a wrong answer is wrong in every future recipe — and the same single place is where you fix it, which is the point of storing it once rather than per row
2. **Answered once, applies everywhere.** The next recipe with cream does not ask again
3. **It never leaves with a shared recipe.** Conversion happens at review, so what is stored and shared is already grams. The receiver never needs to know what you believe about cream
4. **An absent ingredient defaults to the *other* aisle** until the person says otherwise, rather than being guessed into produce

**Relations**

- **overlays** at most one Canonical ingredient (E3)
- **resolved against by** Ingredient lines (E2), ahead of the shared record
- **belongs to** one Account (E12)
- **[?] one small thing left open at field level:** whether the app ever says *"there is a shared value for cream now — use it?"* The rule above says yours wins, so silence is the safe default and a prompt is a nicety, not a decision the model waits on

---

## In by decision, not by job

**All seven items flagged in the first pass were taken into the product on 5 August.** Recorded here because the decision changed what gets built, not what the evidence says — and a register that quietly forgets the difference is no longer a register.

| | What was flagged | Where it now lives |
|---|---|---|
| **U1** | **Nutrition estimate** — kcal per 100 g, kcal per portion | Fields on E1 and E3. The *daily average* half died with the seven-day grid: a flat cook list has no days to average over |
| **U2** | **Finished-dish weight** | Field on E1 — and with U1 in, its original purpose is back: it is what makes kcal per 100 g honest |
| **U3** | **Sub-recipe link** | A relation on E1. Navigation only, nothing traverses it |
| **U4** | **Ingredient group** | Group headings on E1, a group label on E2 |
| **U5** | **Tag** | Promoted to **E13** |
| **U6** | **Public recipe snapshot** | Promoted to **E14** — and it is no longer a side feature. With household cut, **it is the entire social surface of the product** |
| **U7** | **Portion size in grams** | Derived field on E1: yield weight ÷ servings. **Direction matters** — servings stays the input, this is its output, so the 5 August servings decision is intact |

**What did not change.** No new job appeared for any of them. U1 in particular remains a feature that not one of the twelve jobs requires, against a primary persona described as *not a diet persona*. That is a decision taken with the evidence visible, which is the point of writing it down rather than an argument to revisit it.

**One promotion is now load-bearing.** U6 was the weakest item on the list when household sharing existed. It is now the only mechanism by which anything reaches another person, which makes E14 a core object rather than an extra.

---

## Retired — 5 August 2026

Three objects were removed. IDs are not reused, and each records what left with it.

### E9 · Pantry item — removed

**Decision:** the product does not track what is at home, and the grocery list does not subtract from it.

- The *"assumed you have"* section goes with it, and so does every rule protecting it
- **H-2** loses its object entirely — it was an unobserved hypothesis, so nothing measured is lost
- **J-0 is now served on one half only.** *"Without doing the arithmetic **or the remembering** myself"* — the arithmetic half stands; the remembering half is not addressed
- **One cost, recorded rather than argued:** §9's success criterion *"nothing gets bought that was already in the cupboard"* can no longer be met, and its twin — *"nothing gets missed because the app assumed it was"* — is met absolutely, by never assuming

### E10 · Household — removed

**Decision:** there is an account. There is no family, no shared account, no shared library. Sharing a recipe means the other person saves their own copy.

- **J-5** — *feeding a household without collisions* — has no object. Removed from the served set
- **S-1** — *being legible to the people I share a kitchen with* — has no object either
- The live shared list, member invites and flat-permission model all go
- **Everything the household owned now belongs to the Account** (E12), which simplifies every ownership relation in the model rather than complicating it
- The first pass concluded *"solo is a household of one that is never mentioned."* That is now the only case, so the scope collapses into the account and the reasoning is retired with it

### E11 · Person — removed

**Decision:** what a slot needs is a number of portions, not a set of named people. It may be guests, it may be meals across three days — either way it is a plain number the ingredients are recomputed against.

- **Closes the open question opened by the servings decision** — *what is member assignment for* — by deletion
- The per-person calorie average becomes a plain daily average on the Plan (E5)
- The distinction the first pass worried about — six at the table versus four in the household — disappears, because nothing counts people any more

---

## Jobs with nothing to answer them

The inverse pass. **This list grew on 5 August**, which is the honest cost of the cuts.

- **J-5 · feeding a household without collisions** — no object. Removed by decision
- **S-1 · being legible to the people I share a kitchen with** — no object. Removed by decision
- **H-2 · being sure of what is at home before leaving the shop** — no object. Removed with the pantry
- **E-1 · committing without being trapped.** Scores 3 for one persona and 2 for the primary — a stated precondition for typing anything in at all — and no object answers it. **Declined on 5 August: there is no bulk export of the library.** A grocery list leaves as text and one recipe leaves as a link; the collection as a whole does not leave
- **E-2 · careful without being technical.** Correctly has no object: it is the bar E3, E4 and the unit rule are held to
- **E-3 · it stays what I chose.** Correctly has no object: closed by refusals
- **H-6 · the order matching the shop I am standing in.** No store object by decision — one fixed walking order

---

## Value sets, not entities

| | Values |
|---|---|
| **Unit** | `g` · `ml` · `pcs` — exactly three, in the ingredient line only |
| **Aisle category** | ten, in a fixed walking order. Fixed order is what stops this becoming a Store |
| **Doubt flag** | unrecognised ingredient · inferred conversion · missing density · vague amount · detected heading. **Persists on the saved row**, since a recipe can be saved before its doubts are settled |

*Meal position — breakfast · lunch · dinner · extra — was retired with the grid on 5 August.*

## Deliberately absent

- **Sync state, write queues, the local copy** — infrastructure, not objects a person deals with
- **Saved search, filter chip, query syntax** — rejected in §8 of the brief
- **URL fetcher, share target** — cut on 5 August; the parser has one input
- **Role, permission, invite, member** — retired with the household

---

## Resolved

Recorded in the register style of §10.1 of the brief so they are not reopened by accident.

### 5 August 2026 · first pass

| Question | Decision | What moved |
|---|---|---|
| Which number answers J-3 — base servings, the stepper, or a portion size in grams? | **The user types the number of portions.** An input, not a fixed property of the recipe | E1 · E6 · E8 · U7 |
| Should anything record that a dish was actually cooked? | **No. It affects nothing** | A thirteenth entity rejected · E1 · E5 |

**Consequences that survive the second pass.** The recipe carries no user-facing serving count, only an invisible anchor. The grocery list multiplies by **one** number — *ingredient × servings* — and after the removal of E11 there is no second multiplier left to confuse it with. The library's default order can no longer be frecency of *cooking*; the free substitute is **frecency of planning**, since slots are dated already. **One cost:** *median times-cooked* was the week-one measurement meant to decide which persona is the real centre of the product, and the product can no longer produce that number.

### 5 August 2026 · second pass

| Question | Decision | What moved |
|---|---|---|
| Recipe capture from a URL? | **No.** Recipes are written or pasted as text. A site can be copied *from*, but nothing is fetched | E4 · E1 source · no server-side fetcher |
| A live shared grocery list? | **No — too complex.** A list can be shared, but the shared thing is not interactive | E7 · E8 · J-5 and S-1 lose their objects |
| Track what is in the cupboard? | **No.** The list does not subtract what is at home | **E9 retired** |
| A household? | **No.** One account; sharing a recipe means the other person saves their own copy | **E10 retired** · E12 owns everything |
| Named people on a slot? | **No.** A slot needs a number of portions, nothing more | **E11 retired** · closes the member-assignment question |
| The seven items no job produces? | **Build all seven** | U1–U7 · **E13** and **E14** created |

### 5 August 2026 · third pass

| Question | Decision | What moved |
|---|---|---|
| Is the plan a seven-day grid, or a list of things to cook? | **A flat list. No days, no meal positions** | E5 and E6 renamed · meal position retired · the plan-level calorie average dies with the days |
| Is a shared recipe a frozen copy or a live link? | **Frozen, and it cannot be revoked** | E14's lifetime question closed |

### 5 August 2026 · fifth pass — from drawing the flows

| Question | Decision | What moved |
|---|---|---|
| Can an ingredient be swapped for another? | **Yes** — sour cream for greek yoghurt — with three scopes: **once · always · as a copy** | **New screen: Replace ingredient** · E6 gains substitutions · E1 gains variants |
| Where is the portion count set when planning? | **On the recipe, before adding**, and the add sheet carries it | J-0's flow · the Library-row shortcut stays for the unchanged case |
| How does a recipe get created? | **A screen of its own.** Name, then optional photos, then the text — **then a model formats it**, proposing steps, tags, ingredient rows and an estimated portion count, all editable, rows addable and deletable | E1 · E4 · the Recipe editor screen |
| What happens with no signal? | **The name, photos and raw text save as a real recipe with no rows, flagged.** Format it later, as an action on the recipe | E4 · J-1's flow |

### 5 August 2026 · sixth pass — the coverage blanks, reviewed

| Question | Decision | What moved |
|---|---|---|
| Account has no job — remove it? | **No. Accepted.** It is required by the architecture: an identity has to exist for sync and be reachable. A screen can be required by the architecture and by no job at once | Traceability · E12 · the fourth nav item |
| J-5 and S-1 have no screen — add one? | **No. Accepted.** Household is paused, and the rows are the pause showing up in the coverage | Traceability |
| E-1 has no screen — bring export forward? | **No. Bulk export of the library is not being built.** §8.1 listed it as a post-MVP obligation; that is now a rejection, not a schedule | Traceability · E12 · Jobs with nothing to answer them |

### 5 August 2026 · seventh pass — from the IA critique

| Question | Decision | What moved |
|---|---|---|
| Where does an empty search or an empty library lead? | **To a button that creates the recipe.** Not an apology, and **not a remark about whether you have ever cooked it** | Library states · J-2's flow |
| What happens to a recipe that could not be formatted? | **It queues. The model runs on it when the connection returns, and the next time you open the app you are told to check it** | E1's draft field · E4 · J-1's flow |
| How is an unfinished recipe shown? | **As a draft — visible and highlighted**, wherever it appears. Fully usable, never blocked | E1 · Library · Cook list |
| What does a recipe with no ingredient rows contribute to a shopping list? | **A placeholder line that cannot be ticked**, naming the dish and saying its ingredients are not known. Never silence | E8 |
| Does a substitution reach an already-generated list? | **Yes** — everything on a cook list entry reaches it; everything on a recipe does not | E7 · E8 · E6 |
| What is on the Account screen? | **Sign-in settings, who you are, and this device's sync state** | E12 |
| Are the empty, loading and error states specified? | **For all nine screens**, with two rules: an empty state names the next thing to do, and an error never blocks what is already on the device | New states table |

### 5 August 2026 · fourth pass

| Question | Decision | What moved |
|---|---|---|
| Can a half-corrected paste be left and returned to? | **A recipe saves immediately, flags and all.** No stored draft; the doubts move onto the rows and stay visible until corrected | E4 becomes transient · E2 gains a persistent doubt flag · E8 gains the unresolved-row rule |
| Where does a gram weight you type go? | **Into your own record for that ingredient.** Answered once, applies everywhere, and yours always wins over the shipped value | **E15 created** · E3 gains an overlay relation |

---

## Open decisions — none

All six questions raised across the four passes are closed: four by decision, two by deletion. **The entity pass is finished.**

What remains marked **[?]** is field-level and does not block anything: whether a row keeps its original text, how ingredient-data coverage is reported, whether a grocery list carries a done state, whether a past cook list can be copied forward, and whether the app ever offers a newly shipped value in place of a personal one. Each is a small choice inside an object whose shape is settled.

The record of what was asked and answered, for reference:

### 1 · Can a half-corrected paste be left and returned to? (E4)

**The situation.** You paste a recipe. The parser produces the rows and marks four it is unsure of — an ingredient it does not recognise, a conversion it guessed, a *"handful"* it will not guess at. You have thirty seconds, not five minutes. What happens to what you pasted?

**Three answers, and the third dissolves the question:**

| | What happens | Cost |
|---|---|---|
| **A** | Nothing is kept. Paste, correct, save — all in one sitting, or start again | Pasting only works when you have five free minutes. Recipes seen in a busy moment never get in |
| **B** | It is kept as an unfinished draft you come back to | A second stored object, with its own screen and its own pile of things you meant to get to — the exact graveyard the research names in three separate places |
| **C** | **You can save it now, flags and all.** The recipe is real and usable immediately; the doubtful rows stay marked *on the recipe* until you fix them | The library can hold recipes with known-wrong rows — visibly wrong, never silently |

**Decided: C.** It keeps review mandatory in the sense that matters — nothing saves *silently*, every doubt is visible and nothing is guessed behind your back — while dropping the part that was never load-bearing: that every doubt must be resolved *now*. No second object, and the correction can happen at the counter, where the recipe is open anyway.

**Why this got more expensive on 5 August.** With URL import cut, paste is not the main road into the product — it is the only one. If it demands an uninterrupted five minutes, the library never reaches the size everything downstream assumes.

### 2 · Where does a gram weight you type go? (E3)

**The situation.** A recipe says `200 ml cream`. To hold the three-unit rule, that has to become grams — which needs cream's density. Suppose the ingredient data does not have it. The row is flagged, and you are asked: *how many grams is this?* You type **205**.

**Where does 205 live afterwards?**

| | Where it goes | What happens next time |
|---|---|---|
| **A** | Only in this recipe's row | The next recipe with cream asks again. And the one after that |
| **B** | **In your own record for cream** — *"1.02 g per ml, according to you"* | Answered once, applies everywhere, editable in one place |
| **C** | Into the shared ingredient data everyone uses | Needs review and moderation. Zero budget, one user — no |

**Decided: B**, a personal layer over the shared record — now **E15**. Your value always wins over the shipped one, so a later data update never silently overwrites an answer you gave. The cost is the mirror image: a wrong answer is wrong in every future recipe — and the same single place is where you fix it.

**One wrinkle that resolves itself.** Sharing a recipe (E14) does not have to carry your densities: conversion happens at review, so what is stored and shared is already grams. The receiver never needs to know what you believe about cream.

**The one dependency this leaves.** E15 is a layer, and a layer needs something underneath it — so the shape of the object is settled, but building it still waits on §10's unresolved question of where the shared ingredient data comes from. That is a data-source question, not a model question, and nothing in the wireframes waits on it.

---

**Next:** [Screens](#screens).

---

# Screens

**Date:** 5 August 2026 · draft
**Derived from:** the twelve objects above and the jobs in [`research/jtbd.md`](./research/jtbd.md). **Nothing here is taken from a competitor's structure** — the grouping is what a person is trying to do, and the screens are what each object needs in order to be looked at or changed.

### How to read this

- **The top level is not navigation.** Those six lines are intentions, not tabs and not sections. Which of them become tabs is a step-3 question, and answering it here would be exactly the copied-menu mistake this pass is avoiding
- **Every screen carries the job it closes.** No job means **[СИРОТА]**, and the reason is stated
- **P-1** is the Systematic Optimiser, primary. Secondary personas are named where they appear — which is almost nowhere, and that is a finding rather than an omission
- **Empty, loading and error are states, not screens**, and so are search, filters and disclosures. What was demoted is listed at the foot
- **Depth is deliberately shallow.** One nesting level exists in the whole tree

---

## The tree

```
COOKSY
│
├─ Getting a recipe in ─────────────────────────────────── J-1
│  └─ ▸ RECIPE EDITOR ............... J-1 · J-6 ......... P-1 · P-3
│     └─ ▸ FIX INGREDIENT ........... J-3 · E-2 ......... P-1
│
├─ Getting back to something I already have ───────────── J-2 · J-6
│  ├─ ▸ LIBRARY ..................... J-2 · J-6 ......... P-1
│  │     · search — names · ingredients · steps · tags .. J-2
│  │     · tag filter, composed with it ................. J-2
│  │     · paste box .................................... J-1
│  ├─ ▸ RECIPE ...................... J-6 · J-3 · J-2 ... P-1
│  │     · servings, and everything answering to it ..... J-3
│  │     · shared state — opened from a forwarded link .. their J-1
│  └─ ▸ REPLACE INGREDIENT .......... J-6 · J-0 ......... P-1
│
├─ Deciding what to cook ──────────────────────────────── J-0
│  └─ ▸ COOK LIST ................... J-0 · J-3 ......... P-1
│        · servings, changeable in place ................ J-3
│        · past cook lists, and switching between them .. structural
│        · cook this again — copy a past one forward .... H-4
│
├─ Getting it into the house ──────────────────────────── J-0 · J-4
│  └─ ▸ GROCERY LIST ............... J-4 · J-0 · H-1 · S-2   P-1
│        · past lists, and switching between them ....... by decision
│        · line breakdown — which recipes, how much ..... H-1
│        · export as text ............................... S-2
│
└─ Keeping the maths honest ───────────────────────────── J-3 · E-2
   └─ ▸ ACCOUNT ..................... [СИРОТА] .......... P-1
      └─ ▸ MY INGREDIENTS ........... J-3 · E-2 ......... P-1


   ▸  a screen
   ·  part of the screen above it — a state, a control or a section
```

**Nine screens, and nothing left over.** Every candidate either became a screen or found a home inside one. None of the nine belongs to anyone but P-1 — and the one audience outside P-1 does not get a screen either, it gets a state of P-1's.

---

## What each one is for

### ▸ Recipe editor — J-1, J-6 · P-1 and P-3

Where text becomes a recipe, and where a recipe gets corrected. **Reached from the Library as a screen of its own** — creating a recipe is not something that happens inside a box on another screen.

**What the person does, in order:**

1. **Names it.** First, because a name is the one field they always have
2. **Adds photos** — one or several, optional
3. **Pastes or types the text**
4. **A model formats it** and comes back with four proposals: the steps as readable text, tags, the ingredient rows, and an estimated portion count
5. **Edits any of it.** Every word of the text, every tag, every row — and rows can be added or deleted outright

**One screen, four ways in**, and this is the pass's main structural finding: **review and edit are the same screen.**

1. Text was pasted → the model's proposals, doubts first
2. Nothing was pasted → an empty recipe, typed by hand
3. A saved recipe is being changed → the same rows, no doubts
4. A flagged row is being fixed → the same screen, scrolled to it

Splitting review from editing would mean two screens that do the same work on the same object, and would make the fourth entry point homeless. Keeping them as one is what makes **save-now-fix-later** coherent: the place you go back to is the place you left.

**Objects:** E4 → E1, E2. **The only persona note in the tree:** P-3 the Reel Hoarder passes through here too, and this is the only screen they touch. It is also where they are most likely to leave, which is what the unrun parser bake-off (G-1) was meant to measure.

### ▸ Fix ingredient — J-3, E-2 · P-1

*"What is this, and how many grams?"* Reached from a flagged row — in the editor, on the recipe, or from a grocery line that ended up in *other*.

It is a screen rather than a field because **it writes an object** (E15) that outlives this recipe, and the person should be able to see that it did. It is the concrete form of **E-2**: this is the exact moment where a technical product would show a database and this one asks one question.

**Objects:** E15, E2, E3.

### ▸ Library — J-2, J-6 · P-1

Everything I have kept, and **the place J-2 is actually answered.**

**Search is the substance of this screen, not an accessory to it.** *"There is an aubergine in the fridge and it turns tomorrow"* is the pain the research ranks first, and this is the only surface that answers it. What it does:

- **Matches four things** — recipe names · ingredients · method steps · tags
- **Resolves through canonical ingredients** (E3, E15), so typing `aubergine` finds the recipe that said `eggplant`, and `onion` finds the one that said *2 large yellow onions*
- **Splits every result in two** — **Dishes**, where the recipe *is* the thing, matched on title and tags; and **Used in**, where the thing happens inside the recipe, matched on ingredient rows and steps. The distinction is the answer: *am I looking for the fried chicken, or for what to do with it*
- **Every row states its evidence** — what matched, the amount that recipe needs at its own servings, and the ingredient group where the recipe has one
- **Ranks partial matches, never discards them.** Type three ingredients and the recipes with all three come first, then two, then one. That is also what replaces an empty state
- **The person never types an amount. Cooksy always shows one.** Quantities are output, never input — the app knows exactly what a recipe needs and knows nothing about what is in your kitchen
- **Runs locally, returns as you type.** No spinner, no network — this screen gets used in a kitchen and in a shop

**Before anything is typed**, the order is frecency of planning, resettable. Tag filters compose with search rather than replacing it.

**Two things this screen owes the person beyond retrieval.** **Drafts are highlighted here** — a recipe that is unformatted, unconfirmed or freshly processed by the queue is visibly so, in the one place the whole collection is seen at once. And **a search that matches nothing offers to create the recipe**, because "I could not find it" and "I do not have it" are the same sentence for a library of your own making, and the answer to both is a button, not an apology.

**It is still not a separate screen.** There is no moment where the person has *gone to search* — the field is on the Library and the Library rearranges under it. Making it a screen of its own would add a destination to a task that is already here.

**Objects:** E1, E13, resolved through E3 and E15.

### ▸ Recipe — J-6, J-3, J-2 · P-1 — **and one audience that is not P-1**

One dish, ready to cook from. The servings number sits at the top and every amount answers to it.

This is the destination of J-2 and the object of J-6 — and it is also where **J-3 is felt**, even though the number that reaches the shopping list is typed on the cook list. Both places take the same input and mean the same thing.

**The shared recipe is not a second screen. It is this one, opened from a link somebody forwarded.**

That is the correction that removed a screen from this map, and it is right: a recipe you were sent is a recipe. The screen does not change — what changes is who is standing in front of it, which is a **state**, exactly like empty or offline:

| | Mine | Sent to me |
|---|---|---|
| The dish, amounts, steps | the same | the same |
| Servings | mine to change | mine to change — it is arithmetic over what I am reading |
| Actions | edit · add to cook list · share · tag | **save to my library**, and nothing else |
| What it points at | my recipe, live | **the frozen snapshot** (E14). The sender editing theirs afterwards changes nothing here |

The last row is the one thing worth stating out loud, because "just forward the URL" makes it sound live and it is not: the link resolves to the copy made at the moment of sharing. That was decided deliberately — it is what keeps *the user's recipe is sacred* true on both ends.

**Objects:** E1, E2, E13, E14, resolved through E3 and E15.

### ▸ Replace ingredient — J-6, J-0 · P-1

*"Not sour cream. Greek yoghurt."* Reached from an ingredient row, on the Recipe screen or in the editor.

**A screen rather than a sheet**, for the same reason *Fix ingredient* is: it needs a searchable list of everything the app knows about food, and it ends in a choice with three genuinely different consequences.

| Scope | What changes | What it creates |
|---|---|---|
| **Just this time** | This occasion only | A substitution on the **cook list entry** (E6). The recipe is untouched; the grocery list buys yoghurt |
| **Always** | The recipe, from here on | Nothing new — an edit to an ingredient row like any other |
| **As a copy** | Nothing about the original | **A second recipe** (E1). Pancakes, and pancakes the diet way |

**Job.** **J-6** — a variant you worked out is exactly *"my version, on the third attempt"*, which is the job's own phrasing. **J-0** — the list has to buy what will actually be cooked, and a swap that did not reach it would put the wrong thing in the trolley.

**The stated motive is calories**, and it is worth recording precisely rather than glossing: swapping in order to see what a dish *becomes* rests on the calorie estimate, which **no job in the research produces** ([U1](#in-by-decision-not-by-job)). The screen has jobs; the reason it was asked for does not. Both facts are true and neither cancels the other.

**Objects:** E1, E2, E3, E6, E15.

### ▸ Cook list — J-0, J-3 · P-1

The dishes I intend to cook, each with a portion count. Flat: no days, no meal slots.

**This is where J-0's situation clause lives** — *"when I have decided what we are eating over the next few days"* — and the one action that matters leaves it: generate the shopping list.

**The servings count is changeable here, in place, on any entry** — decided 5 August. Six became four, or the guests cancelled, and the fix should not require deleting the dish and adding it again.

**And it reaches the grocery list.** That is the substantive half of the decision, and it drew a line the model did not have — see [what propagates and what does not](#what-propagates-into-a-generated-list-and-what-does-not) under Grocery list.

**One thing this quietly repairs.** The first pass worried that the servings control — the hero interaction, the moment the product is supposed to sell itself — *"produces no durable consequence"*, because the number on the recipe screen is a view that never mutates anything. It now has a second home where it does: **the cook list is the one place where moving that control changes what you buy.** Same control, same meaning, and here it bites.

**Past cook lists live here too, and this one is not symmetry — it is required.** The argument turned out stronger than the parallel with grocery lists that suggested it:

1. **A cook list has to go somewhere after the shop.** Once a grocery list has been generated from it, either the cook list is cleared — and *"what did I plan last week"* becomes unanswerable — or it is kept. There is no third option, and clearing is a decision nobody made
2. **The link between the two objects is bidirectional** (E5 ↔ E7), and it is already in the model: from a cook list you reach its grocery list, from a grocery list you reach the cook list that produced it. **Past grocery lists are kept.** If cook lists were disposable, every pointer back from an old shop would dangle — the archive would hold half a record
3. **Copy-forward needs something to copy from.** *"Cook this again"* is H-4, still a hypothesis, and it is now the one thing on this screen resting on one

So the screen owns the whole set, exactly as Grocery list does: the current one, the ones before it, and the same control moving between them.

**Objects:** E5, E6.

### ▸ Grocery list — J-4, J-0, H-1, S-2 · P-1

One pass through the shop. Aisle-ordered, checkable, and openable.

Four jobs land on one screen, which is unusual enough to note: **J-4** is the walking order and the tick, **J-0** is the completeness, **H-1** is tapping a line to see which recipes it came from, **S-2** is handing the whole thing to someone as text.

**Past lists live here too** — this screen owns the whole set, not just the one in progress. Switching between an in-progress list and a newly generated one is a control in its header; reaching a dated older one is the same control, scrolled further. **In by decision**, and the distinction from before is worth keeping visible: what is *evidenced* is only that generating must not destroy a half-finished shop. Browsing what was bought in March is a decision, not a job — and it costs almost nothing, since a grocery list is a few hundred bytes.

**Objects:** E7, E8. **Four things here are not screens:** the breakdown of a line is a disclosure, the past-list switcher is a control in the header, exporting as text is an action, and a completed list is a state rather than an archive to travel to.

### What propagates into a generated list, and what does not

Making the cook list's servings count reach the grocery list forced a distinction the model had been carrying without stating. Two edits, two answers, and the difference is principled rather than arbitrary:

| I changed… | The generated list | Why |
|---|---|---|
| **The count on a cook list entry** | **updates** | The count is a statement about *this occasion*, and the list is a rendering of that occasion. If the plan says six and the list says four, the list is simply wrong |
| **A substitution on a cook list entry** — *just this time, yoghurt not sour cream* | **updates** | Same object, same reasoning. A swap that did not reach the list would put the wrong thing in the trolley, which is worse than a wrong amount |
| **The recipe itself** — an amount, an ingredient, a fixed flag, a swap set to *always* | **does not update** | The recipe is a document you revise over years (J-6, *"my version, on the third attempt"*). Revising it must not retroactively rewrite shopping you already planned. The list keeps what the recipe said when it was generated — which is what E8's stored contributions are for |
| **A missing gram weight, supplied from a grocery line** | **updates that line only** | You were standing in the list and answered a question the list asked. It would be perverse to make the answer land anywhere else — and it changes one line, not the merge |

**In one line: the list is downstream of the plan, and a snapshot of the recipes.** Everything on a cook list entry reaches it; everything on a recipe does not.

**Which list is affected.** Only the **in-progress** list generated from that cook list. Past and completed lists are records; they are never rewritten, exactly as they are never overwritten by a new generation.

**How the change shows itself**, because a quantity that shifts without saying so is the one unrecoverable failure:

1. **Changed lines are marked** until the person has seen them. The list does not quietly settle into a new shape
2. **An amount that went up unchecks its line**, and says why. You genuinely need more of it, and leaving it ticked would send you home short — which is precisely the failure the whole product is built to avoid
3. **An amount that went down leaves the line alone**, marked. Having bought more than you need is harmless and undoing a tick would be worse
4. **An entry removed from the plan** takes its unticked line with it and leaves a ticked one in place. You already bought it; that is a fact, not a plan

**There is no third party to surprise here.** Household was cut, so the only person who can change a count is the one holding the list — every propagation is the direct consequence of something they just did. That is what makes automatic propagation safe enough to do without a confirmation prompt, and marking enough to keep it honest.

### ▸ My ingredients — J-3, E-2 · P-1

Everything I have told Cooksy about food that it did not already know.

Implied directly by the E15 decision: *"a wrong answer is wrong in every future recipe — and the same single place is where you fix it."* This is that place. Low frequency, and it should look like it.

**Objects:** E15, E3.

### ▸ Account — **[СИРОТА]** · P-1

Sign in, sign out, and the way into *My ingredients*.

**No job produces it.** It exists because cloud accounts are a locked decision (§4 of the brief) — the same reason the tags and the calorie fields are in the model. **E-1** would give it a real purpose the moment full export lands, and until then this screen is the placeholder for a job the product does not close.

---

## Nothing left over

Both archive candidates found homes inside existing screens rather than becoming screens of their own. **Neither one earned a destination; both earned a section.**

That is the shape this pass keeps arriving at, and it is worth naming as a rule rather than a coincidence: **a thing that is the same object in a different state belongs on the same screen.** A past grocery list is a grocery list. A past cook list is a cook list. A recipe somebody sent you is a recipe. Three of the four things that looked like separate screens at the start of this pass were the same object wearing a different state — which is exactly the mistake the brief's own §6 warns about from the other direction, when it keeps the pantry out of the tab bar because a tab bar should reflect frequency of use, not feature count.

---

## Which persona each screen serves — and the finding

| Persona | Screens of their own | Reading |
|---|---|---|
| **P-1** Systematic Optimiser | **All nine** | As it should be. The product is theirs |
| **P-3** Reel Hoarder | **None.** Passes through the editor | Their two entry paths — share sheet and URL import — are both gone. What is left is a paste box they share with P-1 |
| **P-2** Household Logistics Lead | **None** | Household was cut. There is nothing here for them at all |
| **P-4** Data Sovereign | **None.** Account is the nearest, and it is an orphan | Export is post-MVP and a cloud account is mandatory. Both point away from them |

**The finding, stated plainly: after the cuts, every screen in the product belongs to P-1.** That is not a defect in the sitemap — it is what the scope decisions meant, made visible one layer down.

**And it got sharper when the shared recipe folded into Recipe.** The one audience outside P-1 — a stranger holding a forwarded link — does not get a screen at all now. They get a state of P-1's recipe screen, with one action on it. Which is the correct answer, and also an honest measure of how much of this product faces outward: one row in a table.

**What follows from it:** the product now stands or falls on P-1 alone, and the two week-one measurements meant to test whether P-1 or P-3 is the real centre are no longer answerable from inside the product. That was already recorded when cook tracking was dropped; the screen map is where it becomes concrete.

---

## Demoted — states, controls and actions, not screens

Listed because each of them is a screen in at least one competitor, and treating them as screens is how a nine-screen product becomes a twenty-screen one.

| | Where it actually lives |
|---|---|
| **Search** · **tag filter** | The substance of **Library**, and still a state of it. Runs locally as you type; there is no moment of "going to search" |
| **Paste box** | A control on **Library**. Pasting moves you to the editor immediately |
| **A recipe somebody sent me** | A **state of Recipe**, not a page of its own. Same screen, one action — save to my library |
| **Past grocery lists** | A section of **Grocery list**, reached by the same control that switches between two live ones |
| **Past cook lists** | A section of **Cook list**, same control, same shape. Required rather than symmetrical — see the screen |
| **Line breakdown** — which recipes this came from | A disclosure on **Grocery list**. It is H-1's whole point and still not a screen |
| **Add to cook list**, with its portion count | A sheet raised from a **Library** row or from **Recipe**. **It opens with the count already set to whatever the recipe screen is currently showing** — continuity with a number the person set seconds ago, not a default and not a guess, and still theirs to change. Decided 5 August, from [`flows.md`](./flows.md) |
| **Export as text** | An action on **Grocery list** |
| **Share a recipe** | An action on **Recipe**, producing E14 |
| **Empty · loading · error · offline · unsaved** | States of whichever screen they occur on. Every screen has them; none of them is one |

---

## Every screen's states

The line above — *every screen has them* — was true and useless while only four screens had theirs written down. **They were specified where a flow happened to pass and nowhere else.** This closes that: nine screens, every one of them.

**Two rules govern the whole table.** An empty state **names the one thing to do next and offers the control for it** — an empty screen that only apologises is a dead end with better manners. And an error **never blocks what is already on the device**: the network failing is not a reason to stop reading a recipe.

| Screen | Empty | Loading | Error | Also |
|---|---|---|---|---|
| **Library** | *Nothing saved yet* → **the button is New recipe.** It is the only thing to do here on day one | The first sync onto a new device — once, ever | **Sync failed.** Everything on the device still reads and still edits; a quiet marker, never a modal, never a blocked screen | **Drafts are highlighted.** A search that matches nothing offers **create this recipe** rather than an apology |
| **Recipe editor** | A blank recipe, cursor in the name field | **The model formatting.** The one genuine network wait in the product | **Two, and they read differently.** *No signal* → saved as text, formatted when the connection returns. *The model failed* — timed out, errored, hit a limit → **retry**, or save as text and let the queue take it | Saved-with-doubts, on leaving |
| **Fix ingredient** | The picker matches nothing → **name it yourself and give the weight.** This is the path that creates a personal ingredient | — | — | Reached from three places; it returns to whichever one it came from |
| **Recipe** | — | — | **A dead link.** The account behind a shared recipe is gone. Say exactly that and offer nothing false — no "try again", no half-loaded page | Draft banner · *formatted while you were away, check it* · read-only when opened from a link |
| **Replace ingredient** | The picker matches nothing → **create the ingredient**, or keep the original and close | — | — | The scope choice is the last step, never the first — nothing changes until it is made |
| **Cook list** | *Nothing planned yet* → **the button is Go to the library** | — | — | An entry whose recipe is a draft with no rows is **marked here, before the list is generated** — the earliest place the problem can be seen |
| **Grocery list** | Two, and they are not the same. *No list yet* → **Generate one from the cook list.** Everything ticked → **done**, with the date, not an empty screen | — | — | Offline · changed lines marked · the placeholder line for a draft entry |
| **My ingredients** | *Nothing yet* — and it says **when this fills**: the first time you tell the app about something it did not know. Not a call to action; there is nothing to do here yet | — | — | This is the typical state for months. It should read as normal, not as a gap |
| **Account** | — | Signing in | **Sign-in failed** — say which part. **Offline** is not an error: you stay signed in, and sync waits | — |

**The one state that is not on this table**, because it belongs to no single screen: a **queued format** waiting for a connection. It lives on the recipe as a draft, it is highlighted in the Library, and it resolves itself without being asked.

---

**Next:** [Navigation](#navigation).

---

# Navigation

**Date:** 5 August 2026 · draft
**Built on:** the screens above. **No new screens are invented here** — this pass only decides what is always visible, what appears in the flow, and how deep anything sits.

**Main job:** **J-0** — *"when I have decided what we are eating over the next few days, I want to get everything into the house in one go, without doing the arithmetic or the remembering myself."*
**Primary persona:** **P-1**, the Systematic Optimiser — someone who already knows what they want to cook and needs the logistics to disappear.

**How a tap is counted**, so the numbers mean something: a **tap** is one discrete touch that changes what is on screen or commits something. Typing a number is one interaction regardless of digits. Scrolling is not a tap. Landing on the app's first screen costs nothing.

---

## 1 · Global navigation — four

| | Job cluster behind it | Why it is global |
|---|---|---|
| **Library** | **J-2** getting back to something I already have · **J-6** the good version outlasting memory · **J-1** keeping what I find | Two of the three things a person does daily happen here, and the third — capture — is a box on this screen rather than a place of its own. It is also the only screen with content on day one |
| **Cook list** | **J-0** the main job's situation clause · **J-3** the number of people actually eating | The decision half of J-0. This is where *"I have decided what we are eating"* stops being a thought and becomes an object — and where changing the count changes what you buy |
| **Grocery list** | **J-4** one trip instead of three laps · **J-0** the completeness half · **S-2** handing it to someone outside my tools | The payoff half of J-0, and the only screen used **in a shop** — a place with a trolley in one hand, bad light and no signal. It has to be one tap from anywhere, always |
| **Account** | **J-3** and **E-2**, through *My ingredients*, which lives inside it. The Account screen itself: **none** | Decided 5 August. Everything about me and how the app is set up, in one place: the account, settings, and what I have told Cooksy about food it did not know |

**Read across the first three and the core loop reads back: keep → decide → buy.** That is not a coincidence and it is not a menu — it is the product's one sentence, laid out left to right. **The fourth is not part of the loop**, and it should not pretend to be: it is where you go when something about *you* needs changing rather than something about dinner.

### The fourth item, recorded honestly

Three was the recommendation, on the brief's own rule that **navigation reflects frequency of use, not feature count**. Four is the decision, and the trade is worth writing down rather than smoothing over:

- **What it costs.** The bar is the most expensive real estate in the product, and a quarter of it now goes to a screen touched a handful of times a year. The three items that carry the loop each lost a share of the width
- **What makes it defensible anyway.** The tab is not *Settings* — **it is the whole "keeping the maths honest" cluster**, and the thing carrying a job inside it is *My ingredients* (J-3, E-2). Naming the tab after the person rather than after a preferences screen is what makes it a place instead of a drawer
- **What it fixes.** *Account* was reached through a header control that had no other reason to exist. A tab removes the control and the ambiguity with it
- **What it does not fix.** The Account screen closes no job, and after 5 August it never will — bulk export was declined, so **E-1** is not coming to give it one. It is a **permanent orphan with permanent real estate**, kept because the architecture needs an identity to exist and be reachable. **A screen can be required by the architecture and required by no job at the same time**; that is what this one is

### Still refused

- **Add / capture as an item.** The paste box is already on the landing screen at zero taps. A tab would be a second door into the same room — and would imply capture is a place you go, when J-1 asks for the opposite
- **Search as an item.** It is a state of Library. A tab creates a destination for something already in front of you, and reintroduces the "gone to search" moment the screen pass removed
- **Recipe or the editor as an item.** Neither is a destination. Both are always reached *from* something, which is what makes them contextual rather than global

---

## 2 · Depth — taps to the main job

**J-0 has two moments**, and conflating them is how this number gets fudged. Both are counted.

| What is being reached | From a cold open | Verdict |
|---|---|---|
| **The job's surface** — the list, in the shop, ready to tick | **1 tap** | Grocery list is a global item |
| **The decision point** — the cook list, to say what we're eating | **1 tap** | Cook list is a global item |
| **The whole loop, cold, one recipe** — from opening the app to a finished grocery list | **5 taps**, of which **1 is navigation** | See below |

### The five, broken down — and why only one of them is depth

| # | Tap | Navigation, or the work itself? |
|---|---|---|
| 0 | App opens on **Library** | free |
| 1 | Tap a recipe | **navigation** |
| 2 | *Add to cook list* | the work — this is the decision |
| 3 | Confirm, with the servings typed | the work — **this is J-3**, the number the whole product is built to get right |
| 4 | Switch to **Cook list** | navigation, but a global tab |
| 5 | *Generate grocery list* | the work — the act J-0 names |

**Navigation depth is 1. The other four taps are the job, not the route to it.** Asking for the portion count is not overhead to be optimised away — it is the single decision that makes every downstream number correct, and removing it would mean guessing, which the servings decision explicitly refused.

### Where it does get expensive, and the restructure

One recipe is not a real week. **Four dishes is**, and that is where the count turns bad — because reaching a recipe, adding it, and coming back is a round trip repeated per dish.

| A four-dish week | Taps |
|---|---|
| **Through the recipe** — open · set the portions · add · confirm · back, four times over, then plan and generate | **18** |
| **From the Library row** — add in place, without opening the recipe | **10** |

**Both paths exist, and the flows take the first one.** That is worth stating plainly rather than quoting the better number: [`flows.md`](./flows.md) routes J-0 through the **Recipe** screen, because that is where the portion count is set and where an ingredient can be swapped. **So the drawn main path costs 18, and 10 is what it drops to for dishes that need neither.**

**The row shortcut is for the unchanged case** — the fifteen dishes a household rotates through, added at their usual count without a second thought. Tap the add control on the row, the servings sheet appears already carrying the recipe's own count, confirm.

**The trade-off, stated rather than hidden.** You commit a dish to the week without looking at it first — which would be reckless in a discovery product and is not one here, because **P-1 is defined by already knowing what they want to cook.** The recipe is still one tap away for the times you do want to check, and nothing about the row control removes that path. What it costs is one more control on every library row, on the screen that most needs to stay scannable.

**The alternative that was not taken:** collapsing *add* and *confirm* into a single tap by defaulting the servings count. Rejected — a default portion count is a guess about the one number the person is uniquely qualified to supply, and the servings decision already settled that they type it.

### The other jobs, checked against the same model

A navigation model that only serves the main job is a bad one. All of them land at two taps or fewer:

| Job | Path | Taps |
|---|---|---|
| **J-2** getting back to a dish | Library → type → tap a result | **1** |
| **J-6** the collection itself | Library | **0** |
| **J-1** keeping what I find | Library → paste → save | **2** |
| **J-3** cooking for six | Library → recipe → servings is at the top | **1** |
| **J-3** the guests cancelled — six is now four | Cook list → the count on the entry | **1**, and it reaches the grocery list |
| **J-4** walking the shop once | Grocery list → tick | **1** |
| **H-1** what is this line made of | Grocery list → tap the line | **2** |
| **E-2** fixing what the app got wrong | any flagged row → *fix ingredient* | **1 from where you already are** |
| **E-2** maintenance, rather than in the moment | Account → My ingredients | **2** |

---

## 3 · Global · contextual · deep

### Global — always reachable, one tap, never nested

- **Library**, **Cook list**, **Grocery list**, **Account** — the bar
- On Library: the **search field** and the **paste box**. Both are on the landing screen because both answer a job that starts before the person has decided where to go
- On Recipe and on every Cook list entry: the **servings control**. Not navigation, but it belongs in this list — it is the one control that must never be scrolled to, and it now appears in both places the person thinks about portions

### Contextual — appears in the flow, from the thing it belongs to

| Screen or surface | Reached from |
|---|---|
| **Recipe** | a Library row · a search result · a cook list entry · a grocery line's breakdown · a forwarded link |
| **Recipe editor** | the paste box · *new recipe* · *edit* on a recipe · a flagged row |
| **Fix ingredient** | a flagged row, wherever it appears — in the editor, on the recipe, or on a grocery line that landed in *other* |
| **Replace ingredient** | any ingredient row, on **Recipe** or in the **Recipe editor** |
| **Add to cook list** *(sheet)* | a Library row · a Recipe |
| **Line breakdown** *(disclosure)* | a grocery line |
| **Past lists, both kinds** *(section)* | the header control on Cook list and on Grocery list |
| **Export · share** *(actions)* | Grocery list · Recipe |

**The rule they all follow:** a contextual surface is reached from the object it concerns, never from a menu. There is no path to *Fix ingredient* that does not start at a row that needs fixing.

### Deep — rare, and one level below a global item

| | Path | Taps |
|---|---|---|
| **Account · settings** | the Account tab | **1** |
| **My ingredients** | Account → My ingredients | **2** |

**My ingredients is the maintenance door, not the working one.** The working path to the same object is *Fix ingredient*, one tap from the row that is wrong, and that is where nearly every edit will actually happen. The tab exists for the other case — going to look at what you have told the app, without a wrong row to lead you there.

---

## 4 · The landing screen, and one lever deliberately not pulled

**The app opens on Library.** It holds two of the three daily jobs, it is the only screen with content before anything has been planned, and it is where both J-1 and J-2 begin.

**The lever: open on the grocery list when one is in progress.** It is tempting — the shop is the hostile environment the design principles name, and it would take the shop path from one tap to zero.

**Not taken.** A landing screen that changes based on state is a landing screen the person cannot predict, and *predictable* beats *clever* on a screen used with one thumb and a trolley. The saving is a single tap against a cost paid every other time the app is opened. **It is cheap to reverse** if a real shop proves otherwise — which is the same standing the fixed aisle order has, and it belongs in the same list of bets.

---

**Where this leaves the model:** four global items — three carrying the loop and one carrying the person — one tap of navigation to the main job, nothing deeper than two, and every contextual surface hanging off the object it concerns rather than off a menu.

**Next:** [`flows.md`](./flows.md) — the main job and three related ones drawn end to end, including the states and the dead ends. Then [Traceability](#traceability), which counts what all of it actually covers.

---

# Traceability

**Date:** 5 August 2026
**Rows:** every job in [`research/jtbd.md`](./research/jtbd.md) — main, related, emotional, social. **Columns:** every screen in this document.

**A ✓ means the screen genuinely takes part in closing the job**, not that it is somewhere on the route. The Library is on the way to almost everything; it is ticked only where retrieval is part of the job itself. **Being strict is the whole point** — a generous matrix hides exactly the defects this pass exists to find.

## The matrix

| Job | LIB | EDIT | FIX | REC | SWAP | COOK | SHOP | ING | ACC | Screens |
|---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| **J-0** everything into the house in one go | ✓ | | | ✓ | ✓ | ✓ | ✓ | | | **5** |
| **J-1** keeping what I find | ✓ | ✓ | ✓ | ✓ | | | | | | **4** |
| **J-2** using what I already have | ✓ | | | ✓ | | | | | | **2** |
| **J-3** amounts for the people eating | | ✓ | ✓ | ✓ | | ✓ | ✓ | ✓ | | **6** |
| **J-4** one trip, not three laps | | | ✓ | | | ✓ | ✓ | | | **3** |
| **J-5** a household without collisions | | | | | | | | | | **0** |
| **J-6** the good version outlasting memory | ✓ | ✓ | | ✓ | ✓ | | | | | **4** |
| **E-1** committing without being trapped | | | | | | | | | | **0** |
| **E-2** careful without being technical | | ✓ | ✓ | | | | | ✓ | | **3** |
| **E-3** it stays what I chose | | | | | | | | | | **0** |
| **S-1** legible to the people I share a kitchen with | | | | | | | | | | **0** |
| **S-2** handing it to someone outside my tools | | | | | | | ✓ | | | **1** |
| **Jobs per screen** | **4** | **4** | **4** | **5** | **2** | **3** | **4** | **2** | **0** | 28 |

`LIB` Library · `EDIT` Recipe editor · `FIX` Fix ingredient · `REC` Recipe · `SWAP` Replace ingredient · `COOK` Cook list · `SHOP` Grocery list · `ING` My ingredients · `ACC` Account

**Coverage: 8 of 12 jobs have a screen. 8 of 9 screens have a job.** One empty column, four empty rows.

### A few readings before the defects

- **J-3 is the most covered job in the product**, touching six of the nine screens. That is the right shape: the three-unit rule and the portion count were named as the half of the market nobody serves, and the matrix shows the product actually built for it rather than talking about it.
- **J-2 is covered by two screens** and is **pain #1 in the entire research corpus.** Thin is not the same as wrong — search is the substance of the Library rather than a screen of its own — but it is worth knowing that the loudest documented pain rests on the narrowest surface.
- **Replace ingredient is the thinnest new screen at two jobs**, and the reason it was asked for — recalculating calories — contributes **zero**, because calories close no job. The screen earns its place on J-6 and J-0 and not on its own motive.
- **One asymmetry, checked rather than left to look like an error.** SWAP is ticked for J-0 and FIX is not, though both are optional detours off the same path. The difference is real: **a swap changes what goes into the trolley, a fix changes only the aisle a line sorts into** — which is why FIX is ticked for J-4, where the walking order *is* the job.

---

## The five blank lines, reviewed — 5 August 2026

Every empty row and column was put to a decision. **All five came back accepted.** The goal was never a matrix with no blanks for its own sake; it was a matrix with no *unexamined* blanks, and that is now the state: **zero outstanding defects, five recorded positions.**

| Blank | Verdict | Reasoning |
|---|---|---|
| **ACC** — a screen with no job | **Accepted.** Not a candidate for removal | Architecturally necessary. An account has to exist for sync and identity, and it has to be reachable. **A screen can be required by the architecture and required by no job at the same time** — that is a real category, and the matrix simply cannot express it |
| **J-5** household without collisions | **Accepted.** Household is paused | The row is the pause, showing up where it should |
| **S-1** legible to the people I share a kitchen with | **Accepted.** Same cause | — |
| **E-3** it stays what I chose | **Accepted.** Not screen-shaped | Closed by things *not* being built: no monetisation, no feed, no AI upsell, no drift toward a content platform. A promise kept by refusal is still kept, and no screen was ever going to hold it |
| **E-1** committing without being trapped | **Accepted.** **Bulk export of the whole library is not being built** | See below — this one has a cost worth recording once |

### E-1, and the cost recorded once

The recommendation was to bring full library export into Account and close the empty column and the empty row together. **It was declined: there is no bulk download of every recipe.** That is a decision, and the register's job is to state what it costs, not to argue with it.

- **The job is not deferred, it is declined.** §8.1 of the brief listed full library export as a *post-MVP obligation*; it is now a rejection. That is a change to the brief, not a scheduling note
- **E-1 scores 3 for the Data Sovereign and 2 for the primary persona**, where the research records it as a precondition for typing anything in at all — *"nobody types in sixty recipes without knowing they can leave."* The corpus already called this pain *"knowingly left on the table"*; it is now off the table
- **P-4 the Data Sovereign is permanently outside the product.** They were already pointed away by mandatory cloud accounts; this closes the other door

**What the product does let out, stated precisely, because it is not nothing:**

| | Out | How |
|---|---|---|
| A grocery list | **Yes** | Plain text, one tap — this is S-2, and it is covered |
| One recipe | **Yes** | A frozen share link, one at a time, by hand |
| The library as a whole | **No** | Nothing, by decision |

The door is not shut, it is narrow: everything can leave one item at a time, and nothing can leave at once.

---

## Where this leaves the target

| | Count | Status |
|---|---|---|
| **Empty columns** | 1 — Account | Accepted: required by the architecture, produced by no job |
| **Empty rows** | 4 — J-5, S-1, E-3, E-1 | Two are the household pause · one is not screen-shaped · one is a declined feature |
| **Outstanding defects** | **0** | Every blank has a verdict |

**The blanks stay in the matrix rather than being tidied away.** A coverage table that shows only what is covered is a marketing document; the value of this one is that four jobs and one screen are visibly unaccounted for, on purpose, with the reason attached to each.

## The hypotheses, for completeness

Not part of the matrix above, because `jtbd.md` holds them outside the main list — they rest on no external evidence. Recorded because two of them do have surfaces and two are worth watching:

| | Hypothesis | Screen | Note |
|---|---|---|---|
| **H-1** | seeing what a total is made of | **SHOP** — the line breakdown | The least evidenced job in the corpus, and the one the product's only defensible wedge is built on |
| **H-3** | the cost of entering something properly | **EDIT** | What the unrun parser bake-off would measure |
| **H-4** | the same handful of dishes, without asking | **LIB** frecency · **COOK** copy-forward | Two surfaces for a premise that is the brief's own assertion |
| **H-2** | being sure of what is at home | — | No screen. Went with the pantry |
| **H-5** | the pile I meant to cook | — | No screen, and none proposed. The behaviour is evidenced; the feeling behind it is not |
| **H-6** | the order matching the shop I am standing in | — | No screen by decision — one fixed walking order |
| **H-7** | measures I think in | — | No screen. Metric only, locked |

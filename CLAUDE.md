# Cooksy — Product Brief

> A digital recipe book that turns what you want to cook into exactly what you need to buy.

**Status:** brief only. Nothing is built yet. No tech stack has been chosen — that decision is deliberately deferred until the product is settled.

**Scope note:** what were previously staged as v1 and v2 are now a single combined scope. URL import, pantry tracking and household sharing are in. See §11 for the build order, which still matters even though the scope doesn't phase.

---

## 1. The idea

Cooksy stores your recipes, lets you dial the number of portions up or down, and turns any set of planned meals into a single merged grocery list — deduplicated, quantity-summed, aisle-grouped, and minus whatever you already have at home.

The whole product exists to serve one loop:

**Save a recipe → set the portions → plan a few meals → get one shopping list.**

Everything in the product either serves that loop or is cut.

## 2. Who it's for

**Cooking lovers who are also optimisers.** People who genuinely enjoy cooking but resent the overhead around it: retyping recipes, doing portion maths in their head, walking the supermarket three times because onions were written on three different lines.

They are not looking for inspiration or a social feed. They already know what they want to cook. They want the logistics to disappear.

Two things follow from this:
- **The user is the source of recipes, not the app.** No content library, no editorial, no discovery feed.
- **Precision earns trust.** An optimiser will abandon the product the moment the maths is wrong. Quantity handling is the feature, not a detail.

## 3. Platform

Mobile-first, desktop adapted later.

Mobile is where the product is *used* — in the kitchen with the recipe open, in the shop with the list open. Desktop is where it's *administered* — bulk-adding recipes, planning the week. Design mobile properly first; the desktop layout is a later adaptation of the same product, not a separate one.

## 4. Locked decisions

| Question | Decision |
|---|---|
| Units | **Metric only in the ingredient list — grams, millilitres, pieces. Nothing else.** |
| Recipe input | Paste text → auto-parse, **import from URL**, **and capture from the OS share sheet**. All three land on the same editable review screen. |
| Data & accounts | Cloud accounts from day one, synced across devices |
| Offline | **The recipe and the grocery list are fully usable with no connection.** Local-first: reads always work, writes queue and merge on reconnect. |
| Grocery list | Merge duplicate ingredients, group by store aisle, subtract pantry staples visibly |
| History | Past weeks and past grocery lists are kept and browsable, never overwritten |
| Calories | Auto-estimated. **kcal per 100 g** (a fixed property of the recipe) plus **kcal per portion**, where portion size in grams is set by the user |
| Pantry | Two tiers — zero-maintenance **staples**, plus opt-in **tracked quantities** |
| Household | Shared library, shared plan, live shared grocery list. Flat permissions, no roles. |
| Sharing outward | Export list as text; share a recipe via read-only link |
| Meal planning | Weekly planner, with slots assignable to specific household members |
| Purpose | Personal tool / portfolio piece — product and UX led, light on business case |

---

## 5. Feature spec

### 5.1 Units — metric, strictly

**The ingredient list permits exactly three units: `g`, `ml`, `pcs`.** No tablespoons, teaspoons, cups, ounces or pounds ever appear in a structured ingredient row.

Free-text method steps are exempt — "stir in a spoonful of mustard" is fine in prose. The constraint applies to the ingredient list, because that is what scales, merges and gets counted.

**Why this matters more than it looks:** volumetric spoons and cups are ingredient-dependent by weight. A cup of flour is ~120 g; a cup of sugar is ~200 g. Banning them removes an entire class of silent error from scaling, merging and calorie estimation. It is the single highest-leverage constraint in the brief.

**The cost lands on the parser.** Real-world recipes are full of cups and spoons, so conversion happens at import:

- **Volume → volume** for liquids, which is ingredient-independent and always safe: `1 tsp` → `5 ml`, `1 tbsp` → `15 ml`, `1 cup` → `240 ml`
- **Volume → mass** for solids, which requires the canonical ingredient's density: `1 cup flour` → `120 g`
- **Imperial mass → metric**: `1 oz` → `28 g`, `1 lb` → `454 g`
- **Vague amounts** — "a splash", "a handful" — are not guessed. They are surfaced in review for the user to quantify, or marked non-scalable and passed through as text.

**When density is unknown, never guess.** Flag the row in review and ask the user for the gram weight. One wrong density silently corrupts the recipe, the shopping list and the calorie estimate at once.

**`pcs` survives the purge deliberately.** "3 eggs" is how people cook and how eggs are sold; forcing it to "150 g" would be worse on every screen. Each canonical ingredient carries an average unit weight so `pcs` can still be converted to grams for the internal weight and calorie maths.

### 5.2 Recipe capture — share sheet, paste and URL import

Three entry paths, converging on one screen.

**Share sheet — the primary path.** Cooksy registers as a share target on iOS and Android, accepting a URL or a block of text from any app: the browser, Instagram, a messenger, a note. The user is reading a recipe, hits share, picks Cooksy, and lands directly on the review screen. No app switch, no copy-paste, no hunting for a field.

This is how recipes are actually captured. A URL field inside the app asks the user to leave where they are, open Cooksy, find the right screen and paste — four steps for what should be one, and the reason so many recipes never get saved at all. Everything downstream is worthless if capture is slower than screenshotting the page, so **the share extension is a launch requirement, not an enhancement.** It runs the same parse and the same review screen as every other path; only the entry point differs.

**Paste.** The user pastes a raw recipe blob from anywhere — a blog, a message, a note. Cooksy parses it into structure. This remains the fallback when the share sheet isn't available (desktop, unusual apps) and the path for recipes that exist only on paper or in someone's head.

**Import from URL.** The user pastes a link. A server-side fetcher retrieves the page and reads its `schema.org/Recipe` markup, which most food sites publish and which already gives clean ingredients, steps, servings and often a photo. When markup is absent or broken, Cooksy extracts the page's readable text and falls back to the paste parser rather than failing outright. The fetch is server-side because the browser can't do it — and since accounts already require a backend, it has somewhere to live.

URL import is the higher-quality path but not the safer one: structured markup is frequently in cups and ounces, so §5.1 conversion applies identically. Cleaner input, same density problem.

**Parser must handle:**
- Quantities as decimals, fractions and unicode fractions — `1.5`, `1/2`, `½`
- Ranges — `2–3 onions` (take the lower bound, keep the range visible in review)
- Unit before or after the amount, abbreviated or spelled out — `200g`, `200 g`, `200 grams`
- Non-metric units, converted per §5.1
- Count ingredients with no unit — `3 eggs` → `3 pcs`
- Trailing preparation notes — `2 onions, finely chopped` → qty `2`, unit `pcs`, item `onions`, note `finely chopped`
- Ingredients with no quantity at all — `salt to taste`
- Splitting the ingredient block from the method block
- **Ingredient group headings** — `For the dough:` / `For the sauce:` — detected and preserved per §5.2.1

**The review step is mandatory and fully editable, on every path.** Every parsed row is shown, and the user can change **the amount, the unit, the ingredient name, the note, and the non-scalable flag** — and add or delete rows outright. Anything low-confidence is visibly flagged and sorted to the top: unrecognised ingredients, inferred unit conversions, missing densities, vague amounts. Nothing saves silently, and a clean URL import is no exception.

This is the single most important screen in the product. A wrong parse doesn't just corrupt one recipe — it poisons the scaling, the grocery aggregation and the calorie estimate downstream. Make correcting a row faster than typing it from scratch, and the parser has done its job even when it's wrong.

**Recipe fields:** title, optional photo, base servings, default portion size (g), prep + cook time, tags, ingredient rows, optional ingredient groups, numbered steps, source (URL or free text), optional finished-dish weight.

### 5.2.1 Ingredient groups — optional, and recipe-local

A large share of real recipes arrange their ingredients under headings: *for the dough*, *for the sauce*, *for the topping*. A flat list loses information the cook needs at the counter, so Cooksy keeps them.

**Groups are optional.** A recipe with no headings has one implicit group and shows a plain list — no empty scaffolding, no "Ungrouped" label, nothing to configure. Groups appear only when the recipe has them.

**They are detected at import and editable at review.** The parser recognises heading lines in the ingredient block and assigns the rows beneath them. In review the user can rename a group, move a row between groups, add or remove a group, or flatten the recipe entirely. A misdetected heading is a wrong parse like any other and is flagged the same way.

**They are display structure, nothing more.** Groups have no effect on scaling, the weight model, calories or merging — every ingredient row belongs to the recipe first and its group second. A group is a label on a row, not a container.

**The grocery list never shows them.** The list is aggregated by aisle across every planned recipe (§5.9); "for the sauce" is meaningless once four recipes are merged and you're standing in the produce section. The connection back to structure is the existing audit trail: tapping a grocery line reveals which recipes it came from, and in what amounts. That is the switch from aggregated view to recipe view — one already-specified interaction, not a second mode.

The rule in one line: **grouped inside the recipe, flat inside the list.**

### 5.3 The weight model

Everything downstream — scaling, portions, calories, yield — derives from one idea: **a recipe has a total weight.**

```
total raw weight  =  Σ ingredient weights in grams
                     (ml → g via density, pcs → g via average unit weight)

yield weight      =  finished weight if the user entered one,
                     otherwise total raw weight

total kcal        =  Σ ingredient kcal

kcal per 100 g    =  total kcal ÷ yield weight × 100
portion size (g)  =  set by the user; defaults to yield weight ÷ base servings
kcal per portion  =  kcal per 100 g × portion size ÷ 100
servings          =  yield weight ÷ portion size
```

Two properties of this model do a lot of work:

- **kcal per 100 g is scale-invariant.** Doubling a recipe doesn't change it. It is an honest, stable description of the dish itself — the number worth putting on the recipe card.
- **Servings and portion size are two views of the same quantity**, bound together. Move the servings stepper and portion size recalculates; type a portion size and the serving count recalculates. Neither is more "real" than the other, and the user works in whichever they think in.

**The finished-weight field is optional but valuable.** Cooking drives off water, so a stew's raw weight overstates its yield and understates its kcal/100 g. If the user weighs the pot once and enters the number, the estimate becomes genuinely accurate. If they don't, Cooksy uses raw weight and says so.

### 5.4 Portion scaling

The recipe screen has a servings stepper pinned at the top, and the entire ingredient list rescales live as it moves. No "recalculate" button, no modal, no separate mode.

Scaling factor = `target servings ÷ base servings`.

**Rules that make scaling trustworthy:**
- **Round by magnitude.** Under 100 g/ml round to the nearest 5; above, to the nearest 10. Never show `133.33 g`.
- **Flag lumpy count ingredients.** Scaling 3 eggs by 1.5 gives 4.5 eggs. Show `4–5 pcs`, not a fraction of an egg.
- **Some ingredients don't scale.** `salt to taste`, `1 bay leaf`, `oil for frying`. Marked non-scalable at review and passed through untouched.
- **Never mutate the stored recipe.** The base recipe is immutable; scaling is a view over it. The user can always get back to the original.
- The chosen serving count is what carries into the meal plan and the grocery list.

### 5.5 Ingredient normalisation — the engine

This is invisible to the user, and now that pantry and household are in scope, **four features depend on it.**

Each parsed ingredient row is matched to a **canonical ingredient** — one record for "onion" that `onion`, `onions`, `yellow onion` and `1 large onion` all resolve to. The canonical ingredient carries:

- a display name and its aliases
- an **aisle category** (produce · meat & fish · dairy & eggs · bakery · pantry & dry goods · frozen · herbs & spices · drinks · household · other)
- **kcal per 100 g** for the calorie estimate
- **density (g per ml)**, so volumetric input can be converted to mass
- **average unit weight (g per pc)**, so `pcs` can enter the weight maths

It is the join key for the grocery merge, the basis of the calorie estimate, the vocabulary of the pantry, and what lets two household members' recipes combine into one list. Every hour spent here pays out four times.

**Two ingredients merge only if the canonical ingredient matches *and* the units are compatible.** `2 pcs garlic` and `5 g garlic powder` are different ingredients and must never be summed. When the same ingredient appears in incompatible units across recipes (`200 g tomatoes` + `3 pcs tomatoes`), show both parts on one line rather than guessing: `tomatoes — 200 g + 3 pcs`.

### 5.6 Calories

**Cooksy is not a diet tracker.** No macros, no goals, no logging what was actually eaten, no streaks. It reports what a dish is, so the user can decide.

Each recipe shows two numbers:

- **kcal per 100 g** — the honest, portion-independent description of the dish
- **kcal per portion** — derived from the user's chosen portion size in grams

Rules:
- Always labelled an estimate, never with false precision — `~640 kcal`, not `638 kcal`
- Manually overridable per recipe; the override wins
- Degrades gracefully: if some ingredients don't resolve to nutrition data, show the estimate with a note on how many were unmatched, rather than hiding the number or quietly showing a wrong one

### 5.7 Weekly meal planner

A seven-day view. Each day has **breakfast / lunch / dinner** slots, plus a free "extra" slot for batch cooking or snacks.

- Assign a saved recipe to a slot and set the **portion size in grams** for that specific slot — the same dish can be a 200 g lunch and a 350 g dinner
- **Assign the slot to household members** — "everyone", or specific people. In a solo account this control is hidden entirely and everything is implicitly yours.
- The same recipe can appear on several days (cook once, eat twice — an optimiser move worth supporting explicitly)
- Each day shows its total estimated calories
- The week header shows the **average daily calories** across the planned week
- One primary action: **generate grocery list for this week**

**Member assignment is what keeps calories and groceries coherent once a plan is shared.** It resolves two things at once: the grocery list multiplies portions by the number of people eating, and the calorie average is computed per person from the slots they're actually in. Without it, a shared plan makes one of those two numbers wrong — either you shop for one and cook for three, or your "daily average" silently includes your partner's dinner.

The planner is deliberately a week, not a month. Groceries are bought weekly; that's the natural unit.

**Weeks are kept, not consumed.** Navigating back through past weeks shows exactly what was planned and eaten, with the calorie averages still attached. Nothing is archived, deleted or rolled up. Two things fall out of this for free: a past week can be duplicated forward into an empty one — the highest-value shortcut in the whole planner, since households rotate through the same fifteen dishes — and "what did we actually cook in March" is answerable. Forward weeks are equally reachable, so a plan can be built ahead.

### 5.8 Pantry

The goal: don't buy oregano you already own. The risk: pantry features die because nobody maintains an accurate inventory of their kitchen. So the pantry is split into two tiers with very different demands on the user.

**Staples — zero maintenance, the default.** A simple list of things the user always keeps at home: salt, pepper, olive oil, flour, sugar, common spices. No quantities, just presence. These are suppressed from the grocery list by default. Setup is a one-time pass through a suggested starter list, and the set barely changes after that.

**Tracked items — opt-in, quantified.** For the smaller set worth actually counting, the user can store a quantity in `g`/`ml`/`pcs`. Generating a list subtracts what's on hand and asks only for the shortfall: 500 g rice at home, 700 g planned, list says 200 g. Checking items off after a shop offers to add them back.

Tracked quantities drift out of date the moment you cook without telling the app, and no design fixes that. What makes it survivable is that **drift is never silent** — pantry state changes what the list *suggests*, never what it *contains without saying so*.

**Two rules protect trust:**
1. **Subtraction is always visible.** Suppressed and reduced items appear in a collapsed *"assumed you have"* section at the foot of the list, with a one-tap "actually, I'm out" that promotes the item back to full quantity. An ingredient never vanishes without a trace — getting home without garlic because the app quietly assumed is the kind of failure users don't forgive.
2. **The pantry never blocks anything.** Skip it entirely and Cooksy behaves exactly as if the pantry were empty.

The pantry speaks in canonical ingredients (§5.5), so it shares a vocabulary with every recipe automatically.

### 5.9 Grocery list

Generated from either an ad-hoc selection of recipes or a planned week.

- Ingredients merged across all selected recipes at their planned quantities, multiplied by the people assigned to each slot
- Pantry staples and stocked quantities subtracted, visibly, per §5.8
- Grouped by aisle category, in a sensible walking order through a store
- Each line is tappable to check off; checked items dim and sink to the bottom of their group
- Tapping a line reveals **which recipes it came from**, in what amounts, and **what the pantry deducted** — merged totals must always be auditable, or the user won't trust them
- Manual lines can be added freely (bin bags, coffee)
- Lists persist, so an in-progress shop survives closing the app
- In a household, the list is **live and shared** — two people in different aisles see each other's checkoffs
- **Export as plain text** — one tap, formatted for pasting into a messenger or notes app, for whoever isn't a Cooksy user

**List lifecycle — generating never destroys.** A list is a dated document, not a scratchpad that the next generation overwrites.

- Generating a list while one is in progress **never silently replaces it.** Cooksy asks: *add these items to the current list*, or *start a new one and keep this*. Merging into a live list re-runs the merge and pantry maths across the combined set, so quantities stay correct rather than being appended as duplicate lines.
- **Past lists are kept and browsable**, each stamped with its date and what generated it — a planned week, or an ad-hoc selection of recipes. What was bought and what stayed unchecked is preserved as it was.
- **A past list can be regenerated forward** — "shop this again" rebuilds it against today's pantry state rather than the old one, since the point of a repeat is a fresh subtraction.
- The list and the plan that produced it stay linked in both directions: from a week you can reach its list, from a list you can reach its week.

Cost is negligible — a grocery list is a few hundred bytes — and the payoff is a household that can answer "did we already buy coffee this month" without remembering.

**Offline is the default assumption for this screen.** See §5.12: the shop is where signal dies, and a list that needs a network to be ticked off is not a list.

### 5.10 Household sharing

A household is a small group — realistically two to four people — sharing one recipe library, one meal plan, and one live grocery list.

- **Invite by link.** No org chart, no admin roles, no per-item permissions. Everyone in a household can do everything. Households are built on trust that already exists offline; modelling permissions would add real complexity to solve a problem these users don't have.
- **The grocery list syncs live.** This is the feature people will actually feel — two people splitting a shop, watching items disappear in real time. It's also the only screen where latency is genuinely visible.
- **Recipes are last-write-wins**, with a quiet "edited by Ana, 2 days ago" note. Simultaneous edits to the same recipe by two housemates are rare enough that a merge UI would cost more than it saves.
- **Checkoffs are conflict-free by construction** — checking an item is monotonic, so two people checking the same thing converge on the same answer with no reconciliation.
- **A solo user must never see any of it.** No household UI, no member pickers, no "share" affordances until a household exists. Adding sharing must not tax the person who cooks alone.

Personal preferences stay personal: the pantry is per-household (it's a shared kitchen), but the calorie average is per-person (it's a shared kitchen, not a shared body).

### 5.11 Sharing outward

- **Grocery list → text export.** For the person at the shop who doesn't use Cooksy.
- **Recipe → read-only link.** Opens a clean public view; a Cooksy user can save it to their own library in one tap.

Distinct from §5.10: household sharing is continuous and collaborative, outward sharing is a one-time snapshot to someone outside.

### 5.12 Offline

Cloud accounts from day one (§4) describe where data *lives*, not what the app requires to *work*. Cooksy is **local-first**: the device holds a full copy, the app reads from it, and the network is a background synchroniser that the user never waits on.

This is not a technical nicety. §7.4 already names the shop and the kitchen as hostile environments, and the most common hostility is no signal — supermarkets are concrete boxes, often below ground. **A grocery list that needs a network to be ticked off is not a grocery list.** The same holds standing at the hob with a recipe open.

**What must work with the radio off:**

- Opening any saved recipe, including its photo, and moving the servings stepper (§5.4 is pure arithmetic over local data — it must never round-trip)
- Reading the grocery list, checking items off, adding manual lines, editing quantities
- Reading and editing the week plan
- Reading and editing the pantry

**What may require a connection**, because it fundamentally cannot be done locally: URL import (the fetch is server-side, §5.2), the read-only recipe link (§5.11), joining a household, and the *live* half of live sharing.

**Rules:**

1. **Writes queue and merge; they never fail and never block.** An action taken offline is applied locally at once and reconciled on reconnect. Checkoffs are already conflict-free by construction (§5.10), which is what makes the hard case — two people shopping, one of them offline — resolve correctly with no reconciliation UI.
2. **Never show a spinner where a local read would do.** If the answer is on the device, render it immediately and reconcile behind the scenes.
3. **Sync state is visible but quiet.** A small, honest indicator when something is pending — consistent with §7.3, no silent wrongness — never a modal, never a blocking error, never a lost edit.
4. **Offline degrades one path, not the app.** Failing to fetch a URL says so and offers the paste box; it doesn't strand the user on a dead screen.

Because this shapes the storage layer, sync protocol and every write path, it has to be settled before the data model does — see §11.

---

## 6. Screens (mobile)

**Three primary tabs**, because three things are used daily:

1. **Library** — recipe grid/list, search, tag filters, prominent add button. The home screen.
2. **Week plan** — seven days, meal slots with per-slot portion size and member assignment, per-day calories, weekly average, generate-list action. Swipe or step back and forward through past and future weeks; duplicate a past week forward.
3. **Grocery list** — aisle-grouped merged list, checkoff, "assumed you have" section, add manual item, export. Past lists reachable from the header, each dated and linked to the week that produced it.

**Reached contextually, not from the tab bar:**

4. **Recipe** — photo, servings stepper pinned at top, live-scaling ingredients grouped where the recipe has groups, steps, kcal/100 g and kcal/portion, actions (add to plan, add to list, share).
5. **Add recipe** — **arrived at from the share sheet**, or from a paste box *or* URL field inside the app → parse → **review & fix** → save. Manual entry as a fallback path. Neither URL import nor share-sheet capture adds a screen: all three are inputs to the same flow, and the share sheet simply skips straight to review.
6. **Pantry** — staples list and tracked quantities. Entered from the "assumed you have" section of the grocery list, where the user is already thinking about it, and from settings.
7. **Settings** — account, household members and invites, units, export.

Pantry is deliberately kept out of the tab bar: it's configured once and touched rarely, and a tab bar should reflect frequency of use, not feature count. The contextual entry point from the grocery list is where the thought actually occurs.

## 7. Design principles

1. **The servings stepper is the hero.** The moment a user drags portions from 4 to 6 and watches every quantity reflow instantly is the moment the product sells itself. It must feel immediate and physical.
2. **Merged numbers are always auditable.** Any aggregate — a grocery line, a calorie total, a pantry deduction — can be opened to see what it's made of. Optimisers verify before they trust.
3. **Honest estimates over confident guesses.** Where the app is unsure (parse confidence, unknown density, calorie coverage, stale pantry counts) it says so plainly and asks. Silent wrongness is the only unrecoverable failure.
4. **Kitchen and shop are hostile environments.** Wet hands, one thumb, bad light, a trolley in the other hand, and no signal in the basement of the supermarket. Large tap targets, high contrast, no precision gestures, no timeouts, and nothing that waits on a network (§5.12).
5. **The user's recipe is sacred.** Cooksy stores what they confirmed at review. Scaling, pantry logic and suggestions are layers over it, never edits to it.
6. **Solo use must not pay for shared use.** Every household feature is invisible until a household exists.

## 8. Explicitly out of scope

These are not deferred — they're rejected, because they'd make Cooksy a different product:

Recipe discovery or a public feed · social features, ratings, comments · macro and micronutrient tracking or diet goals · supermarket price lookup and online ordering · photo/OCR import of physical cookbooks · package-size reconciliation (telling the user that 250 ml cream means buying a 500 ml carton — country-specific product data for marginal gain) · cooking mode with timers · monetisation.

The first four would pull Cooksy toward being a social network, a diet tracker, or a shopping service. It is a tool for people who already know what they want to cook.

## 9. What good looks like

Since this is a personal tool and portfolio piece, success is qualitative:

- A real week's cooking gets planned in Cooksy and the resulting list is actually taken to a shop
- Scaled quantities are correct enough that they're never double-checked by hand after the first few uses
- Importing a recipe from a blog is faster than retyping it — including the time spent fixing the parse
- The merged list is genuinely shorter than the sum of its recipes, and the trip through the store is one pass
- Nothing gets bought that was already in the cupboard — and nothing gets missed because the app assumed it was

## 10. Open question

**One remains: where the canonical ingredient data comes from.**

Cooksy needs a database of ingredients carrying four attributes each — kcal/100 g, density, average unit weight, and aisle category. Nutrition databases exist; density and unit weight are patchier, and aisle category is essentially absent from all of them.

Candidate approaches, unresolved:
- Seed a curated set of the few hundred ingredients that cover most home cooking, and let unmatched ingredients fall back to the review screen where the user supplies the number once
- Build on an open nutrition dataset and layer the missing attributes on top by hand
- Derive it on demand and cache what's been resolved

Whatever the source, the fallback path is fixed: **an unmatched ingredient never blocks saving a recipe.** It appears flagged in review, the user can fill in what they know, and the calorie estimate reports its own coverage honestly.

*Resolved earlier:* recipes with a yield rather than portions (a loaf, a jar of sauce) needed no special handling — the weight model in §5.3 covers them natively, since an 800 g jar of sauce at 50 g portions is the same arithmetic as a stew at 350 g portions.

## 11. Build order

Scope is combined, but the work still has a required sequence — three features now depend on foundations that have to be right first.

0. **Local-first storage and the sync model (§5.12).** Not a feature and not a screen, which is exactly why it has to come first: it is the shape every write in the product is built on. Retrofitting offline onto a request-response app means rewriting every write path, and step 8 depends on getting it right.
1. **Canonical ingredients + the weight model.** Nothing else is correct until this is. Four features join on it.
2. **Recipe capture → review → save**, paste path first. Prove the parse-and-correct loop before adding a second input to it. Ingredient groups (§5.2.1) belong here, in the parser and the review screen, not bolted on later.
3. **Portion scaling and calories.** The hero interaction, and it's cheap once §5.3 exists.
4. **Grocery list — merge and aisle grouping.** This closes the core loop. **Cook a real week off it before going further.**
5. **Weekly planner.** Depends on a working list to be worth anything. History (§5.7, §5.9) comes free if weeks and lists are dated records from the start — so make them dated records from the start.
6. **URL import, then the share sheet.** Both are additive to a flow that already works. Import first because the share extension hands its payload to the same parser; ship the extension as soon as that parser is real, since it is what makes capture fast enough to use daily.
7. **Pantry.** Modifies the list, so the list must be trusted before it starts subtracting from it.
8. **Household sharing.** Touches the data model everywhere and is the only piece requiring live sync — worth doing last, when the shape of the data has stopped moving. Step 0 is what makes it tractable rather than a rewrite.

Steps 1–4 are the product. Steps 5–8 make it better and are, individually, each smaller than what precedes them. If attention runs out, it should run out at the bottom of this list, not the middle.

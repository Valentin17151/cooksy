# Jobs to be done

**Date:** 29 July 2026
**Derived from:** [`personas.md`](./personas.md) and the corpus it rests on — [`competitive-landscape.md`](./competitive-landscape.md) · [`comparison.md`](./comparison.md) · [`ux-patterns.md`](./ux-patterns.md) · [`benchmark-retrieval.md`](./benchmark-retrieval.md) · [`summary.md`](./summary.md) · 20 screens in [`screens/`](./screens/)

**Format:** *When [situation], I want [motivation], so that [outcome].*

---

## The bar for the main list

The corpus contains **no interviews, no teardowns, no user reviews** ([`summary.md` §5.9](./summary.md#5-unverified)). Every job here is inferred. The question is only *from what*, so the admission threshold is explicit:

| | Admitted to the main list | Sent to [Hypotheses](#hypotheses--not-yet-earned-a-place) |
|---|---|---|
| **Rests on** | At least one **external** datum — a product's own marketing, a captured screen, or a pattern across several products | Only the research's or the brief's **own assertion**, or nothing at all |

The distinction matters because it is exactly where the corpus is weakest. A vendor charging money for something is evidence that someone buys it. The brief asserting that an optimiser feels something is not.

**Evidence classes**, carried from [`personas.md`](./personas.md): *(vendor copy)* · *(screen)* · *(correlation)* · *(assertion)* · **[?]** no data.

---

## 1 · The main job

> ### J-0
> **When** I have decided what we are eating over the next few days,
> **I want** to get everything into the house in one go, without doing the arithmetic or the remembering myself,
> **so that** the week I planned is the week we actually cook.
>
> **Українською:** *Коли я вирішив, що ми їстимемо найближчі кілька днів, я хочу зібрати все потрібне за один похід і не рахувати та не пригадувати все сам, щоб тиждень, який я спланував, і був тижнем, який ми справді зготували.*

**Persona:** P-1 the Systematic Optimiser — with P-2 riding on the same job once more than one person is fed.

**Grew from:**

- **The meta-pain, arriving from three unrelated tiers** — *"saving is not cooking."* Instagram/TikTok: *"capture is effortless; retrieval is hopeless."* Apple Notes/Notion: *"most 'I'll organise it later' recipes die here."* Cookpad/Pinterest: *"save rates are vast, cook-through rates are dismal."* *(correlation)* — [`competitive-landscape.md` §The meta-pain](./competitive-landscape.md#the-meta-pain-saving-is-not-cooking)
- **Where the pain actually lands:** *"four days later — at 6pm in a kitchen, or standing in aisle three — and almost nobody is there for it."* The whole market competes at the moment of saving. *(correlation)* — same source
- **The category sells this exact transformation.** Plan to Eat: *"Pick your meals, and we'll automatically build your grocery list."* Paprika merges ingredients and sorts them by aisle. *(vendor copy)* — [`comparison.md` tier 1](./comparison.md#tier-1--hard) · screens [t1-plan-to-eat.png](./screens/t1-plan-to-eat.png), [t1-paprika.png](./screens/t1-paprika.png)
- **Four of the five success criteria in §9 of the brief describe this one job**, not the collection that feeds it — a real week taken to a shop, one pass through the store, nothing bought that was already owned, nothing missed because the app assumed.

---

## 2 · Related jobs — the path to J-0

Six. Five are steps the main job cannot skip; the sixth (J-6) is the one the others accumulate into.

> ### J-1 · Keeping what I find
> **When** something I want to cook goes past me — in a video, on a blog, in a message from a friend —
> **I want** to keep it in the seconds before it is gone, in a form that still makes sense three weeks later,
> **so that** finding it again is never harder than finding it the first time.
>
> **Українською:** *Коли повз мене проходить те, що я хочу зготувати — у відео, в блозі, у повідомленні від друга, — я хочу зберегти це за ті кілька секунд, поки воно не зникло, і так, щоб через три тижні воно ще мало сенс, щоб знайти це вдруге було не важче, ніж знайти вперше.*

**Persona:** P-3 the Reel Hoarder, primary. P-1 secondary.

**Grew from:**
- **114M reels under `#recipe` on one platform alone** *(screen)* — [t2-instagram-recipe-tag.png](./screens/t2-instagram-recipe-tag.png), [`comparison.md` tier 2](./comparison.md#tier-2--soft)
- **What a save actually is there:** a bookmark on content you do not own and cannot export — *"no search, no export, no quantities; content can vanish"* *(correlation)* — [`comparison.md` tier 2](./comparison.md#tier-2--soft)
- **All five hard competitors market this above everything else** — *"save from any website"*, *"from wherever you find them."* Mela goes furthest, shipping live detection in-browser, RSS, an OCR scanner for physical books and import from video descriptions. *(vendor copy)* — [`comparison.md` pattern 1](./comparison.md#common-market-patterns), [tier 3](./comparison.md#tier-3--aspirational) · [t3-mela.png](./screens/t3-mela.png)

---

> ### J-2 · Getting something out of what I already have
> **When** something in the fridge turns tomorrow and I cannot remember what I made with it last time,
> **I want** to get back to the dish I already know works,
> **so that** it ends up in a pan rather than a bin.
>
> **Українською:** *Коли те, що лежить у холодильнику, завтра вже зіпсується, а я не пам'ятаю, що готував із цим минулого разу, я хочу повернутися до страви, яка в мене вже виходила, щоб воно опинилося в каструлі, а не у смітнику.*

**Persona:** P-1.

**Grew from:**
- **Pain #1 in the whole corpus:** *"the recipe is saved and cannot be reached… storage is solved everywhere; usable storage nowhere."* *(correlation)* — [`competitive-landscape.md` pain 1](./competitive-landscape.md#seven-structural-pains)
- **People pay for exactly this against collections they already own.** Eat Your Books is a subscription business built on a library you own and cannot search, indexed by humans book by book. *(vendor copy)* — [`benchmark-retrieval.md` §2](./benchmark-retrieval.md#2-the-five-products)
- **And at consumer scale:** SuperCook, built entirely on cooking from what you have, holds **4.8★ across 22K ratings**; Cookpad runs ingredient-first search for 100M users across 23 countries. *(vendor copy)* — [`benchmark-retrieval.md` §2 and Sources](./benchmark-retrieval.md)

---

> ### J-3 · Cooking for the number of people actually eating
> **When** there are six of us at the table and the dish was written for four,
> **I want** the amounts to already be right without me doing sums in my head,
> **so that** I neither run short nor throw half of it away.
>
> **Українською:** *Коли нас за столом шестеро, а страва розрахована на чотирьох, я хочу, щоб кількості вже були правильні й мені не довелося рахувати в голові, щоб і не забракло, і половина не пішла у смітник.*

**Persona:** P-1.

**Grew from:**
- **A competitor sells this as a headline capability** — Crouton scales by servings *or per individual ingredient* *(vendor copy)* — [`comparison.md` tier 3](./comparison.md#tier-3--aspirational) · [t3-crouton.png](./screens/t3-crouton.png)
- **The mess it is done against is documented across all fifteen:** *"everyone converts units; nobody constrains them."* Crouton advertises metric/imperial conversion as a feature, i.e. deliberately preserves both; Tandoor makes conversions user-editable. A cup of flour and a cup of sugar differ by roughly 80 g and every product keeps that alive. *(correlation)* — [`competitive-landscape.md` pain 6](./competitive-landscape.md#seven-structural-pains), [`comparison.md` D-5](./comparison.md#key-differences)

---

> ### J-4 · One trip instead of three laps
> **When** I am standing at the entrance to the shop with several meals' worth to buy,
> **I want** to walk it once, in the order the shop is actually laid out,
> **so that** I am not doubling back for onions I already walked past.
>
> **Українською:** *Коли я стою на вході в магазин, а купити треба одразу на кілька страв, я хочу пройти його один раз, у тому порядку, як він насправді розкладений, щоб не вертатися по цибулю, повз яку я вже пройшов.*

**Persona:** P-1, with P-2 once the trip is split between people.

**Grew from:**
- **This is the category's central marketed mechanism.** Paprika: lists that *"automatically combine ingredients and sort them by aisle."* AnyList: automatic category grouping. Tandoor: list auto-sorted by supermarket. *(vendor copy)* — [`comparison.md` tier 1–2](./comparison.md#tier-1--hard) · [t2-anylist.png](./screens/t2-anylist.png)
- **Ordering it to the walk is the category default, not one product's quirk** — Paprika ships custom aisle organisation, Plan to Eat user-reorderable categories and per-store lists, AnyList category assignment *"essentially always right."* Established by a correction to the desk research, applied at source. *(vendor copy + correlation)* — [`comparison.md` §Corrections](./comparison.md#corrections-to-competitive-landscapemd--all-applied-21-july-2026)

---

> ### J-5 · Feeding a household without collisions
> **When** two of us are out buying for the same few days at the same time,
> **I want** us both watching the same picture change as it changes,
> **so that** nothing gets bought twice, and nothing gets left behind because each of us assumed the other had it.
>
> **Українською:** *Коли ми вдвох закуповуємось на ті самі кілька днів одночасно, я хочу, щоб ми обидва бачили, як змінюється одна й та сама картина, щоб нічого не купилося двічі й нічого не лишилося тому, що кожен подумав, ніби це взяв інший.*

**Persona:** P-2 the Household Logistics Lead.

**Grew from:**
- **Table stakes, and priced at almost nothing** — AnyList charges **$5/yr more for a whole household than one person**; Crouton ships it through Family Sharing; Fond sells workspaces for up to ten. Paprika's total absence of it is now the outlier. *(vendor copy + correlation)* — [`comparison.md` pattern 3](./comparison.md#common-market-patterns) · [t3-anylist-complete-pricing.png](./screens/t3-anylist-complete-pricing.png)
- **The promise being sold, verbatim:** *"Any changes made to a shared list will show up instantly to everyone sharing the list."* *(vendor copy)* — [`comparison.md` tier 2](./comparison.md#tier-2--soft)
- **Two people mid-shop in two different aisles** is a named audience in its own right. *(vendor copy)* — [`comparison.md` tier 3](./comparison.md#tier-3--aspirational)

---

> ### J-6 · Making the good version outlast my memory of it
> **When** a dish finally comes out right — my version of it, on the third attempt —
> **I want** that version kept somewhere that is properly mine, in the state I actually cook it in,
> **so that** in five years I am not rebuilding from memory what I had already worked out.
>
> **Українською:** *Коли страва нарешті виходить така, як треба, — моя версія, з третьої спроби, — я хочу, щоб саме ця версія зберігалася там, де вона справді моя, і в тому вигляді, в якому я її насправді готую, щоб через п'ять років не відновлювати з пам'яті те, що я вже колись довів до пуття.*

**Persona:** P-1 primary. P-4 on the *"properly mine"* clause, which is where this job meets E-1. P-3 by its absence — a pile of saved links never becomes this, which is the whole of their problem.

**Grew from:**
- **For three of the fifteen, the collection is the centre of gravity** — Paprika, Mela and Crouton are built around the library, with everything else derived from it. Paprika's product base, stated plainly: *"Recipe library, with planner and list derived from it."* *(correlation + vendor copy)* — [`comparison.md` D-3](./comparison.md#key-differences), [tier 1](./comparison.md#tier-1--hard)
- **One product is sold as this job and almost nothing else:** *"A home for your favourite recipes, from wherever you find them."* *(vendor copy)* — [`comparison.md` tier 3](./comparison.md#tier-3--aspirational) · [t3-crouton.png](./screens/t3-crouton.png)
- **Two vendors identify their audience by the collection itself**, not by what it is used for — *"cooking enthusiasts with huge collections"* and *"design-conscious Apple users with a personal collection"*, the latter with no mandatory account and data in a private container. *(vendor copy)* — [`comparison.md` tiers 1 and 3](./comparison.md#tier-1--hard) · [t1-tandoor.png](./screens/t1-tandoor.png), [t3-mela.png](./screens/t3-mela.png)
- **People already hold collections for decades** without any software at all — Eat Your Books is a paid business serving shelves of cookbooks their owners cannot search. *(vendor copy)* — [`benchmark-retrieval.md` §2](./benchmark-retrieval.md#2-the-five-products)

**Why this job was missing from the first pass, recorded so the reasoning is visible.** The corpus's loudest single finding is *"saving is not cooking"*, and it names storage-for-its-own-sake as the failure mode in three separate tiers — the notes graveyard, the reel graveyard, vast saves against dismal cook-through. That argument was allowed to suppress the job rather than qualify it. **The correction is not that the finding was wrong; it is that it constrains this job's *outcome*, not its existence.** J-6 is real, and it is only earned when what is kept gets cooked — which is why its outcome clause is about reproducing a dish, never about the size of the collection.

---

## 3 · Emotional jobs

How the person wants to feel, or to stop feeling. **This is the corpus's weakest ground** — no one has reported a feeling to this research. What follows is admitted only where vendors visibly compete on the emotion, which is evidence that someone is paying to resolve it.

> ### E-1 · Committing without being trapped
> **When** I am about to put years of my own collecting into someone else's hands,
> **I want** to know I could take all of it back out again,
> **so that** I can commit to it properly, instead of half-using it and quietly keeping a copy elsewhere.
>
> **Українською:** *Коли я збираюся віддати роки власного збирання в чужі руки, я хочу знати, що зможу забрати все назад, щоб довіритися по-справжньому, а не користуватися наполовину, тихцем тримаючи копію десь іще.*

**Persona:** P-4 the Data Sovereign, primary. P-1 secondary — this is a precondition to J-1 for them, not a separate interest.

**Grew from:**
- **The fear tax.** *"Nobody types in sixty recipes without knowing they can leave."* Export is unaddressed on Fond's, Plan to Eat's and AnyList's sites; on Instagram/TikTok you can export nothing at all. *(correlation)* — [`competitive-landscape.md` pain 5](./competitive-landscape.md#seven-structural-pains)
- **Two vendors compete on precisely this feeling.** Mela: *"does not collect any data… does not depend on or use any third-party service"*, confirmed by the App Store listing. Tandoor: open source, self-host, *"GDPR Compliant — Made in Germany"*, no tracking, data exportable within 90 days. *(vendor copy)* — [`comparison.md` tiers 1 and 3](./comparison.md#tier-1--hard) · [t3-mela.png](./screens/t3-mela.png), [t1-tandoor.png](./screens/t1-tandoor.png)
- The corpus adds that these two have *"the most evangelical users"* — **that half is unmeasured** *(assertion)* and the job does not rest on it.

---

> ### E-2 · Being careful about food without having to be technical
> **When** I finally find something precise enough to be worth relying on,
> **I want** to use it without first learning to run a server,
> **so that** being exact about food is not a privilege reserved for technical people.
>
> **Українською:** *Коли я нарешті знаходжу щось достатньо точне, щоб на нього покластися, я хочу просто ним користуватися, а не вчитися спершу адмініструвати сервер, щоб точність у їжі не була привілеєм технічних людей.*

**Persona:** P-4 primary, P-1 secondary.

**Grew from:**
- **The forced trade, documented:** *"the optimiser's real choice today is a good model behind Docker, or a good app that fudges the maths."* *(correlation)* — [`competitive-landscape.md` pain 7](./competitive-landscape.md#seven-structural-pains)
- **The correlation underneath it:** of fifteen products, exactly one is built ingredient-first, and it is *"comfortably the least approachable product in the set."* Setup and interface cost keep Tandoor to a technical audience. *(correlation)* — [`summary.md` D-2](./summary.md#13-three-differences)
- **The inference is named:** the corpus documents the *choice*; that being on the wrong side of it feels like exclusion is a reading of that fact, not a measurement.

---

> ### E-3 · Choosing something and having it stay what I chose
> **When** I pick something because it does one thing properly,
> **I want** it to still be that same thing a year from now,
> **so that** I am not slowly moved somewhere I never chose to go.
>
> **Українською:** *Коли я обираю щось саме за те, що воно добре робить одну річ, я хочу, щоб через рік воно лишалося тим самим, щоб мене поступово не перенесли туди, куди я не погоджувався йти.*

**Persona:** P-1 primary, P-4 secondary.

**Grew from:**
- **The 2026 land-grab, across the set:** *"AI is the 2026 land-grab, and it's the paywall."* Fond gates import *and* its assistant behind payment; Tandoor's top tier is named *"Premium AI"*; Samsung Food leads with Health Score and AI meal plans. *"Monetization is migrating from the app to the inference."* *(correlation)* — [`comparison.md` pattern 4](./comparison.md#common-market-patterns)
- **A worked example of the drift:** Samsung Food is *"a content platform first — AI meal plans, Health Scores, dietary feeds"*, with a personal collection second. *(vendor copy)* — [`competitive-landscape.md` Samsung Food](./competitive-landscape.md#samsung-food-formerly-whisk) · [t1-samsung-food.png](./screens/t1-samsung-food.png)
- **The counter-position holds a market:** one-time purchase with no subscription is why Paprika's users stay. The *"tolerate an ageing interface"* half is *(assertion)*; the pricing and the persistence of that column are *(vendor copy + correlation)* — [`comparison.md` D-1](./comparison.md#key-differences)

---

## 4 · Social jobs

How the person stands in relation to other people. **Read the caveat at the foot of this section before using either of these** — it is the sharpest finding in the whole document.

> ### S-1 · Being legible to the people I share a kitchen with
> **When** feeding us is a job several of us share,
> **I want** what I have already done to be visible without me having to announce it,
> **so that** nobody has to ask what has been handled and what has not.
>
> **Українською:** *Коли годувати нас — спільна справа кількох людей, я хочу, щоб зроблене мною було видно без окремих оголошень, щоб нікому не доводилося перепитувати, що вже зроблено, а що ні.*

**Persona:** P-2.

**Grew from:**
- **The product built on this is sold on visibility to others**, not on private organisation: *"the best way to create and share a grocery shopping list"*, with changes showing up *"instantly to everyone sharing the list."* *(vendor copy)* — [`comparison.md` tier 2](./comparison.md#tier-2--soft) · [t2-anylist.png](./screens/t2-anylist.png)
- **Households are a priced unit across the category**, which is evidence that coordination between named people is what is being bought. *(vendor copy)* — [`comparison.md` pattern 3](./comparison.md#common-market-patterns)
- The corpus also names a second household member **who never authors anything and only ticks items off** — the person this legibility is aimed at. That one is *(assertion)* — [`ux-patterns.md` §5](./ux-patterns.md)

---

> ### S-2 · Handing it on to someone who does not live in my tools
> **When** the person going to the shop is not the person who worked out what we need,
> **I want** to hand over what is needed in whatever form already reaches them,
> **so that** helping out never requires them to install anything of mine.
>
> **Українською:** *Коли до магазину йде не той, хто продумував, що нам потрібно, я хочу передати це в тому вигляді, який до людини і так доходить, щоб допомога не вимагала від неї нічого встановлювати.*

**Persona:** P-2, with P-1 on the sending side.

**Grew from:**
- **The receiving surface is already installed on everyone's phone**: shared lists in Apple Reminders and Google Keep are *"the zero-effort shared grocery list"* — free, everywhere, platform-grade sync. *(correlation)* — [`competitive-landscape.md` tier 2](./competitive-landscape.md#tier-2--soft)
- **And that is exactly the competitive floor:** *"a household with a working shared Keep list has no felt problem for Cooksy to solve."* The handover job survives whether or not the rest of the product is adopted. *(assertion — recorded as the honest counter-evidence)*

---

**The caveat, and it is worth more than either job above.** The one social job this corpus evidences *strongly* belongs to a segment Cooksy has deliberately excluded: recognition for cooking. Cookpad ranks by つくれぽ counts, hall-of-fame recipes praised by 1,000+ users, dishes *"made 300,000+ times"*; Pinterest is a visual bookmark graph built on sharing outward. *(vendor copy + screen)* — [t2-cookpad.png](./screens/t2-cookpad.png), [t2-pinterest.png](./screens/t2-pinterest.png)

That is the **discovery-seeker anti-persona** ([`personas.md` §Anti-personas](./personas.md)). So the corpus's best social evidence points at a door the product has chosen to keep shut, and S-1 and S-2 above are the residue: coordination and handover, not status. **If social jobs turn out to matter more than this, the research currently cannot tell us — it only knows about the kind Cooksy refuses to serve.**

---

## Hypotheses — not yet earned a place

Each of these is a plausible job that **nothing external supports**. They are held here rather than deleted, with what would move them up.

| # | Job | Why it is not in the main list | What would move it |
|---|---|---|---|
| **H-1** | *When a total has been assembled for me out of several sources, I want to be able to open it up and see what it is made of, so that I can stop re-checking it by hand.*<br><br>**UA:** *Коли якусь суму зібрали за мене з кількох джерел, я хочу мати змогу її розгорнути й побачити, з чого вона складається, щоб перестати перевіряти це руками.* | The market **gap** is well documented — *"trust is signalled socially, never demonstrated numerically… nobody proves a number by showing its parts"* *(correlation)*. The **job** is not: the corpus grades *"a tool you verify by hand has negative ROI"* as *"logic, not data"*, and G-3 says plainly it is **not testable by desk research**. | Watching someone verify, or decline to. G-3 |
| **H-2** | *When I have been told I already have something at home, I want to be sure of it before I leave the shop, so that I do not get home without the one thing I did not buy.*<br><br>**UA:** *Коли мені сказали, що вдома це вже є, я хочу переконатися в цьому до того, як вийду з магазину, щоб не повернутися додому без єдиної речі, яку я не купив.* | Rests entirely on the brief's own rule — *"an ingredient never vanishes without a trace… the kind of failure users don't forgive"* *(assertion)*. Nobody has watched this happen. | G-7 — a month of real upkeep, or a teardown of a shipped pantry |
| **H-3** | *When putting something in properly costs more than scribbling it down, I want to stop bothering, so that I am not paying for tidiness I never get anything back from.*<br><br>**UA:** *Коли внести щось як належить коштує дорожче, ніж просто нашкрябати собі нотатку, я хочу перестати це робити, щоб не платити за охайність, з якої я нічого не отримую.* | The threshold claim — *"if paste → review → save is slower than pasting into a note, Cooksy loses"* — is *(assertion)*, and *"field-hunting is where libraries die at eleven recipes"* is the research's own frame. | G-1, the parser bake-off. Named the highest-value outstanding item |
| **H-4** | *When I keep coming back to the same handful of dishes, I want them in front of me without having to ask, so that I stop re-deciding what I decided long ago.*<br><br>**UA:** *Коли я знову й знову повертаюся до тих самих кількох страв, я хочу бачити їх перед собою, не питаючи, щоб не вирішувати заново те, що я вирішив уже давно.* | The premise — households rotate through roughly fifteen dishes — is the **brief's own assertion**, then reused as a threshold. Circular. | G-8, and the two week-one counts in G-2 |
| **H-5** | *When I have built up a pile of things I meant to cook and never did, I want going back to it to feel like choosing, not like owing.*<br><br>**UA:** *Коли в мене назбиралася купа того, що я збирався зготувати й так і не зготував, я хочу, щоб повертатися до неї було як вибирати, а не як віддавати борг.* | The **behaviour** is evidenced — vast saves, dismal cook-through *(correlation)*. The **feeling** attached to it is invented here; no one has reported it. | Any first-hand contact. Nothing in the corpus can reach it |
| **H-6** | *When I am shopping where I actually live, I want the order of things to match the shop I am standing in, so that one pass really is one pass.*<br><br>**UA:** *Коли я купую там, де я насправді живу, я хочу, щоб порядок збігався з магазином, у якому я стою, щоб один прохід і справді був одним проходом.* | All sources are US-centric and the walking order **has never been validated against a European supermarket** — while reordering is rejected, so it is the only order anyone gets. | G-6 — walk a real shop, count the backtracks |
| **H-7** | *When a dish is written in measures I do not think in, I want it in the ones I do, so that I am not converting in my head while my hands are busy.*<br><br>**UA:** *Коли страва записана в мірах, якими я не думаю, я хочу бачити її в тих, якими думаю, щоб не перераховувати в голові, поки руки зайняті.* | The mirror of J-3, for a non-metric person. Whether such a user is in the audience at all is **[?]** — the adoption risk was *"accepted, not disputed"*, and unmeasured. | A non-metric user. There is not one to test against yet |

**One thing to notice about this table.** H-1 is the job that Cooksy's most defensible wedge is built to serve — auditability is called *"an unoccupied position in the entire category"* — and it is the least evidenced job in this document. That is not an argument against the wedge. It is the reason the wedge is still available.

---

## Wording check — feature names

Requested explicitly, so it is run explicitly. Every job statement above was checked against the product vocabulary in [`CLAUDE.md`](../CLAUDE.md). **No job statement contains any of:**

`grocery list` · `shopping list` · `meal planner` · `week plan` · `pantry` · `staples` · `recipe library` · `search` · `filter` · `import` · `parser` · `review screen` · `servings stepper` · `scaling` · `portion size` · `merge` · `aisle grouping` · `sub-recipe` · `household sharing` · `sync` · `offline` · `export` · `share sheet` · `calories` · `kcal` · `canonical ingredient` · `tags`

**Borderline words that were kept, and why.** Each names something that existed long before any software did:

- **"cooking", "the hob", "the fridge", "the cupboard", "the shop", "a trip"** — physical world.
- **"amounts"** — used in place of *quantities* and *portion size*, which are typed fields in the brief.
- **"in the order I will walk it"** (J-4) — deliberately describes the person's path through a building, not a grouping rule.
- **"keep it in a form that will still make sense"** (J-1) — describes the state the person needs, not the capture or correction steps that produce it.
- **"the same picture of what is planned"** (J-5) — a shared understanding between people, not a synchronised document.
- **"walk away with all of it intact"** (E-1) — the person's freedom to leave, not a data-portability capability.

**Statements rewritten during checks**, recorded so the bar is visible. First pass: J-2 read *"I want to search my collection by that ingredient"*; J-4 read *"gathered into one merged list grouped by aisle."*

**Second pass — the wording rework.** Every statement was rewritten again, this time for craft rather than vocabulary. Four had real defects:

| | Defect | Fix |
|---|---|---|
| **J-0** | *"I want those decisions **turned into**…"* — passive, and turned by whom. A motivation clause that implies a system doing the work is a solution in disguise | Motivation is now the person's own: *get everything into the house in one go, without doing the arithmetic or the remembering myself* |
| **J-2** | *"I want **to see** what I could make"* — seeing a set of options is a screen, not a motivation | Now *get back to the dish I already know works*, and the situation carries the actual struggle: **not being able to remember** what you made last time |
| **J-4** | Repeated J-0's *"single trip"*, so the two jobs blurred | J-0 keeps completeness and amounts; **J-4 now owns the in-store moment** — standing at the entrance, walking it once, not doubling back |
| **J-6** | Two outcomes stacked in one clause | Reduced to one. The *"exists nowhere else"* argument lives in the evidence, where it is sourced |

**The Ukrainian is a parallel formulation, not a translation.** Each was written to be idiomatic — *"опинилося в каструлі, а не у смітнику"* rather than a literal rendering of *"ends up in a pan rather than a bin"*. The feature-name rule was applied to both languages independently: the noun *план* was avoided in J-5 (it maps onto the weekly planner) in favour of *"на ті самі кілька днів"*, and the English was changed to match.

---

## 5 · The matrix

Two questions only: **what to build first, and what not to build at all.**

### How to read a cell

| | Meaning |
|---|---|
| **3** | The job this persona is defined by — the reason they would adopt anything at all |
| **2** | Clearly matters and is evidenced, but is not what defines them |
| **1** ▽ | **Evidenced as low priority**, and the marker is load-bearing: the score comes from *documented behaviour that implies the job is not being pursued* — vast save rates against dismal cook-through, or living happily on a platform that exports nothing. It is an inference from what people do, not a preference anyone stated. |
| **[?]** | **Nothing in the corpus speaks to this cell.** Not a low score, not a middling one — an absence. Never averaged, never guessed. |
| ⚑ | The corpus contains evidence pointing **both ways**; the conflict is named under the table |

**On the two added columns.** FUNCTION and COMPETITORS deliberately use product vocabulary — naming a feature is the entire point of those columns. The no-feature-names rule governs the **job statements** in sections 1–4, and it still holds there.

### Jobs × personas

| Job | P-1 Optimiser *(primary)* | P-2 Household | P-3 Hoarder | P-4 Sovereign | FUNCTION — what closes it | COMPETITORS — is it already closed? |
|---|---|---|---|---|---|---|
| **J-0** one trip, right amounts | **3** · §9's success criteria *are* this job | **3** · *"we'll automatically build your grocery list"*, sold to busy families | **1** ▽ · vast saves, dismal cook-through | **2** · Tandoor sorts the list by supermarket | §5.7 planner → §5.9 list generation | **Covered, heavily.** Paprika, Plan to Eat, Samsung and Tandoor all ship the loop end to end |
| **J-1** keeping what I find | **3** · capture cost is the typed-record pattern's one weakness | **[?]** | **3** · 114M reels; one-tap save | **2** · Mela ships live detection, RSS, OCR, video-description import | §5.2 paste + URL import → mandatory review | **Covered, universally.** *"Everyone leads with capture"*; Mela is the benchmark |
| **J-2** using what I already have | **3** · pain #1; the aubergine question is theirs | **[?]** | **3** · *"retrieval is hopeless"* is their tier's finding | **2** · *"huge collections"*; Tandoor trigram ⚠︎ | §5.13 two-tier search over §5.5 | **Barely, in-category.** Paprika scores R1=3 across seven fields; the good answers (SuperCook, Eat Your Books) are *outside* the category |
| **J-3** amounts for the people eating | **3** · Crouton sells scaling; D-3 unit chaos across 15 | **[?]** | **[?]** | **2** · Tandoor ships editable unit conversions | §5.4 scaling · §5.1 three units · §5.3 weight model | **Half.** Everyone converts; **nobody constrains.** The three-unit rule is unique across all 15 and validated by none |
| **J-4** one trip, not three laps | **3** · §9's *"one pass through the store"* | **3** · AnyList category assignment *"essentially always right"* | **1** ▽ | **2** · list auto-sorted by supermarket | §5.9 merge + aisle order · §5.8 subtraction | **Covered, thoroughly.** The category's marketed mechanism; reordering is the default, incumbent included |
| **J-5** household without collisions | **[?]** ⚑ | **3** · priced at +$5/yr; *"instantly to everyone"* | **[?]** | **[?]** ⚑ | §5.10 household + live shared list | **Covered — table stakes.** *"Its absence is a defect."* Paprika is the outlier |
| **J-6** the good version outlasting memory | **3** · Paprika's product base *is* the library | **[?]** · AnyList's base is the list, not a library | **2** · saving at that scale is keeping-intent, unmet | **3** · *"huge collections"*, *"a personal collection"* | §6.1 Library · §5.2 review → save · §8.1 export *(post-MVP)* | **Covered.** The centre of gravity for 3 of the 15 |
| **E-1** committing without being trapped | **2** · *"nobody types in sixty recipes without knowing they can leave"* | **[?]** | **1** ▽ · accepts a platform that exports nothing | **3** · GDPR, self-host, 90-day export | **None in MVP** — §8.1 defers full export | **Split.** Mela and Tandoor own it outright; Fond, Plan to Eat and AnyList are silent |
| **E-2** careful without being technical | **3** · pain 7: Docker or fudged maths | **[?]** | **2** · their tier is defined by zero setup | **1** ▽ · they already pay the technical cost willingly | **Not a feature** — §3's PWA and §7's principles | **Unoccupied.** The single ingredient-first product is the least approachable of the fifteen |
| **E-3** it stays what I chose | **2** · the one-time column persists | **[?]** | **1** ▽ · lives on platforms that change under them constantly | **3** · OSS and self-host are this job absolute | **Not a feature** — §8's refusals, §4's no-monetisation | **Eroding.** *"AI is the 2026 land-grab, and it's the paywall"* |
| **S-1** legible to the people I share a kitchen with | **[?]** | **3** · AnyList is sold on visibility to others | **[?]** | **[?]** | §5.7 member assignment · §5.10 live list | **Covered.** AnyList |
| **S-2** handing it to someone outside my tools | **[?]** | **2** · Reminders and Keep are already on every phone | **[?]** | **[?]** | §5.11 text export | **Weak.** Sharing *inside* an app is common; handover *outside* it is unaddressed on most sites |

### The two ⚑ conflicts, named

**J-5 × P-1.** Paprika ships **no household sharing at all** and its audience stays anyway *(vendor copy)* — which reads as low importance. Against that, market pattern 3 finds sharing is now table stakes and *"its absence is a defect"* *(correlation)*. The two point opposite ways and the corpus cannot resolve which describes P-1. Averaging them to a 2 would manufacture a fact, so the cell stays **[?]**.

**J-5 × P-4.** Tandoor ships live list sync; Mela ships no sharing at all and holds the strongest advocacy in the set. Both are P-4's anchor products. Same resolution: **[?]**.

---

## 6 · Conclusion A — three jobs for the MVP core

The filter is the one requested: **scored 3 for the primary persona, and not already closed by the market.**

Seven jobs score 3 for P-1. Four of them fall out immediately because the category already does them well — J-0, J-1, J-4 and J-6 are covered heavily, universally, thoroughly and by three products respectively. Building there is building a worse Paprika. Three survive:

> **1 · J-2 — using what I already have.**
> Scored **3** for P-1 and **3** for P-3, and it is **pain #1** in the entire corpus. In-category coverage is genuinely poor: Paprika searches seven fields and still scores R1=3, and the products that do this well — SuperCook, Eat Your Books — are outside the category and not competing here. Cooksy's own spec was scored at **23/40, below Tandoor**, on exactly this dimension before it was rebuilt. Highest pain, weakest incumbents.

> **2 · J-3 — amounts for the people actually eating.**
> The market covers **half** of this job and the half it skips is the whole point. *"Everyone converts units; nobody constrains them"* — Crouton advertises metric/imperial conversion as a feature, deliberately preserving the ambiguity; Tandoor makes conversions user-editable. The three-unit rule is **unique across all fifteen products and validated by nobody's shipped behaviour.** That makes it simultaneously the sharpest idea in the brief and the least externally supported — a real bet, but a bet on an empty position rather than a crowded one.

> **3 · E-2 — being careful about food without having to be technical.**
> The only **unoccupied** cell in the COMPETITORS column that a primary persona scores 3 on. Pain 7, stated directly: *"the optimiser's real choice today is a good model behind Docker, or a good app that fudges the maths."* Of fifteen products exactly one is ingredient-first, and it is comfortably the least approachable. **This is not a feature and cannot be scheduled as one** — it is a standard the other two are held to. It belongs in the core precisely because it is the thing that decides whether J-2 and J-3 are usable by anyone who is not already a self-hoster.

**The fourth candidate, and why it is not in the three.** H-1 — *seeing what a total is made of* — would otherwise top this list. Auditability is called *"an unoccupied position in the entire category, and the closest thing Cooksy has to a defensible wedge"*, and three of five best-in-niche products score ≤3 on match transparency. It is held back for one reason: **it is a hypothesis, not an established job.** The market gap is documented; the human desire behind it is graded *"logic, not data"* and G-3 states it is not testable by desk research. Build it — the wedge is real and the position is empty — but do not let it into a list labelled *evidenced* until someone has been watched either verifying a number or declining to.

---

## 7 · Conclusion B — features that close no job

Read directly off the FUNCTION column: features in the brief that no row in this matrix requires.

**1 · Calorie reporting (§5.6) — the strongest candidate, and the most uncomfortable.**
Not one of the twelve jobs needs it. Worse, the persona work points the other way: P-1 is explicitly *"not a diet persona"*, and *"health-goal seekers"* are named as Samsung Food's audience and recorded as an **anti-persona**. The two dependent pieces fall with it — the optional finished-dish weight field exists mainly to make kcal/100 g honest, and *kcal per portion* is the calorie half of the portion-size machinery. **Two readings, and the research cannot choose between them:** either a genuine job is missing because no one went looking for *"I want to know what I'm actually eating"*, or the feature is unanchored. It is a locked decision in §4, so this is a flag for a decision-maker, not a recommendation to cut.

**2 · Sub-recipe links (§5.2.2).**
Their only retrieval value is placing a recipe in the *Used in* tier — which J-2's function already reaches through method text and ingredient matching. The brief concedes the position itself: they *"can land any time after step 2, and cost nothing to defer because nothing depends on them."* A feature nothing depends on, serving a job nothing requires.

**3 · Ingredient groups (§5.2.1).**
Serve no job in this matrix directly. The justification that survives is narrow but real: parse fidelity — a heading in the source is information the cook loses if it is dropped — plus one field on a search result row. Cheap enough that the case is weak rather than damning.

**And the inverse failure, which matters more: a job with no function at all.**
**E-1** — *committing without being trapped* — scores **3** for P-4 and **2** for P-1, and **MVP ships nothing that closes it**, because full library export is deferred to §8.1. The corpus already calls this pain *"knowingly left on the table."* The matrix now puts a number on what is being left: the defining job of one persona, and a stated precondition for the primary persona typing anything in at all.

*(**E-3** also has no feature, and that is correct rather than a gap — it is closed by §8's refusals and §4's no-monetisation stance. A promise kept by not building things is still kept.)*

---

## 8 · What the empty cells say

**17 of 48 cells are [?] — just over a third of the matrix is unknown.** Distribution is not even, and the shape is the finding:

| Persona | Unknown cells | Reading |
|---|---|---|
| **P-1** primary | 3 of 12 | Best understood, as it should be. All three gaps are social or household jobs |
| **P-2** household | **7 of 12** | **The least understood persona in the set** — and the strongest secondary |
| **P-3** hoarder | 4 of 12 | Well evidenced on capture and retrieval, blank on everything downstream |
| **P-4** sovereign | 3 of 12 | Sharply defined, on a narrow set of jobs |

**P-2 is the actionable one.** Everything known about them concerns coordination — J-5, J-4, S-1, S-2 — and everything about what they cook, keep, find or scale is blank. This is the persona whose core job the corpus also says may not be felt at all (*"a household with a working shared Keep list has no felt problem for Cooksy to solve"*). A secondary persona that is simultaneously the least understood **and** the one carrying a live "maybe there is no pain here" verdict is the cheapest place a single conversation would change the picture — and worth more than another pass over the same fifteen products.

---

## Traceability

| Job | Persona | Strongest single source | Class |
|---|---|---|---|
| **J-0** | P-1 (P-2) | The meta-pain across three tiers; §9's success criteria | correlation |
| **J-1** | P-3 (P-1) | 114M `#recipe` reels; all five hard competitors market import | screen · correlation |
| **J-2** | P-1 | Pain #1; Eat Your Books as a paid business; SuperCook 4.8★/22K | correlation · vendor copy |
| **J-3** | P-1 | Crouton sells per-ingredient scaling; D-3 unit chaos across 15 | vendor copy · correlation |
| **J-4** | P-1 (P-2) | Merge-and-sort is the category's marketed mechanism | vendor copy |
| **J-5** | P-2 | Household priced +$5/yr; sharing is table stakes | vendor copy · screen |
| **J-6** | P-1 (P-4, P-3) | The collection is the centre of gravity for 3 of 15; Crouton sold as *"a home for your favourite recipes"* | correlation · vendor copy |
| **E-1** | P-4 (P-1) | Mela and Tandoor compete on exactly this feeling | vendor copy |
| **E-2** | P-4 (P-1) | Docker-or-fudged-maths; the only ingredient-first product is the least usable | correlation |
| **E-3** | P-1 (P-4) | AI as the 2026 paywall; Samsung Food's drift to content | correlation |
| **S-1** | P-2 | AnyList sold on visibility to others; households priced as a unit | vendor copy |
| **S-2** | P-2 (P-1) | Reminders/Keep as the already-installed receiving surface | correlation |
| **H-1 … H-7** | — | Nothing external. See the table above | assertion · **[?]** |

**Standing caveat.** Twelve jobs, none of them observed. The single cheapest thing that would change this document more than another pass over the same fifteen products: **five conversations with people who cook.** The corpus contains zero ([`summary.md` §5.9](./summary.md#5-unverified)).

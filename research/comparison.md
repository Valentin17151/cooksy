# Competitor comparison — five axes, three tiers

**Date:** 20 July 2026
**Scope:** the 15 products already identified in [`competitive-landscape.md`](./competitive-landscape.md) — 5 per tier. No new products were added.
**Method:** page fetches against live sites and App Store listings, plus browser capture of key screens into [`screens/`](./screens/). Where a product's key screen sits behind a login I don't hold, the screenshot is watermarked **ACCESS RESTRICTED** rather than faked.

Axes: **audience · product base · key mechanism · trust · monetization.**

---

## Tier 1 — Hard

Same product, same audience.

| | **Paprika 3** | **Fond** | **Samsung Food** | **Plan to Eat** | **Tandoor** |
|---|---|---|---|---|---|
| **Audience** | Multi-device home cooks who shop systematically. No demographic claimed; the UI selects for tolerance. | "2,400+ home cooks on the waitlist" — enthusiasts, pre-launch. | Global home cooks + health-goal seekers + community browsers. | "If you love meal planning and staying organized" — organised households, busy families. | "Cooking enthusiasts with huge collections" — self-hosters, technical. |
| **Product base** | **Recipe library**, with planner and list derived from it. | **Extracted recipes** (URL/photo/social) + plans + lists, over a normalised ingredient layer. | **Content platform first**, personal recipe box second. Communities and discovery are the shell. | **Planner-first.** The calendar is the core; the list is the by-product. | **Ingredient/food database first** — the only one of the 15 built this way. |
| **Key mechanism** | Cloud sync across devices → grocery lists that "automatically combine ingredients and sort them by aisle", with **custom aisle organisation** and a pantry tracking quantity, purchase date and expiry. | "Save–Plan–Shop–Cook" driven by **August**, an AI assistant scoped to *your* library, plan and inventory rather than the open internet. | Save from any site → drag-and-drop weekly plan → "one click" list → nutrition and Health Score unlock. | "Pick your meals, and we'll automatically build your grocery list." **User-reorderable categories**, per-store lists, a Staples list, a separate pantry. | URL import from thousands of sites, list auto-sorted by supermarket, editable unit conversions, nutrition + pricing, real-time list sync. |
| **Trust** | Strong and understated: "all of your data is stored locally", explicit offline access, one-time purchase. But email + user content are linked to identity, and **there is no household sharing at all**. | Sync across four platforms; list "shared with whoever is shopping". Offline, export and permissions **not stated anywhere on the site**. Pre-launch. | Ratings (4.8), Webby nomination, nutrition breadth. Against that: a hardware giant's account, AI meal plans and a Health Score you must trust. | 14-day trial, no credit card. Testimonials and an origin story. Offline, export and privacy claims absent. | **The strongest data story in the set:** open source, self-host via Docker/K8s, "GDPR Compliant - Made in Germany", no tracking or analytics, data exportable within 90 days of cancellation. |
| **Monetization** | **One-time, per platform.** $4.99 on iOS; "each version of Paprika is sold separately". No subscription. | **Freemium, AI-gated.** Free to 50 recipes incl. planning, lists and cook mode; "AI features (recipe import from URL/photo and August chat) are part of the paid plans". Prices unpublished. | **Free tier + Food+**, $59.99/yr (per prior desk research; not re-verified — site 403s to fetchers). | **Subscription only.** "$5.95/mo or $49/year", annual billed as "4 months free". No free tier. | **OSS free self-host**, plus hosted: Free €0 · Basic €1.99/mo · Standard €3.49/mo (reg. €4.49) · **Premium AI** €4.99/mo (reg. €6.49). |
| **Screens** | [site](./screens/t1-paprika.png) | [site](./screens/t1-fond.png) | [site](./screens/t1-samsung-food.png) | [site](./screens/t1-plan-to-eat.png) | [site](./screens/t1-tandoor.png) · [app 🔒](./screens/t1-tandoor-app-restricted.png) |

---

## Tier 2 — Soft

Different product, same underlying job. This is where the recipes actually live today.

| | **Apple Notes & Notion** | **Instagram & TikTok saves** | **AnyList** | **Apple Reminders & Google Keep** | **Cookpad & Pinterest** |
|---|---|---|---|---|---|
| **Audience** | Everyone. Not cooking-specific, which is the point. | Everyone under ~45. Where recipes are *found* in 2026. | Households coordinating a shop — the closest soft competitor to the core loop. | Everyone. The zero-effort shared list. | Discovery-seekers. Cookpad is "Japan's #1 recipe search". |
| **Product base** | **Unstructured documents.** No schema, no quantities, infinite tolerance. | **Someone else's video.** A save is a bookmark on content you don't own and can't export. | **The list itself.** Page title: "the best way to create and share a grocery shopping list." Recipes and planning grew on top. | **Generic checkable items.** No quantities, no ingredients, no semantics. | **UGC community content** (Cookpad) and a **visual bookmark graph** (Pinterest). Storage is a side effect of browsing. |
| **Key mechanism** | Frictionless capture from anywhere via the system share sheet. Nothing to configure, nothing to correct. | Infinite discovery + one-tap save. Capture is effortless; **retrieval is hopeless**. 114M reels on `#recipe` alone. | "Any changes made to a shared list will show up instantly to everyone sharing the list", plus automatic category grouping and Siri input. | Shared list, checkbox, already installed, free, works everywhere. | Social proof as ranking: つくれぽ counts, "hall of fame" recipes praised by 1,000+ users, "made 300,000+ times". |
| **Trust** | Apple Notes: on-device, iCloud, no extra account, offline-native. Notion: cloud workspace, account required. Both are trusted because they're *general* — no cooking vendor to outlive. | None, structurally. No search, no export, no quantities; content can vanish. The personal saves collection is **login-only**. | Instant sync across Mac/PC/iOS/iPad. Offline behaviour, export and privacy **not addressed on the site**. | Platform-grade sync and offline. Keep's actual product is **login-gated**. | Crowd validation substitutes for correctness. Vast save rates, dismal cook-through. |
| **Monetization** | Notes free with the OS; Notion freemium. | **Free, ad-funded.** You are the inventory. | **AnyList Complete**, yearly only: "$9.99 / year for an individual", "$14.99 / year for a household". | Free with the platform. | Cookpad freemium (プレミアムサービス); Pinterest advertising. |
| **Screens** | [Notion](./screens/t2-notion.png) · [Apple Notes 🔒](./screens/t2-apple-notes-restricted.png) | [`#recipe` tag](./screens/t2-instagram-recipe-tag.png) | [site](./screens/t2-anylist.png) | [Google Keep 🔒](./screens/t2-google-keep-restricted.png) | [Cookpad](./screens/t2-cookpad.png) · [Pinterest](./screens/t2-pinterest.png) |

---

## Tier 3 — Aspirational

The craft bar.

| | **Mela** | **Crouton** | **NYT Cooking** | **AnyList** *(as sync benchmark)* | **Things 3 & Todoist** |
|---|---|---|---|---|---|
| **Audience** | Design-conscious Apple users with a personal collection. | Apple-ecosystem cooks who cook *from the device*. | Subscribers; "home cooks of all levels". | Households mid-shop, in two different aisles. | Outside the category entirely — the list-craft reference. |
| **Product base** | **Personal library, no mandatory account.** Data sits in a private iCloud container or locally. | "A home for your favourite recipes, from wherever you find them", on iCloud. | **Editorial content library.** The personal Recipe Box is subscriber-gated. | Same product as Tier 2; judged here on execution. | Task objects. Things: local + first-party sync. Todoist: cloud, freemium. |
| **Key mechanism** | **In-app browser with live recipe detection** — browse → auto-detect → preview → save. Plus RSS blog subscriptions, an OCR scanner for physical books, and **import from YouTube / TikTok / Instagram video descriptions**. Cook mode in large type with Live Activities timers. | **Step-by-step cook mode**: "tap on ingredients within a step to get the quantity", hands-free step advance for messy hands, scaling by servings *or per individual ingredient*, self-naming timers ("Bake Cookies"). | Editorial authority — "tested and perfected" — plus community cooking notes. | Shared-list sync so fast it reads as local, and category assignment that is essentially always right. | One-thumb list ergonomics: instant writes, undo, gestures, empty states, flawless offline. |
| **Trust** | **The strongest privacy position of all 15:** "Mela does not collect any data… stored securely in a private container in your iCloud account. Mela does not depend on or use any third-party service." App Store confirms: "The developer does not collect any data from this app." | iCloud sync, household sharing, Family Sharing. Weaker than Mela: email and user ID are **linked to you**, plus analytics. | Institutional authority, borrowed from the masthead rather than built by the software. | Reliability as trust — it has simply never lost a checkoff. | Things: two Apple Design Awards, Editors' Choice, a decade of use. Todoist: roles and permissions at the Business tier. |
| **Monetization** | Free download + **one-time IAP**: "Mela+ for iOS/iPadOS $6.99". | **Hybrid.** Discover Monthly $1.99 · Discover Yearly $14.99 · **Crouton Plus $24.99 (lifetime)** · Early Bird $17.99 · tips $0.99–$7.99. | **Subscription, hard paywall.** Price not shown on any page captured. | $9.99/yr individual · $14.99/yr household. | Things: one-time per platform. Todoist: freemium (Beginner / Pro / Business). |
| **Screens** | [site](./screens/t3-mela.png) | [site](./screens/t3-crouton.png) | [site](./screens/t3-nyt-cooking.png) · [Recipe Box 🔒](./screens/t3-nyt-recipe-box-restricted.png) | [Complete pricing](./screens/t3-anylist-complete-pricing.png) | [Things](./screens/t3-things.png) · [Todoist](./screens/t3-todoist.png) |

---

## Common market patterns

1. **Everyone leads with capture; nobody leads with correctness.** All five hard competitors market import — "save from any website", "from wherever you find them". Not one markets quantity accuracy, unit integrity or an audit trail. The correction step is treated as a cost to hide, never a feature to sell. Cooksy's mandatory review screen (§5.2) is therefore *contrarian positioning*, not table stakes — which cuts both ways.
2. **The grocery list is always derived, never authored.** In every hard product the list is an output of the plan. Only AnyList treats it as a first-class object with a life of its own — and it's the one product households actually run their shop from. This is direct support for §5.9's "generating never destroys".
3. **Household sharing has become table stakes, and it's priced at almost nothing.** AnyList charges $5/yr more for a household than an individual; Crouton ships it via Family Sharing; Fond sells workspaces; Tandoor syncs live. Paprika's total absence of it is now the outlier, not the norm. Sharing is no longer a differentiator — its *absence* is a defect.
4. **AI is the 2026 land-grab, and it's the paywall.** Fond gates URL/photo import *and* its assistant behind payment; Tandoor's top tier is literally named "Premium AI"; Samsung Food leads with Health Score and AI plans. Monetization is migrating from the app to the inference.
5. **Trust is signalled socially, never demonstrated numerically.** NYT borrows it from the masthead, Cookpad from "made 300,000+ times", Samsung from ratings and awards, Mela and Things from design awards. Nobody proves a number by showing its parts. §7.2's auditability is an **unoccupied trust position**.

## Key differences

1. **Monetization shape predicts architecture, reliably.** One-time (Paprika $4.99, Mela $6.99, Things) → local-first, offline, no server, no sharing. Subscription (Plan to Eat $5.95/mo, Fond, Samsung, NYT) → server-side, sync, sharing, AI. Free/ad or OSS (Instagram, Keep, Tandoor self-host) → you're either the product or the sysadmin. **Cooksy wants the offline guarantees of column one with the sharing and server-side import of column two** — the expensive corner of the matrix, and §8 rules out revenue.
2. **Data ownership spans the full range.** Mela ("does not collect any data", no third-party services) and Tandoor (GDPR, self-host, 90-day export) at one pole; Instagram/TikTok saves at the other, where you own and can export nothing. Paprika sits oddly between: local storage and no subscription, but email and user content linked to identity.
3. **Centre of gravity differs wildly** — library (Paprika, Mela, Crouton), planner (Plan to Eat), list (AnyList), content (Samsung, Cookpad, NYT), **ingredient database (Tandoor alone)**. Only Tandoor shares Cooksy's ingredient-first centre, and it is comfortably the least approachable product in the set. That correlation is worth staring at: the correct model has historically shipped inside the worst interface.
4. **Cook-time interaction is the whole aspirational differentiator, and the hard tier ignores it completely.** Crouton's tap-an-ingredient-inside-a-step and hands-free advance, Mela's large-type cook mode — no hard competitor markets any of it. §8's blanket rejection of "cooking mode with timers" currently discards this entire axis along with the timers.
5. **Everyone converts units; nobody constrains them.** Crouton advertises metric/imperial conversion *as a feature* — i.e. it deliberately preserves both. Tandoor makes conversions user-editable. Cooksy's strict three-unit rule (`g`/`ml`/`pcs`) is genuinely unique across all 15 products, and is validated by no one's shipped behaviour.

## Open questions for PM

1. **Is "review every parse" a feature or a tax?** No competitor ships a mandatory correction step, and the soft tier beats everyone on capture speed by having no structure at all. Fond's answer is to make AI good enough that review is unnecessary — and to charge for that. Cooksy bets the exact opposite. That bet needs the parser bake-off already listed in *Gaps*, not conviction.
2. **Does the architecture assume a budget the product has ruled out?** Local-first + offline + live household sync + server-side URL fetch is a subscription-shaped cost base, chosen in §5.12/§11.0, while §8 rejects monetisation. Fine for a portfolio piece — but it should be an acknowledged subsidy, not an oversight.
3. **The flat-permissions decision rests on an unverified claim.** `competitive-landscape.md` attributes an owner/editor/viewer model to Fond; **nothing on Fond's site corroborates it**, and the product reads as pre-launch (waitlist, "Coming soon"). §5.10 currently justifies itself against a competitor behaviour I could not confirm. Verify it or drop the justification and stand on the reasoning alone.
4. **Video recipes can no longer be deferred.** Mela — a one-person shop — already imports from YouTube, TikTok and Instagram video descriptions, so "too hard" is not the reason to exclude it. Instagram's `#recipe` tag alone shows **114M reels**. This is now the largest capture surface in the market and a craft-tier competitor has shipped against it, while the brief still lists it as merely "Open".
5. **Does metric-only survive contact with a non-metric user?** Every one of the 15 preserves both systems. The constraint is simultaneously Cooksy's sharpest idea and its largest adoption risk: it makes the product work-as-intended impossible for US users, who are most of this category's paying base. Is that a deliberate EU-first narrowing, or an unexamined default?

---

## Corrections to `competitive-landscape.md`

Three claims in the existing desk research did not survive this pass:

- **"No offline capability mentioned" / Paprika.** The App Store listing states the opposite: "all of your data is stored locally", with explicit offline access. Paprika is local-first *and* one-time-purchase — a closer precedent for §5.12 than the doc implies.
- **"Aisle organisation is limited" / Paprika.** The listing advertises **custom aisle organisation**. This weakens the framing of the open *user-editable aisle order* finding: it isn't only Plan to Eat and AnyList that ship reordering, it's the category default, including the incumbent.
- **Fond's roles model.** Recorded as "owner / editor / viewer" and used as the foil for §5.10. Unsupported by anything on their site; treat as unverified.

## Method notes

- `samsungfood.com` and `cooking.nytimes.com` return 403 / block server-side fetchers but load normally in a real browser — both were captured and read via Playwright instead.
- Four screens sit behind logins not held here and are watermarked **ACCESS RESTRICTED**: Tandoor's app, Apple Notes (iCloud), Google Keep, and the NYT Recipe Box.
- Instagram's personal saves collection could not be reached without an account; the public `#recipe` tag page was captured instead, which is where the 114M figure comes from.
- Prices are quoted verbatim from vendor pages and App Store listings on 20 July 2026. Fond, NYT Cooking, Things and Todoist do not render numeric prices on their public pages; those cells say so rather than guess.

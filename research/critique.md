# Critique — where the persona and jobs work sags

**Date:** 29 July 2026
**Scope:** an adversarial audit of [`personas.md`](./personas.md) and [`jtbd.md`](./jtbd.md), both written earlier in this research phase.
**Method:** every claim classified **confirmed / hypothesis / invented**, then filtered for the ones that drive design decisions while resting on nothing. Three verification greps were run against the corpus rather than trusting recall; they are recorded in [§5](#5-what-was-actually-checked) so this document is itself checkable.

**Why this exists.** Both audited documents are careful about marking `[?]` at the level of individual facts, and that care is real. It is also what makes them dangerous: **a document that visibly flags its small uncertainties reads as trustworthy about its large ones.** The large ones are structural, and none of them carries a `[?]`.

Per the house rule in [`research.md`](./research.md), each finding carries its implication.

---

## 1 · The flaw that conditions everything below

**The persona work is partly circular.**

The brief's §2 defines the audience as *"cooking lovers who are also optimisers."* The research was written against the brief, and its own analytical voice adopts the word — *"an optimiser's tool"* (Plan to Eat), *"the nerd-optimiser's choice"* (Tandoor), *"an optimiser re-checks the merged quantity by hand"* (pain 4), *"the optimiser's real choice today"* (pain 7). All four are the research describing the brief's persona back to itself. [`personas.md`](./personas.md) then built P-1 out of that research and presented it as evidence-grounded.

> brief → research → persona → validates brief

The only genuinely external anchor in that loop is one line of Paprika marketing: *"multi-device home cooks who shop systematically."* Mapping that onto *"cooking lovers who are also optimisers"* is **an inference made while writing the personas, not a finding recovered from the market.**

**Implication.** P-1 is presented in both documents as the best-evidenced persona. It is better described as *the brief's own hypothesis, wearing a competitor's marketing copy as a costume.* Every priority decision downstream inherits that.

---

## 2 · Claim-by-claim audit

✅ **confirmed** — traceable to vendor copy, a captured screen, or a documented cross-product pattern
⚠️ **hypothesis** — reasoned from evidence, but the step to the claim is inference
✖️ **invented** — no corpus counterpart; produced during writing

### 2.1 The framework itself — where the worst of it sits

| Claim | | Note |
|---|:--:|---|
| There are four distinct persona types | ✖️ | The corpus never segments users at all. The segmentation was created, not found. |
| P-1, P-3 and P-4 are *different people* | ✖️ | They could be one person in three moments — the systematic cook who also hoards reels and also wants their data out. **Nothing in the corpus tests this, and both documents assume it silently.** |
| Persona names and characterisations | ✖️ | Authored. *"Optimiser"* is borrowed from the research's own framing (§1), not from any user. |
| The 1–3 importance scale | ✖️ | Invented and uncalibrated. No anchor definitions were validated against anything; two analysts would produce different numbers. |
| Each of the 31 non-`[?]` scores | ✖️ | The leap from *"a vendor markets X"* to *"this persona values X at 3"* is unsupported by any method. |
| The ▽ rule — behaviour implies individual priority | ✖️ | **Ecological fallacy.** It infers one person's priority from aggregate platform statistics. |
| The admission threshold (external datum → main list) | ✖️ | A reasonable rule, invented for the occasion. |
| The MVP-core filter (P-1 = 3 **and** not covered) | ✖️ | Same. |
| *"17 of 48 cells unknown"* | ⚠️ | Arithmetically true, epistemically soft: **the denominator was chosen** by choosing 12 jobs and 4 personas. It reads as a measurement and is a property of the framing. |
| `[?]` is never averaged into a score | ✅ | Verified by grep — see [§5](#5-what-was-actually-checked). |
| No fabricated user quotes anywhere | ✅ | Every *Voice* block is marked `[?]` and substituted with a labelled corpus line. This held up. |

### 2.2 Persona claims

| Claim | | Note |
|---|:--:|---|
| Paprika, Tandoor, Mela, Plan to Eat audience wordings | ✅ | Vendor copy, with screens. |
| AnyList household pricing +$5/yr | ✅ | Vendor copy + [captured screen](./screens/t3-anylist-complete-pricing.png). |
| 114M reels on `#recipe` | ✅ | [Captured screen](./screens/t2-instagram-recipe-tag.png). |
| Mela *"does not collect any data"* | ✅ | Vendor copy, App Store confirmed. |
| P-3 age *"under ~45"* | ⚠️ | Correctly flagged `[?]`. The corpus's own estimate. |
| Household size 2–4 | ⚠️ | Correctly flagged. The brief's assumption. |
| P-1 is *"not a diet persona"* | ⚠️ | **Sourced to the brief (§2, §8), not to research** — a product decision projected onto a user, then used in [§4](#4-the-dangerous-list) to argue against a product feature. |
| *"The most evangelical users"* | ⚠️ | The corpus asserts it; nothing measures it. Flagged at the time. |
| Anti-personas | ⚠️ | §8's exclusions restated as people. Legitimate framing; not a discovery. |

### 2.3 Jobs

| Claim | | Note |
|---|:--:|---|
| J-1 — capture matters | ✅ | 114M reels; all five hard competitors market import. Strong. |
| J-2 — retrieval is pain #1 | ⚠️ | Eat Your Books and SuperCook as paying businesses are ✅. **The *ranking* as "pain #1" is the research's own synthesis**, itself desk-inferred. |
| J-3 — unit chaos across fifteen products | ✅ | Documented across the set. |
| J-4 — merge-and-order is the marketed mechanism | ✅ | Vendor copy, several products. |
| J-5 — sharing is table stakes | ✅ | Pricing evidence is unusually hard for this corpus. |
| J-6 — *"the library is the centre of gravity for 3 of 15"* | ⚠️ | **A fact about product architecture used as evidence about user desire.** A real inferential leap, made without comment. |
| E-1 — the fear tax | ⚠️ | That vendors compete on it is ✅; that users feel it is inference. |
| **E-2 as a *job* at all** | ✖️ | [`jtbd.md`](./jtbd.md) states it *"is not a feature and cannot be scheduled as one."* A thing that cannot be scheduled is a quality bar, not a job — **and it was placed in the MVP core regardless.** Category error. |
| E-3 — drift and the AI paywall | ⚠️ | Market drift documented ✅; the felt need inferred. |
| S-1, S-2 | ⚠️ | Thin. S-2's counter-evidence — a working shared Keep list already solves it — is stronger than its evidence. |
| Concrete details: *"six of us"*, *"third attempt"*, *"five years"*, *"three weeks"* | ✖️ | Rhetorical scaffolding for the formulations. Harmless in intent, but a reader can mistake them for findings. |
| Emotional outcomes, e.g. *"quietly keeping a copy elsewhere"* | ✖️ | The hedging behaviour was authored, not observed. |

---

## 3 · What held up

Recorded so the audit is not merely destructive:

- **No fabricated user speech.** Every *Voice* was marked `[?]` and given a labelled substitute. Under pressure to produce persona colour, nothing was invented.
- **`[?]` was never averaged**, including in the two ⚑ conflict cells (J-5 × P-1, J-5 × P-4) where a 2 would have been easy and wrong.
- **The wording discipline survived two languages.** Feature vocabulary is absent from all 43 English statement lines and all 19 Ukrainian ones — and the Ukrainian was audited *separately*, which caught two failures the English pass would have missed.
- **J-6 was added when challenged**, and the reason it was missing was recorded rather than quietly patched.

---

## 4 · The dangerous list

Claims that **drive design decisions** while resting on `[?]` or on invention. Ranked by blast radius.

| # | Decision it drives | What it actually rests on |
|---|---|---|
| **1** | **P-1 is primary** — orders the entire backlog | The circular derivation in [§1](#1--the-flaw-that-conditions-everything-below), plus one mapping made while writing. Nothing external nominates this person as the priority. |
| **2** | **The three MVP-core jobs (J-2, J-3, E-2)** — the build decision itself | Invented scores passed through an invented filter. **Move P-1 by one point on any row and the set changes.** |
| **3** | **Not designing downstream for P-3** — scored 1 ▽ on J-0 and J-4 | *"Dismal cook-through."* **Verified: the corpus contains no number for this anywhere.** An unquantified adjective about Cookpad/Pinterest aggregates, applied to an individual. |
| **4** | **"Calories close no job"** — could remove a locked §4 feature | The completeness of a job list derived from research that never asked about nutrition. **Absence of evidence used as evidence of absence.** |
| **5** | **Metric-only as the wedge** — the least reversible decision in the brief | *"Nobody constrains units"*, read as an open position. See below. |
| **6** | **Pulling export into MVP** (E-1 has no function) | P-4 = 3 is solid. P-1 = 2 rests on a single unsourced sentence. |
| **7** | **Researching P-2 first** | The 17/48 density, whose denominator was chosen here. |

### 4.1 The one most worth being wrong about — #5

Both documents read *"everyone converts units; nobody constrains them"* as a **vacancy**: an idea the market has not had. The opposite reading was never considered — that fifteen products preserve unit ambiguity **because users demand it**.

The corpus contains a fact that points that way, and it was cited while drawing the opposite conclusion: **Tandoor made unit conversions user-editable.** Products do not usually add configurability to something users are happy to have fixed. Crouton, similarly, sells metric/imperial conversion *as a feature* — it markets the flexibility, not the constraint.

There is no evidence either way, which is exactly the problem: **only the flattering interpretation was written down.** The decision is irreversible in practice — it is discovered as wrong after sixty recipes have been entered — and it is the sharpest idea in the brief.

---

## 5 · What was actually checked

Three greps were run against the corpus and the audited files rather than relying on memory. Recorded so this document can be re-run:

1. **Gendered pronouns for personas whose gender is nowhere stated.** Found **9 instances** of *his/him* across `jtbd.md` and the matrix artifact — P-1, P-3 and P-4 all silently rendered male. Corrected to they/them the same day; zero residual. *This was a live defect in published material, found only because the audit was run.*
2. **A number behind *"dismal cook-through."*** None exists — the phrase appears in `competitive-landscape.md`, `comparison.md` and `summary.md` and is unquantified in all three. It is the sole support for finding **#3** above.
3. **Whether the corpus names any segment.** It does use *"optimiser"* — four times, always in the research's own voice, never as reported data. This is the evidence for [§1](#1--the-flaw-that-conditions-everything-below).

---

## 6 · Three questions that would close the most

All three are **free, public and answerable this week**, without a single user interview.

### Q1 · Are P-1 and P-3 the same person?

**Closes:** findings 1, 2 and 3 at once — the top of the dangerous list.
**Why it matters:** if they are one person, the persona set collapses and **capture speed becomes a primary-persona problem rather than a secondary one** — which changes the MVP core directly.
**Where to look:** r/Cooking, r/MealPrepSunday and r/EatCheapAndHealthy, searching *"recipes I saved and never made"*. Paprika's App Store reviews and r/Paprika.
**What would falsify the split:** a single person describing **both** systematic shopping **and** a graveyard of saved links. One such post is enough.

### Q2 · Why do people actually abandon recipe managers?

**Closes:** findings 2 and 4, plus gaps G-1 and hypothesis H-3.
**Why it matters:** the claim that capture cost kills libraries is assertion-only, and the entire typed-record risk analysis rests on it.
**Where to look:** **Tandoor's GitHub issue tracker** — public, detailed, written by real users, free to read, and the highest-yield source available anywhere in this project. Then 1–3★ App Store and Play reviews for Paprika, Plan to Eat, AnyList, Crouton and Mela: one-star reviews state abandonment reasons that no marketing page ever will.

### Q3 · Is unit constraint an idea nobody had, or one everyone tried and abandoned?

**Closes:** finding 5 — the least reversible decision in the brief.
**Why it matters:** [§4.1](#41-the-one-most-worth-being-wrong-about--5). Only the flattering reading has been written down.
**Where to look:** **Tandoor's GitHub issues and pull requests on units and conversions.** They shipped user-editable conversions; there is almost certainly a thread explaining the pressure that produced it, and **that thread is the single most decision-relevant document that currently exists for this brief.** Then Paprika's forum threads on conversion, and Crouton's release notes and reviews mentioning metric/imperial.

---

## 7 · The one-line finding

> **Two of the three questions above point at the same place. Tandoor's issue tracker is the cheapest real-user evidence available to this project, it is free, and neither research document mentions it.**

Fifteen products were read through their marketing. Not one was read through its complaints.

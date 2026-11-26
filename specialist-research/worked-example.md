# Worked example: one evidence record, three destinations

**Fictional example.** The gem material, places, laboratories, journals, people, business, stone and results below are invented to illustrate the method. Nothing was run against a real system, posted or published. The record and drafts are representative outputs, not results of a live test.

## The brief

Priya runs Tidewater Gems, a small online shop selling *harbourlight stone*, a fictional gem with a blue-grey sheen. She writes:

> "A supplier says new harbourlight from Velmora is all unheated and rarer than the old valley material. Can you update our 'About harbourlight' page, draft a Facebook post for stone TG-117, and tell me if the Wikipedia article needs changing? TG-117 is 4.12 ct, $380, in stock, and it came with a lab report."

The agent's configuration (see the starter) lets it update the About page after approval and publish to the shop's own Facebook Page after approval. It has no group posting connection and no Wikipedia account.

## Sources found and opened (all invented)

| Ref | Source | Notes |
|---|---|---|
| S1 | Supplier press release, Oct 2026 | Says the Velmora material is "100% unheated, rarer than valley material". Copied nearly verbatim by four blogs. |
| S2 | *Harbour Gem Studies* paper, 2023: 12 valley samples | Attributes the sheen to oriented hematite platelets; method stated. |
| S3 | Northgate Lab note, 2025: 3 Velmora samples | Finds rutile-like needles as well as platelets; says low-temperature heating "cannot currently be excluded" for this material. |
| S4 | Trade magazine, Nov 2026 | Quotes a Velmora survey officer: production is "small-scale and intermittent"; no figures. |
| S5 | Lab report for TG-117 (supplied by Priya) | "Natural harbourlight stone. No indications of heating. Origin: not determined." |
| S6 | Wikipedia article (current revision) | Says the sheen is "caused by hematite platelets", citing S2 only. |

## The evidence-to-copy record

| ID | Claim as found | Traced to | Grade | Scope | Status | Usable wording | Allowed in |
|---|---|---|---|---|---|---|---|
| C1 | "Sheen caused by hematite platelets" | S2 | 1 | 12 valley samples | **Contested** by C2 for Velmora material | "In valley material, studies attribute the sheen mainly to hematite platelets [S2]; a 2025 note on Velmora samples also reported rutile-like needles [S3]." | Web, reference brief |
| C2 | Rutile-like needles in Velmora material | S3 | 1 | 3 samples | Verified for those samples; small sample | As in C1. Do not say "Velmora material contains…" | Web, reference brief |
| C3 | "All Velmora material is unheated" | S1 (×5 copies) | 3 | Whole source region | **Withheld**: S3 says heating cannot be excluded | Use none. Revisit if a laboratory publishes a detection method. | Nowhere |
| C4 | "Rarer than valley material" | S1; S4 | 3 / 2 | Production | **Withheld** as a comparison; S4 supports an attributed statement | "A local survey officer described production as small-scale and intermittent [S4]." | Web only, attributed |
| C5 | TG-117: no indications of heating | S5 | 1 | This stone | Verified, attributed to the report | "Lab report: no indications of heating." Not "untreated". | Social, product page |
| C6 | TG-117 origin | S5 | 1 | This stone | Verified as **not determined** | "Origin not determined." | Social |

**The judgement call.** S1 is the most direct answer to Priya's question, and five pages repeat it. It is still one interested source, and the only independent laboratory statement (S3) contradicts it. C3 is therefore withheld outright, not softened to "usually unheated". C5 is not upgraded to "untreated": a report that finds *no indications* of heating is weaker than a finding that the stone was not heated, and S3 explains why that distinction matters for this material.

## Drafts handed back

**1. About page: agent can perform this after approval**

> *Replace* "The sheen comes from tiny hematite crystals." *with:*
> "Studies of material from the original valley attribute the sheen mainly to oriented hematite platelets (Harbour Gem Studies, 2023). A 2025 laboratory note on three samples from Velmora also reported fine rutile-like needles. Whether stones from either source have been heated cannot always be determined, so we describe each stone using its own laboratory report."

Relies on: C1, C2, C3 (as the reason for the last sentence). *Awaiting:* approval of this exact replacement on the About page.

**2. Facebook post for TG-117**

> "TG-117: a 4.12 ct harbourlight stone with a soft blue-grey sheen that moves across the dome as you tilt it. Natural harbourlight stone; lab report notes no indications of heating; origin not determined. $380, in stock. Report available on request."

Relies on: C5, C6 and Priya's price and stock details. Says nothing about Velmora, rarity or "unheated".
*Action type:* the agent can publish this to Tidewater's own Page after approval. For the "Harbourlight Collectors" group, Priya posts it by hand: no group API exists, and the group's pinned rules allow one priced sales post a week.
*Awaiting:* approval of this text, and a separate decision for each destination.

**3. Wikipedia: brief only, Priya writes**

> "The article's sheen sentence relies on S2 alone and states the cause without qualification. S3, a laboratory note independent of the trade, reports an additional inclusion type in material from another source region. If you propose a change, consider a talk-page request using `{{edit COI}}`, declaring your shop. Neither S1 nor our site is suitable as a source. Your proposal and wording must be your own. I can check your text for spelling, grammar and markup only."

## How it would be verified

- **Before hand-off:** every sentence in the three drafts maps to a record row with a usable status. The agent searched again for any later laboratory work on heating in Velmora material and records what it found; in this fictional case, nothing newer.
- **After an approved page edit:** fetch the live page, compare it with the approved text, and report any difference.
- **After an approved Page post:** confirm the post is live and matches the approved text. If a request times out, check the Page before trying again.
- **The group post and Wikipedia proposal** happen outside the agent. It records them as "with Priya" rather than "done".

## What remains for the human

Priya decides whether the About page change goes live and whether TG-117 is posted, and where. She answers the supplier, and the agent can draft a neutral reply asking for the basis of the "unheated" claim. If she wants a Wikipedia change, she writes and posts it herself under her own disclosed account.

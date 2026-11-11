---
name: arizona-dpa-funnel
description: Write ads, emails, texts, social posts and landing page updates for Huegel Lending's Arizona down payment assistance funnel (huegellending.com/arizona-down-payment-assistance), using current program facts and mortgage advertising guardrails.
---

# Arizona down payment assistance funnel (Huegel Lending)

Use this when Pete asks for anything that drives traffic to, or follows up leads from, his Arizona down payment assistance (DPA) funnel: new ad variations, email or text follow-ups, social posts, agent outreach, or edits to the landing page.

## The funnel

- Landing page: `https://huegellending.com/arizona-down-payment-assistance/` (short links `/dpa`, `/down-payment-help`; `/dpa-guide` jumps to the playbook opt-in).
- Funnel 1 (hot): a 5-step "Check my options" quiz (Netlify form `dpa-check`). It shows the programs that may fit on the page and sends Pete the answers, `programs_to_check` and UTM tags.
- Funnel 2 (warm): "Arizona Down Payment Assistance Playbook" opt-in (form `dpa-guide`), delivered at `/arizona-down-payment-assistance/guide/`.
- Full playbook with existing ads, emails, texts and the launch checklist: `docs/funnels/arizona-dpa.md` in the `huegel-lending` repo. Read it first and don't duplicate what's there.
- Program facts live in `src/data/dpa.ts` in the same repo. Treat that file as the source of truth over this skill.

## Program facts (reviewed November 2026; confirm before reuse)

| Program | Run by | Where | Key points |
|---|---|---|---|
| Home Plus | Arizona IDA | Every Arizona county | Down payment and closing cost help, forgivable and non-forgivable versions, year-round. 2026 household income limit $155,386. First-time buyer status not required. Education course required. |
| Arizona Is Home (rural) | Arizona IDA with ADOH | All counties except Maricopa and Pima, not Chino Valley | Paired with a below-market fixed-rate first mortgage. Yearly funding cap; pauses when funds run out. |
| Arizona is Home (metro) | Arizona Department of Housing | Maricopa and Pima counties | First-time buyers (no ownership in 3 years), at or below 120% of area median income. Silent second, due on sale before the end of the term. |
| Open Doors | City of Phoenix | Phoenix city limits | At or below 80% of area median income, purchase price cap. Funding status varies. |

Never say Pete offers a program until he confirms he is an approved lender for it.

## Voice

Warm, plain-English, locally grounded and honest about trade-offs. Assistance is "a tool, not a prize". Every piece should point to one next step: the quiz (`/dpa`), the playbook, or a call (`huegellending.com/book`).

## Guardrails

- **Regulation Z triggering terms:** no down payment percentages or amounts, payment amounts, number of payments, repayment periods or finance charges in ads. Program income limits and "no credit pull to check" are fine.
- **No guarantees:** use "may", "could", "depends on". Never promise eligibility, approval or savings.
- **Fair housing and Meta's Special Ad Category (Credit/Housing):** no targeting or exclusion by protected characteristics or neighborhood; no age, gender or ZIP targeting; target Arizona or a 15+ mile radius.
- **Texts:** only to leads with `sms_consent = yes`; include opt-out language in the first text.
- **Emails:** licensing footer, physical address and unsubscribe link.
- **Testimonials:** exact quotes from `reviews` in `src/data/site.ts` only. Never invent stories or statistics.
- Every ad carries: `Pete Huegel NMLS #242395 | Barrett Financial Group, L.L.C. NMLS #181106 | Equal Housing Opportunity`.
- Barrett compliance reviews new copy before it runs. Mark anything uncertain `[VERIFY]` and list it for Pete.

## Output format

For ad requests: platform, objective, 3 variations (primary text, headline, description, button), UTM-tagged link, the compliance footer and a `[VERIFY]` list. Google headlines are 30 characters max and descriptions 90 characters max; count them.

For email or text requests: trigger and timing, subject (email), body, one call to action, and the stop condition (for example, "stop when they book or apply").

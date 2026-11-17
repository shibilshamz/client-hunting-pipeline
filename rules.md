# Hard Rules (every agent, every run — these never move)

## Sending
1. **Never send an email.** Only create Gmail drafts. Never call send_message, reply or forward.
2. Drafts stay in the Gmail **Drafts** folder (the Gmail connector can't create labels). Every draft is also
   listed with its link in `drafts/YYYY-MM-DD.md`.

## Money / credits ($0 budget)
3. **Never purchase anything.** Never call Lusha `purchase_options`, any RocketReach upgrade, Vibe Prospecting `show-pricing-plans`,
   or any upgrade/checkout tool. If a tool returns "out of credits" (HTTP 402), stop the run and report it.
4. **RocketReach is the main contact tool** (since 2026-11-17). Call RocketReach `account` at the start of a
   run (free). `person_search` is free. `person_lookup` uses `standard_lookup` (email only).
5. Budget per run: max 5 RocketReach `person_lookup` calls. Never use `premium_lookup`/`phone_lookup`,
   never `company_lookup` or `email_verify` unless Shibil asks. Respect rate limits (100 lookups/hour).
6. Never pay for phone numbers. Emails only.
7. **Lusha = backup only**, when RocketReach has nobody on the company domain: max 1 contact search +
   1 email reveal per run, `waterfallEnabled: false`, emails only. If Lusha has < 3 credits, skip it.
7b. **Apollo: DO NOT USE for now.** Tested 2026-09-23: on the Free plan Apollo blocks API access to people
   search and people enrichment ("not included in your Free plan"). Calling it wastes time. Only use Apollo
   if Shibil says he upgraded to a paid plan — then: max 2 email reveals per run, never phones, never buy.
8. Vibe Prospecting: only use if it has free credits left AND Lusha found no contact for a top company.
   Check cost first with `estimate-cost`. Never buy.

## Data quality
9. **Email priority** (approved by Shibil 2026-09-23):
   a. VERIFIED — decision-maker's email on the company domain, grade A/A- from RocketReach (or revealed by Lusha backup).
   b. PUBLIC — if RocketReach/Lusha have none, an email the company itself publishes (its website contact page or its own
      job post), e.g. info@ / support@. Address the decision-maker by name if RocketReach/Lusha found one ("Hi Omar,"),
      otherwise "Hi {Company} team,". Mark it PUBLIC in prospects.md.
   c. Nothing found → no draft; mark UNVERIFIED and move on. Never guess an address (no firstname@ guessing).
9b. **Collect other public contact details** for Shibil to use by hand: company phone, WhatsApp number,
   decision-maker's LinkedIn URL — only when published by the company itself or returned free by RocketReach search.
   Never pay for phone reveals (RocketReach or Lusha). Record them in the `other contacts` column of prospects.md.
   The robot never messages anyone on WhatsApp/LinkedIn/phone — Shibil decides.
10. **Dedup:** never research a company already in `prospects.md` (match on domain, then name).
    Never contact anyone in `do-not-contact.md`. One person, one email sequence, ever.
11. **No padding.** If fewer than 2 companies score ≥ 60, draft only those that do — or none — and say
    why (filters too narrow, signal pool exhausted).
12. Never invent a fact about a company. Every claim in an email must be traceable to the signal or
    the company's own website.

## Compliance (UAE, B2B)
13. Business email addresses only, about something relevant to their job.
14. Every email says in one short line where we found them (e.g. "saw your job post on Indeed") and has a
    plain opt-out line.
15. Anyone who replies "no" / "stop" / "unsubscribe" goes into `do-not-contact.md` the same day.
16. Don't scrape LinkedIn. Don't use LinkedIn automation tools.

## Privacy
17. Never name the anonymous HR client or their company in any email or file, and never use gendered
    words (she/her/he/him) for them in emails.

## WhatsApp (added 2026-10-12)
18. The robot **never sends WhatsApp messages** and never uses the WhatsApp Business API, bulk-sender tools,
    bots or "WhatsApp number checker" services. It only prepares messages + one-tap wa.me links; Shibil
    sends each one by hand from his WhatsApp Business app, max ~5 per day.
19. Only use numbers the company itself publishes (website, wa.me link, job post, Google Maps listing).
    Never guess numbers, never buy them, never use Lusha phone reveals.
20. WhatsApp only to UAE mobile numbers (9715XXXXXXXX) or numbers inside a published wa.me link.
21. One WhatsApp message per company, plus at most ONE short nudge after 3–4 days if no reply. Any "no" /
    "not interested" → do-not-contact.md. "Not now" → no more messages for 6 weeks.
22. One channel at a time: WhatsApp first when available; email only if WhatsApp gets no reply in 3 days.

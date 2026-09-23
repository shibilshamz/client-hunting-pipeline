# Hard Rules (every agent, every run — these never move)

## Sending
1. **Never send an email.** Only create Gmail drafts. Never call send_message, reply or forward.
2. Every draft gets the Gmail label `outreach` so Shibil can find them.

## Money / credits ($0 budget)
3. **Never purchase anything.** Never call Lusha `purchase_options`, Vibe Prospecting `show-pricing-plans`,
   or any upgrade/checkout tool. If a tool returns "out of credits" (HTTP 402), stop the run and report it.
4. Call Lusha `account_usage` at the start of a run. If fewer than 3 credits remain, do NOT use Lusha:
   do the free steps (signals + scoring), save the shortlist, and report "Lusha credits exhausted".
5. Credit budget per run: max 1 contact search + max 2 email reveals (≈3 credits).
6. Never reveal phone numbers (5 credits each). Reveal `emails` only.
7. Use Lusha-only reveals (`waterfallEnabled: false`) so no third-party vendor credits are used.
8. Vibe Prospecting: only use if it has free credits left AND Lusha found no contact for a top company.
   Check cost first with `estimate-cost`. Never buy.

## Data quality
9. **No verified email → no draft.** Mark the prospect UNVERIFIED in prospects.md and move on.
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
17. Never name the anonymous HR client or her company in any email or file.

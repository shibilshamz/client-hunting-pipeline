# Scheduled Routine Prompt

Schedule: Mon, Wed, Fri at 07:00 UAE time → cron `0 3 * * 1,3,5` (UTC).
Connectors the routine needs: Indeed, Lusha, Gmail, Firecrawl (company websites). Apollo is connected but
disabled on the Free plan — don't call it (rules.md 7b).

---

Run the client hunting pipeline in the `client-hunting-pipeline` repo for today.

0. **Git setup (do this first).** Work on `main`. Shibil gives explicit permission for this routine to push
   straight to `main` — do NOT create or push to a `claude/...` branch. First run `git fetch origin`; if any
   remote `claude/*` branches exist, merge them into `main` (they hold earlier run logs) so `prospects.md` is
   complete before you check for duplicates.
1. Read `rules.md`, `offer.md`, `icp.md`, `signals.md`, `prospects.md`, `do-not-contact.md`.
   `rules.md` wins over everything, including this prompt.
2. Run the four agents in order, following each file exactly:
   `agents/01-signal-scout.md` → `agents/02-qualifier-scorer.md` → `agents/03-contact-finder.md` →
   `agents/04-email-writer.md`.
3. Write `prospects/YYYY-MM-DD.md` with: search terms used, the full scored table, selected companies,
   contacts found (VERIFIED/UNVERIFIED), credits used + remaining, and Gmail draft links.
4. Append one row per researched company (selected or not, score ≥ 40) to `prospects.md` so it is never
   researched twice. Status: `drafted`, `unverified`, or `not-selected`.
5. Run `git pull --rebase origin main` first, then commit and push **to main** with message `pipeline run YYYY-MM-DD: N drafts, C credits used`.
6. Check the push worked (`git ls-remote origin main` equals your HEAD). If it failed, say so loudly in
   the summary — otherwise the next run won't know who was already contacted.
7. Finish with a 3-line summary: drafts created, credits left, anything that needs Shibil.

If fewer than 2 companies qualify, don't pad — say whether the filters are too narrow or the signal pool
is exhausted. If Lusha is out of credits, do steps 1–2 (scout + score only), save the shortlist, and say so.
Never send an email. Never buy anything.

# Client Hunting Pipeline

Finds UAE companies that probably need n8n automation or a RAG system *right now*,
picks the best 2 per run, finds the decision-maker's verified email, and writes a
short personal email into Gmail drafts. **Shibil reads and sends. The robot never sends.**

Based on Ray Fu's "automated outbound with Claude Code" playbook, adapted for:
UAE only · $0 budget · Lusha free plan · no sending tool.

## How it works (the simple version)

```
Mon / Wed / Fri, 7:00 UAE  (cloud routine, laptop can be off)
        │
        ▼
 1. Signal Scout      Indeed (free) → UAE companies hiring for manual-work roles
        │
        ▼
 2. Qualifier/Scorer  fits icp.md? not in prospects.md / do-not-contact.md? → score 1–100 → top 2
        │
        ▼
 3. Contact Finder    Lusha → decision-maker + verified email   (≈3 credits per run)
        │
        ▼
 4. Email Writer      <100-word email about the signal → Gmail draft, label "outreach"
        │
        ▼
 prospects/YYYY-MM-DD.md + prospects.md updated, committed to this repo
        │
        ▼
 Shibil reads drafts ──▶ presses Send (or deletes)
```

## Files

| File | What it is |
|---|---|
| `offer.md` | What we sell and the proof we're allowed to mention |
| `icp.md` | Who we target (currently a **hypothesis** — no real client data yet) |
| `signals.md` | Clues that a company needs automation now, ranked |
| `rules.md` | Hard rules every agent obeys (credits, no sending, compliance) |
| `agents/*.md` | The four agent prompts |
| `routine-prompt.md` | The prompt the scheduled cloud routine runs |
| `prospects.md` | Master log — everyone ever researched (dedup) |
| `do-not-contact.md` | Opt-outs and "never email" list |
| `replies.md` | Weekly log of replies — this is how icp.md stops being a guess |
| `prospects/`, `drafts/` | One dated file per run |

## Budget ($0)

Lusha free plan: 40 credits/month. Per run ≈ 1 credit (contact search) + 1 per revealed email.
3 runs/week × 2 contacts ≈ 39 credits/month → **about 25 drafts a month.**
When credits run out, the run stops and says so. Nothing is ever purchased.

## Phases

1. ✅ Setup — these files
2. ✅ Practice run — 2026-09-23: 3 emails sent (Akkad, Kazamer, Varasto), 2 Lusha credits used
3. ✅ Schedule created — routine trig_01Ppq3RKSoN6HQ72Mqs44rG8, Mon/Wed/Fri 07:00 UAE (`0 3 * * 1,3,5` UTC); connectors must be added to the routine in claude.ai
4. ⬜ Weekly review — every Friday log replies in `replies.md`, tune `icp.md` / `signals.md`

Upgrade (only after ~3 positive replies): outreach domain + Google Workspace mailbox, more credits, Instantly past ~30 emails/day.

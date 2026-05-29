# 2026-05-29 — Nines Product Session: manual workflow + team structure (Nare)

**Date**: 2026-05-29 · captured via Granola
**Source**: <https://notes.granola.ai/t/2b434895-0005-4e28-824d-6528e3a7f2b7-008umkv4>
**Granola title**: "PLACEHOLDER Nines Product Session"
**Attendees referenced**: Nare (Nartarlamazyan — presented), Enoc, Luiyit, broader Nines team
**Related artifacts**: [`2026-05-28 product walk-through`](./2026-05-28-product-walkthrough.md) — likely the deeper notes from that same/adjacent session

> Nare (Nartarlamazyan) presented a comprehensive manual workflow for handling AI generation **outside** the platform. Centers on a dedicated creative-technologist (CT) team, batch-based processing, category/brand-specific workflow templates, and a two-tier QC system. Enoc proposed splitting the platform into `ct.nines.com` (internal CT workflow) + a separate client-facing approval interface.

## Decisions

- **Manual workflow stays the source of truth** for now; will stress-test requirements before any platform build.
- **Batch-based processing**: **40–50 SKUs per batch** (refined from the 25–50 range floated in the 05-28 walk-through).
- **Same team members assigned to a batch end-to-end** — no handoffs mid-batch to avoid knowledge-transfer loss.
- **Two-tier QC**:
  - **Raw AI outputs** — 70–80% accuracy acceptable.
  - **Final retouched assets** — 100% accuracy required.
- **Client selection happens BEFORE retouching** — client picks from 4–5 generations per pose; only the selected variant gets retouched.
- **Variants per asset**: generate **6–7 variants** with live QC.
- **Target rejection rate**: ≤ 5% if process followed.
- **Daily coordination**: status calls 3x/week, 10 minutes each.
- **Platform direction (Enoc)**:
  - Build `ct.nines.com` as the internal creative-technologist workflow surface.
  - Keep a **separate client-facing interface** for approvals.
  - Frame.io-style review (multi-asset review, selection, comments).

## Open questions

| Question | Raised by | Status |
|---|---|---|
| Same meeting as 2026-05-28 walk-through, or a distinct follow-up session? | (us) | verify |
| `ct.nines.com` — new subdomain, separate app, or module inside Nines? | (us) | open |
| Frame.io vs build-our-own for client multi-asset review surface? | (team) | to evaluate |
| Hiring plan + budget for 3–4 full-time CTs + a PM? | (us, ask Mindy) | open |
| Avatar / pose / background / lighting library — per brand or shared base + brand overrides? | (us) | open |
| Where do brand-specific workflow templates (Vivian/ComfyUI) live + version control? | (us) | open |

(Mirrored in [`../open-questions.md`](../open-questions.md).)

## Action items

| Owner | Item | Due | Status |
|---|---|---|---|
| Nare | Finalize the proposed pipeline structure in FigJam (input → CT prep → generation → QC → client selection → final delivery) | this week | open |
| Hiring | Recruit 3–4 full-time creative technologists | rolling | open |
| Hiring | Recruit / assign a project manager to bridge data accuracy + team coordination | TBD | open |
| Nare | Define avatar + pose libraries per brand | TBD | open |
| Aaron + Mark | Define background/lighting specifications per category + per brand (Vans: tops ≠ bottoms; shoes distinct) | TBD | open |
| CT team | Define category-specific Vivian/ComfyUI workflow templates per brand; mark popular categories (tops, bottoms, sneakers) as reusable | TBD | open |
| 5thPivot (Luiyit + Lu) | Scope `ct.nines.com` — internal CT workflow surface + separate client-facing approval interface | post 2026-05-28 walkthrough | open |
| 5thPivot | Automated folder structure + naming convention handling | TBD | open |
| All | Daily status calls (3x/week, 10 minutes) | recurring | open |

(Mirrored in [`../action-items.md`](../action-items.md).)

## Notes

### Manual workflow process (Nare's proposal)

Current pain points:
- Input data sharing is **unorganized**, complex to navigate, manual downloads.
- No folder logic or naming conventions from clients.
- Multiple download/upload cycles create inefficiency.

Proposed pipeline (in order):
1. **Input data organization** with automated download.
2. **Data preparation** for creative technologists.
3. **Sharing with CT team**.
4. **Generation** using dedicated brand/category workflows.
5. **Internal QC + client selection**.
6. **Final delivery** (retouched).

### Team structure + resource requirements

- **Dedicated CT team**: 3–4 people full-time.
- **Project manager** role essential:
  - Owns data accuracy + coordination.
  - Reviews shared client assets.
  - Prepares summary decks for CTs.
  - Bridges teams (client ↔ CT ↔ retouching ↔ delivery).
- **Batch model**: 40–50 SKUs per batch; same humans on a batch start-to-finish.

### Workflow templates + asset management

- **Category-specific** Vivian/ComfyUI workflows **per brand**.
- Popular categories (tops, bottoms, sneakers) → reusable templates.
- Distinguish **repetitive vs customized** categories.
- **Avatar + pose libraries per brand** required.
- Background / lighting specs vary by category and brand:
  - **Vans**: different lighting for tops vs bottoms.
  - **Shoes**: distinct specifications vs apparel.
- Generate **6–7 variants per asset** with live QC.

### Client selection + QC

- Two-tier QC (raw 70–80% acceptable; final retouched must be 100%).
- Client selection BEFORE retouching: 4–5 generations per pose to pick from.
- Client validates **pose**, **mood**, **avatar–product relationship**.
- Review surface options: Nines (current) or Frame.io (multi-asset review).
- Target rejection ≤ 5% with the process followed.

### Platform direction (Enoc)

- Current Nines platform **not suitable** for this workflow.
- Proposal: build specialized tools.
  - **`ct.nines.com`** — internal creative-technologist workflow surface.
  - **Separate client-facing approval interface** (Frame.io-style review for multi-asset selection + comments).
- Automated folder structure + naming convention handling needed.
- **Manual process first** — stress-test the requirements before committing to the platform build.
- **Daily status calls** (3x/week, 10 min) for coordination during the manual run.

## Raw source

Granola: <https://notes.granola.ai/t/2b434895-0005-4e28-824d-6528e3a7f2b7-008umkv4>

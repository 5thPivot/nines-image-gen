# 2026-05-28 — Product walk-through

**Date**: 2026-05-28 · Thursday · 80 minutes
**Attendees**: Luiyit (you), Nare (transcribed as "Nari"), Mindy, Mark, Aaron, Alex, Elizabeth, Rebecca, Bitter, Katrina (joining from Germany)
**Source**: live session — internal meeting summary

> First end-to-end pipeline walk-through with the new content lead (Nare) so she can build a complete map. Anchor: deliver three brands (**North Face, Vans, Timberland**, ~500 SKUs) under an optimized **manual** workflow. Full automation deferred (~6 months out). Surfaced 14 engineering deliverables on the 5thPivot side, most of which Luiyit committed to on the mic.

## Decisions

- **No full pipeline automation now** — full automation = ~6 months out.
- **Hybrid workflow**: image generation stays **outside Nines** (ChatGPT, Veronica Beard tool, ComfyUI) for flexibility across LLMs and pipelines. Nines stays as the **client review interface**.
- **Pose strategy**: scrape brand sites → generate a library of variations → client selects from our library. Don't try to replicate exact reference poses.
- **Client selection model**: deliver ~5–10 variations per SKU; client picks one per angle; only the selected variation gets retouched.
- **Sell variation as a feature**: position the abundance of options as a privilege so clients feel ownership.
- **Batch-based tracking**: work in batches of **25–50 SKUs**, not per-image.
- **Tooling to evaluate**: Frame.io for QC and client review.
- **One owner per pipeline step**: data ingestion, generation, QC, retouching, delivery — each gets a single responsible person.
- **Friday brainstorm**: Nare maps the pipeline in FigJam in a working session.
- **Canonical store = S3**: Luiyit confirmed on mic that all generated assets will live in S3 as the canonical store. Output folder structure pending — must be defined with Aaron + Mark.

## Open questions

| Question | Raised by | Status |
|---|---|---|
| Is Frame.io worth the seat cost as a QC layer? | (team) | to evaluate |
| How do we handle inpainting for accessories (3D scenes, bags, hats) vs apparel? | (team) | open |
| Where does QC validation logic live once generation moves out of Nines? | (team) | open |
| Nari vs Nare — same person (transcription) or two distinct people? | (us) | open — likely same |
| Elizabeth on this call = Vans client contact or a different Elizabeth in PM? | (us) | verify |

(Mirrored in [`../open-questions.md`](../open-questions.md).)

## Action items

| Owner | Item | Due | Status |
|---|---|---|---|
| Nare | High-level pipeline draft in FigJam | before Friday | open |
| All | Working session — finalize pipeline map + per-step owners | Friday 2026-05-29 | scheduled |
| Elizabeth + Bitter + Nare | Define client communication guidelines (what to expect per round) | TBD | open |
| Luiyit | Decide AWS account approach (new dedicated vs Nines existing) + report back | this week | open |
| Luiyit | Sync with Lu — define what we need from Nines on the infra side; hand off list to Nines team this week | this week | open |
| Luiyit | Begin S3 storage layer + auto-move pipeline | after Friday session | open |
| Luiyit | Auto-push back to Nines once images selected/QC'd | TBD | open |
| Luiyit | Comment notifier (SKU-level when client comments in Nines) | ~couple of days | open |
| Luiyit | CSV extract + spreadsheet sync (V1/V2 feedback columns per SKU) | TBD | open |
| Luiyit | Threshold-based CSV trigger (e.g. when 15 SKUs commented) | TBD | open |
| Luiyit + Aaron | S3 folder structure per component (avatars / poses / try-on / inpainting / QC / final) | TBD | open |
| Luiyit | Auto-create spreadsheet on client upload (Drive folders + metadata + deadline + link) | TBD | open |
| Luiyit | Input validation at upload time (resolution, required angles, naming convention) | TBD | open |
| Luiyit | Prescriptive folder structure (Round 1 / QC selected / Retouching / Final) | TBD | open |
| Luiyit | Investigate / fix broken Nines QA model (retrain per-brand or remove) | TBD | open |
| Luiyit | Regeneration trigger when client rejects an asset | TBD | open |

(Mirrored in [`../action-items.md`](../action-items.md).)

## Notes

### Current workflow + pain points

1. Clients upload assets into Nines → products area.
2. Image generation happens **outside Nines** (ChatGPT, Veronica Beard tool, ComfyUI) for flexibility across LLMs and pipelines.
3. Mark / Aaron / Alex craft prompts per SKU manually.
4. Nines built-in QA is **broken**: marks accurate generations as failed AND lets obvious failures through.
5. Generated images live on **individual creatives' machines** — no shared canonical location.
6. Client comments are **not synced back** to the assets they reference.
7. Naming conventions differ per brand; no unified logic.

### Brand-specific notes

- **North Face**: provided a PDF library of poses (scraped to use as references).
- **Vans, Timberland**: no pose library; team will scrape the brand website.
- **Veronica Beard**: prompts had to be crafted via ChatGPT instead of Nano Banana because ChatGPT gave better results for this brand.
- **Pearlman**: shown live as the example of the current Nines client review experience.

### What Luiyit committed to on mic

- All generated assets will live in **S3 as the canonical store**.
- Output structure from the generation pipeline still pending — must be defined with **Aaron + Mark** so folders/keys map cleanly to **brand / SKU / angle / variation**.
- Once structure locked, layer an **automated flow** on top to move (or copy) selected images from S3 into whatever location Nines needs for client review — creatives keep working in their preferred tools while Nines stays the review surface for the client.
- Sync with **Lu today** to define what we need from Nines on the infrastructure side. Goal: hand off that list this week so the Nines team can stand it up on their end and share access with us.

### Process notes

- Team has hired ~6 QC people — they will manually QC if needed.
- Deliverable target: **5,000 final images** (10 per SKU on average across 500 SKUs).
- Generation will use Veronica Beard / ComfyUI workflows; the workflow file itself can change per brand without changing the core system.
- Retouching policy: **only retouch after the client selects**, never before.

## Raw source

Internal meeting summary at `OBS/Nines/Product Walk-through/Product Walk-through - Summary.md`.

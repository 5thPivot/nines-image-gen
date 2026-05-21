# 2026-05-20 — Integration kickoff with Aaron and Mark

**Date**: 2026-05-20 · Tuesday
**Attendees**: Aaron, Mark, Mindy, Heidi, Enoc, (Lu/Luiyit added afterwards via Nines Grit channel)
**Granola**: <https://notes.granola.ai/d/a9191175-c32d-4c81-b946-05157e91ec3b>
**Related artifacts**: Figma board "Breakdown process" ([sources/pdfs](../sources/pdfs/)), GitHub notebook [comfyui-inpaint-cropstitch-nb2](https://github.com/amortegui84/comfyui-inpaint-cropstitch-nb2)

> First sync where 5thPivot was pulled in. Mindy wants Aaron/Mark to work directly with us (not Eric) on the cloud + integration plan. New `nines_grit` Slack channel created to host this workstream.

## Decisions

- The image gen team will work with **5thPivot directly**, not via Eric, for cloud deployment and integration planning.
- A new Slack channel **`nines_grit`** owns this workstream.
- 5thPivot's job is to **shadow Aaron/Mark first**, then propose the AWS architecture — no premature design.
- A **master diagram** has to exist before any infra work starts: what's automatable vs manual, end-to-end UX flow, brand-specific setup.
- Cloud deployment will be tested **in parallel** with the current manual workflow — manual stays the source of truth until cloud is proven.

## Open questions

| Question | Raised by | Status |
|---|---|---|
| Cost ownership ($5–6k per 10k images in API credits + cloud compute) — who pays? | (us) | open |
| How are different naming conventions per brand normalized? | (us) | open |
| Avatar / pose library — built per brand or shared? | (us) | open |
| What's genuinely automatable vs always-manual in this workflow? | Enoc | open |
| Does NVIDIA upscaling (under test) replace OpenAI inpainting or layer on top? | (us) | open |

(Mirrored in [`../open-questions.md`](../open-questions.md).)

## Action items

| Owner | Item | Due | Status |
|---|---|---|---|
| Mindy | Create "Nines Grit" Slack channel + add team | 2026-05-20 | done |
| Aaron + Mark | Prepare process documentation | next meeting | open |
| Enoc | Bring Lu into the loop (backend / cloud infra) | 2026-05-21 | done |
| Heidi | Set up FigJam for visual QA process with Terry | TBD | open |
| (us) | Schedule afternoon meeting with 5thPivot, Aaron, Mark | 2026-05-20 | done |
| Mark | Continue bags project with two new team members joining 7AM | ongoing | in progress |
| (us) | Test cloud deployment in parallel while manual workflow ships | ongoing | open |

(Mirrored in [`../action-items.md`](../action-items.md).)

## Notes

### AI image generation workflow (Aaron's demo)

- Uses a **JAR/SCREAM model** to auto-detect objects and create masks.
- Masks go to **OpenAI for inpainting** — replaces / enhances specific regions.
- A **smart stitcher** positions the enhanced regions back on the original image with **edge fade** so seams disappear.
- Net effect: more detail in specific regions without re-rendering the full picture.
- The whole pipeline is documented in **GitHub** with implementation instructions (notebook linked above).
- Team is currently **testing NVIDIA upscaling** for video/image enhancement — not in production yet.

### Current platform integration challenges (Eric's view)

- Eric is **blocked**: waiting for more data + examples to wire this into the Nines platform.
- Need **prompts and examples** showing how the retouching team would change logos / elements via AI mask creation.
- The local tools are powerful but the **browser-based Nines experience** doesn't expose them — that's the gap.
- Every brand requires **manual setup**:
  - Different naming conventions per client.
  - Category-specific processing rules.
  - Avatar + pose library curation.

### Technical infrastructure status

- APIs run **locally per machine** today. Doesn't scale.
- Target = **AWS server for batch processing**, multiple API accounts to handle volume.
- Current throughput: ~30 images per API call. Target: **2–4k images daily**.
- Cost ballpark: **$5–6k for 10k images** in API credits, plus cloud compute.

### North Face / Vans current project — bags

- Mark is **120% focused** on the bags project. **1 month timeline**.
- Running **manual + automated in parallel**:
  - Manual = better lighting + quality.
  - Automated = consistency issues.
- **Terry** (Berlin, available 8PM EST) doing QA / retouching support.
- Two more team members **joining tomorrow 7AM** to absorb the bags load.

### Integration planning / next steps

- We need a **comprehensive process map** before any implementation.
- 5thPivot will **shadow Aaron/Mark** to understand the actual flow.
- Master diagram must define:
  - Automatable vs manual splits.
  - User experience from platform → processing → back.
  - Brand-specific setup steps.
- **Lu (Luiyit)** will lead the cloud infrastructure side once we have the process map.

## Raw source

Granola export: [`../sources/granola/1. Integration plan.md`](../sources/granola/1.%20Integration%20plan.md) (formatted screenshot in `.jpg`).

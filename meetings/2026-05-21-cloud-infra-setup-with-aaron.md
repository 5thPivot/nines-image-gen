# 2026-05-21 — Cloud infrastructure setup with Aaron

**Date**: 2026-05-21 · afternoon (per action item D3 from kickoff)
**Attendees**: Aaron, Enoc, Lu — first sync where Lu meets Aaron (Enoc intros)
**Granola**: <https://notes.granola.ai/d/bf8caf60-ea5d-4db9-a03a-d9ec598b1a47>
**Related artifacts**: GitHub notebook [comfyui-inpaint-cropstitch-nb2](https://github.com/amortegui84/comfyui-inpaint-cropstitch-nb2)

> First working session between Aaron and 5thPivot's backend lead. Aaron demoed the actual workflow (ComfyUI + Florence + Fal/Replicate). Outcome: agreed modular cloud architecture, separate mini admin from main Nines platform initially.

## Decisions

- **Modular cloud architecture** chosen — 4 separate pipeline modules (try-on / inpainting / variations / upscale), each behind its own JSON API.
- **AWS on-demand server provisioning per user session** — replaces today's single-user local servers (which conflict if shared).
- **Mini admin interface** built separately from main Nines platform initially — avoids integration complexity until pipeline proven.
- **Google auth** with 3-user limit for pilot — covers internal users only.
- **S3** for image uploads + execution history tracking.
- Each module exposes APIs that can later plug into existing Nines workflows.

## Open questions

| Question | Raised by | Status |
|---|---|---|
| Open-source models for lingerie/swimwear content — which models, where hosted? | (us) | open |
| Fine-tuning effort + cost for quality content-filter-friendly results? | (us) | open |
| QA bottleneck — debate over client selection (show 25 generations) vs pre-filtering (show 5 best) — which wins? | Aaron | open |
| Master avatar library with pose conventions — who builds, who maintains? | (us) | open |
| Aaron's contract resolution timeline — when can he fully transition to Nines? | Enoc | open |

(Mirrored in [`../open-questions.md`](../open-questions.md).)

## Action items

| Owner | Item | Due | Status |
|---|---|---|---|
| 5thPivot (Lu) | Build mini admin interface (workflow management) | TBD | open |
| 5thPivot | S3 storage for input image uploads | TBD | open |
| 5thPivot | Workflow execution via JSON APIs (calls Fal/Replicate-backed modules) | TBD | open |
| 5thPivot | Execution history + results tracking | TBD | open |
| 5thPivot | Google auth (3-user pilot) | TBD | open |
| Aaron + 5thPivot | Define 4 module API contracts (try-on / inpainting / variations / upscale) | TBD | open |
| Aaron | Identify open-source models suitable for lingerie/swimwear (private-host) | TBD | open |
| Aaron + Heidi | Decide QA approach — client selection vs pre-filtering | TBD | open |

(Mirrored in [`../action-items.md`](../action-items.md).)

## Notes

### Team introductions & project context

- Enoc introduced Lu (longtime collaborator, described as "AI before AI").
- Aaron based in Medellín, Colombia. Currently a consultant — **restricted from touching prompts/workflows by contract conflicts**. Consults through another company to avoid talent-poaching issues. Cannot fully transition to Nines until contract resolved.
- Mark already integrated into Nines team (note: Granola transcribed as "Marc" — same person).
- Project anchor: **5,000-image delivery target in one week**.

### Current workflow architecture (Aaron's demo)

- Automated inpainting system built on **ComfyUI nodes**.
- **Florence** model handles automatic element recognition (glasses, face, upper/lower body, objects). → This is what we've been calling "JAR/SCREAM" — likely Granola mistranscription of "Florence". **Resolves open question #9.**
- Automatic masking → image-to-image processing.
- Smart crop + stitch for precise placement.
- System exports as **JSON API** — no UI needed for execution.
- Backed by **Fal** and **Replicate** APIs for compute.
- Dockerized, running successfully today.
- **Concurrent processing**: ~30 simultaneous API calls through Fal.
- Limitation: **single-user servers** — multiple users conflict.
- Proposed fix: **AWS on-demand server provisioning per user session**.

### Proposed cloud integration strategy

- **Mini admin interface** for workflow management:
  - Upload images to S3.
  - Select + execute workflows via JSON APIs.
  - Track execution history + results.
  - Auth via Google (3-user pilot).
- **Modular pipelines** — each callable via API:
  1. Try-on module
  2. Inpainting module
  3. Variations module
  4. Upscale module
- Each module connects via APIs to existing Nines workflows later.
- **Kept separate from main platform initially** to avoid integration complexity.

### Process challenges & quality control

- **Content filtering**: regular APIs block lingerie / swimwear content.
  - Workaround: open-source models hosted on private servers.
  - Need custom fine-tuning for quality.
- **QA bottleneck** for final delivery:
  - Target: **4–5 generations per requested image** (deliver 5 final → generate ~25).
  - Manual QA review required before client delivery.
  - Open debate: let client pick from 25, or pre-filter to 5 best?
- **Data organization complexity**:
  - SKUs / categories / subcategories / styles create naming convention challenges.
  - Master avatar library with pose conventions needed.
  - Spreadsheet coordination between client data and workflow inputs.

## Raw source

Granola: <https://notes.granola.ai/d/bf8caf60-ea5d-4db9-a03a-d9ec598b1a47>

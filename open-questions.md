# Open questions

Single source of truth for unanswered questions. Each row tagged with source meeting + raise date + status.

Add new questions here AND mirror in the source meeting's notes. Close them with a one-line resolution when answered (don't delete — keep the audit trail).

## Open

| # | Question | Source | Raised | Owner | Priority |
|---|---|---|---|---|---|
| 1 | Cost ownership: $5–6k per 10k images in API credits + cloud compute. Who pays? | [2026-05-20](./meetings/2026-05-20-integration-kickoff.md) | 2026-05-20 | TBD | high |
| 2 | How are different naming conventions per brand normalized? | [2026-05-20](./meetings/2026-05-20-integration-kickoff.md) | 2026-05-20 | (us, when we shadow) | medium |
| 3 | Avatar / pose library — built per brand or shared? | [2026-05-20](./meetings/2026-05-20-integration-kickoff.md) | 2026-05-20 | Aaron + Mark | medium |
| 4 | What's genuinely automatable vs always-manual in the workflow? | [2026-05-20](./meetings/2026-05-20-integration-kickoff.md) | 2026-05-20 | Aaron + Mark | high |
| 5 | Does NVIDIA upscaling replace OpenAI inpainting or layer on top? | [2026-05-20](./meetings/2026-05-20-integration-kickoff.md) | 2026-05-20 | Aaron | low |
| 6 | How will crop shots beyond full/upper/lower body get implemented? | [2026-05-21](./meetings/2026-05-21-pipeline-deep-dive.md) | 2026-05-21 | Image gen team | low |
| 7 | When will pocket-rendering bug (hand positioning) be fixed? Workaround in place. | [2026-05-21](./meetings/2026-05-21-pipeline-deep-dive.md) | 2026-05-21 | Image gen team | low |
| 8 | Reference photos from phone cameras break proportions — who owns the input-photo standards doc? | [2026-05-21](./meetings/2026-05-21-pipeline-deep-dive.md) | 2026-05-21 | TBD (likely us) | medium |
| 10 | "Nano Banana" — what's the actual vendor / API? | [2026-05-21](./meetings/2026-05-21-pipeline-deep-dive.md) | 2026-05-21 | (us, ask Mark) | low |
| 11 | What is the "core 4 WF automation logic" Aaron is building? Which 4 workflows? | [2026-05-21 action plan](./meetings/2026-05-21-action-plan.md) | 2026-05-21 | (us, ask Aaron) | high |
| 12 | What does "scenes per category" mean concretely — examples? | [2026-05-21 action plan](./meetings/2026-05-21-action-plan.md) | 2026-05-21 | Nare | high |
| 13 | Where does Nare's client-questions doc live? Need link. | [2026-05-21 action plan](./meetings/2026-05-21-action-plan.md) | 2026-05-21 | (us, ask Nare/Heidi) | medium |
| 14 | Data requirements per category — what shape? Schema we agree on? | [2026-05-21 action plan](./meetings/2026-05-21-action-plan.md) | 2026-05-21 | Nare | high |
| 15 | Open-source models for lingerie/swimwear content — which models, where hosted? | [2026-05-21 cloud infra](./meetings/2026-05-21-cloud-infra-setup-with-aaron.md) | 2026-05-21 | Aaron | medium |
| 16 | Fine-tuning effort + cost for content-filter-friendly results? | [2026-05-21 cloud infra](./meetings/2026-05-21-cloud-infra-setup-with-aaron.md) | 2026-05-21 | Aaron + (us) | medium |
| 17 | QA approach — client picks from 25 vs pre-filter to 5 best? | [2026-05-21 cloud infra](./meetings/2026-05-21-cloud-infra-setup-with-aaron.md) | 2026-05-21 | Aaron + Heidi | medium |
| 18 | Master avatar library with pose conventions — who builds, who maintains? | [2026-05-21 cloud infra](./meetings/2026-05-21-cloud-infra-setup-with-aaron.md) | 2026-05-21 | TBD | medium |
| 19 | Aaron's contract resolution timeline — when can he fully transition to Nines? | [2026-05-21 cloud infra](./meetings/2026-05-21-cloud-infra-setup-with-aaron.md) | 2026-05-21 | Enoc | high |
| 20 | Is Frame.io worth the seat cost as a QC layer? | [2026-05-28 walk-through](./meetings/2026-05-28-product-walkthrough.md) | 2026-05-28 | (us, evaluate) | medium |
| 21 | How do we handle inpainting for accessories (3D scenes, bags, hats) vs apparel? | [2026-05-28 walk-through](./meetings/2026-05-28-product-walkthrough.md) | 2026-05-28 | Aaron + Mark | medium |
| 22 | Where does QC validation logic live once generation moves out of Nines? | [2026-05-28 walk-through](./meetings/2026-05-28-product-walkthrough.md) | 2026-05-28 | (us + image gen team) | high |
| 23 | AWS account approach — new dedicated account vs Nines existing? | [2026-05-28 walk-through](./meetings/2026-05-28-product-walkthrough.md) | 2026-05-28 | Luiyit | high |
| 24 | "Nari" in 2026-05-28 walk-through = "Nare" (same person, transcription variance)? | [2026-05-28 walk-through](./meetings/2026-05-28-product-walkthrough.md) | 2026-05-28 | (us, verify) | low |
| 25 | Elizabeth in walk-through = same Elizabeth as Vans client contact? | [2026-05-28 walk-through](./meetings/2026-05-28-product-walkthrough.md) | 2026-05-28 | (us, verify) | low |
| 26 | Is the 2026-05-29 Granola session same meeting as 2026-05-28 walk-through, or a distinct follow-up? | [2026-05-29 Nare workflow](./meetings/2026-05-29-nines-product-session-nare-workflow.md) | 2026-05-29 | (us, verify) | low |
| 27 | `ct.nines.com` — new subdomain, separate app, or module inside Nines? | [2026-05-29 Nare workflow](./meetings/2026-05-29-nines-product-session-nare-workflow.md) | 2026-05-29 | Enoc + Luiyit | high |
| 28 | Hiring plan + budget for 3–4 full-time CTs + dedicated PM? | [2026-05-29 Nare workflow](./meetings/2026-05-29-nines-product-session-nare-workflow.md) | 2026-05-29 | Mindy | high |
| 29 | Avatar / pose / background / lighting library — per brand or shared base + brand overrides? | [2026-05-29 Nare workflow](./meetings/2026-05-29-nines-product-session-nare-workflow.md) | 2026-05-29 | Nare + image gen team | medium |
| 30 | Where do brand-specific Vivian/ComfyUI workflow templates live + version control? | [2026-05-29 Nare workflow](./meetings/2026-05-29-nines-product-session-nare-workflow.md) | 2026-05-29 | CT team | medium |

## Answered

| # | Question | Answer | Closed |
|---|---|---|---|
| 9 | What does "JAR/SCREAM model" actually refer to? | **Florence** (Microsoft vision foundation model). "JAR/SCREAM" was a Granola mistranscription. Confirmed by Aaron in [2026-05-21 cloud infra sync](./meetings/2026-05-21-cloud-infra-setup-with-aaron.md). | 2026-05-21 |

## Closed without answer

(none yet)

# Glossary

Vocabulary the image gen team drops without defining. Update as new terms surface in syncs.

## Models / tools in active use

- **Florence model** — Microsoft's vision foundation model. Handles automatic element recognition (glasses, face, upper/lower body, objects) for the inpainting pipeline. Aaron confirmed 2026-05-21 (cloud infra sync). **Replaces what we had been transcribing as "JAR/SCREAM"** — that was a Granola mistranscription of "Florence".
- **Fal** — Compute API used to run the inpainting workflows. ~30 concurrent calls per server. Lives behind the ComfyUI JSON-API export.
- **Replicate** — Secondary compute API used alongside Fal for workflow execution.
- **OpenAI (inpainting)** — Receives the masks from Florence and rewrites the masked regions. Standard OpenAI image-edit API endpoint.
- **Smart stitching** — In-house step that composites the inpainted regions back into the original image with **edge fade** so seams disappear. Lives in the GitHub notebook ([`amortegui84/comfyui-inpaint-cropstitch-nb2`](https://github.com/amortegui84/comfyui-inpaint-cropstitch-nb2)).
- **Nano Banana** — 4K generation model. In use right now for the bags project. (Vendor / source unconfirmed — log when we find out.)
- **Image2** — Secondary tool used with grain removal, applied when texture issues show up.
- **NVIDIA upscaling** — Under evaluation for video + image enhancement. Not in production.
- **ComfyUI** — Node-based stable diffusion workflow tool. The team's notebook (linked above) plugs the inpaint + crop + stitch nodes together.

## Pipeline concepts

- **Inpainting** — Regenerating a specific region of an image based on a mask + prompt, leaving the rest untouched. Used here for **detail recovery** (logos, stitching, textures) — not full-scene generation.
- **Stitching** — Compositing the inpainted region back into the source image with feathered edges so the seam isn't visible.
- **Avatar** — A brand-specific synthetic model identity. Includes a **pose library** + **lighting library** so the same avatar can render across angles without drifting.
- **Try-on** — Rendering a garment on an avatar across multiple angles. Implemented as a **collage technique** that preserves avatar likeness when generating new views.
- **Crop shots** — Tight image crops of product detail. Today the pipeline produces full / upper / lower body only; tighter crops need dev work.
- **Spreadsheet logic** — The driver for batch combinations: which avatar × which garment × which pose. Pipeline reads this and queues API calls.
- **Naming conventions** — Filename-driven contracts linking input garments to specific outputs. Each brand has its own — that's a normalization gap.

## Project / business terms

- **SKU** — Stock-keeping unit. A single garment variant. The team handles 200–500 per brand per delivery cycle.
- **Tech pack** — Apparel-industry term for the full product spec sheet (measurements, materials, construction notes). The QC team's background. Influences what they look for in review.
- **First-delivery approval rating** — % of generated images the client accepts on first review. Team target: 90%+.
- **Creative director** — Client-side decision-maker who owns visual direction. Team executes their vision; doesn't lead creatively.

## Workflow / operational terms

- **Core 4 WF automation logic** — Aaron's deliverable as of 2026-05-21. Four workflow automations whose exact scope is still TBD. Likely maps to the focus areas (avatars / try-on / QC / inpainting) or to specific brand workflows. **Open question — ask Aaron.**
- **Scenes per category** — The set of must-have shots required for each product category (e.g. for bags: front, side, back, top, diagonal × on-model + cutout). Anchor for client confirmation; downstream work (poses, spreadsheet templates) is gated on locking these in.
- **Data requirements per category** — Nare's deliverable, due 2026-05-22 evening. Defines the input data shape per product category — what fields, what photo standards, what metadata.
- **Spreadsheet templates for input data** — Nare's follow-up deliverable, gated on client confirmation of poses. Templates clients fill in to drive the batch combinations (avatar × garment × pose).
- **Product UX** — Mindy + Nare's Friday (2026-05-23) walkthrough. First explicit nines-platform-side surface discussion in our thread.

## Cloud architecture (proposed)

- **Mini admin interface** — Separate web app (NOT inside main Nines platform initially). Upload images → S3, pick workflow, fire JSON API, watch execution history. Google auth with 3-user pilot cap.
- **Modular pipelines** — 4 independent module APIs: **try-on**, **inpainting**, **variations**, **upscale**. Each exposes its own JSON contract; Nines workflows later call them.
- **AWS on-demand server provisioning** — Spin up a per-user-session server so multiple users don't conflict on a single-user ComfyUI box. Replaces today's local-only setup.
- **Content-filter workaround** — Regular APIs block lingerie/swimwear. Plan: open-source models on private servers + custom fine-tuning.
- **Hybrid workflow** — Generation runs **outside Nines** (ChatGPT, Veronica Beard tool, ComfyUI). Nines stays as the **client review interface**. Locked in 2026-05-28 walk-through after seeing pain points of in-platform QA.
- **Canonical S3 store** — All generated assets land in S3 (5thPivot side). Folder/key schema pending — must map to brand / SKU / angle / variation. Defined with Aaron + Mark before automation layer is built on top.
- **Batch-based tracking** — Track progress at the **batch** level (**40–50 SKUs per batch** per Nare's 2026-05-29 session, refined from the 25–50 range floated 2026-05-28). Same humans on a batch start-to-finish to avoid handoff loss.
- **Pose library strategy** — Scrape brand sites → generate a library of pose variations → client picks from our library. Don't try to match exact reference poses.
- **Client selection model** — Deliver 5–10 variations per SKU; client picks one per angle; only the selected variation gets retouched. Retouching policy: never before selection.
- **Frame.io** — Under evaluation (2026-05-28) as a QC + client review tooling layer. Seat cost is the open question.
- **Pearlman** — Brand client used in 2026-05-28 walk-through as the live example of the current Nines client review experience.

## Workflow process + roles (Nare 2026-05-29)

- **Creative technologist (CT)** — Role that runs the actual generation work (prompts, Vivian/ComfyUI workflows, variant production). Hiring target: **3–4 full-time**.
- **Project manager (PM)** — Bridge role: owns data accuracy + coordination, reviews shared client assets, prepares CT-ready summary decks. **Essential — non-negotiable per Nare.**
- **Two-tier QC** — **Raw AI outputs**: 70–80% accuracy acceptable. **Final retouched assets**: 100% required. Different humans / different bars.
- **6–7 variants per asset** — Generation policy with live QC during the run.
- **4–5 generations per pose for client selection** — What the client picks from before any retouching. Client validates pose, mood, and avatar–product relationship.
- **5% max rejection rate** — Target if the process is followed end-to-end.
- **Daily status cadence** — Status calls **3×/week, 10 minutes** during the manual run.
- **`ct.nines.com`** — Enoc's proposed internal CT workflow surface. Separate from the client-facing approval interface. Frame.io-style multi-asset review on the client side. Stress-test the manual process first.
- **Repetitive vs customized categories** — Distinction that gates template reuse. Popular categories (tops, bottoms, sneakers) get reusable Vivian/ComfyUI templates; customized categories get one-offs per brand.
- **Per-brand background / lighting specs** — Vary by category × brand (e.g. Vans: tops ≠ bottoms; shoes distinct). Tracked separately from the global pose library.

## Roles inside the workstream

See [`people.md`](./people.md) for the human roster. Functional roles below:

- **Image gen team** — Aaron + Mark + new hires. Owns the pipeline.
- **Retouching** — Terry. Manual fixes on top of pipeline output.
- **QC** — Heidi + Terry. Reviews every image before client delivery.
- **Platform integration** — Eric (Nines side, currently blocked).
- **Cloud infra** — Us (5thPivot — Lu + Luiyit).

# 2026-05-21 — Pipeline deep dive with Aaron and Mark

**Date**: 2026-05-21 · Wednesday
**Attendees**: Aaron, Mark, image gen team only (no Nines process discussion this round)
**Granola**: <https://notes.granola.ai/d/b757bb04-a5b5-431b-93fe-cd64ba4de57f>
**Related artifacts**: Figma board "Breakdown process" ([sources/pdfs](../sources/pdfs/)), training deck [Google Slides](https://docs.google.com/presentation/d/1gu1m6FpqsBcyrceRQcOCTBFzjvSLGM9-/edit)

> Sync focused exclusively on the image gen team's pipeline — how it works today, what's adding people, what's broken. Nothing about Nines platform integration yet. They're trying to **recruit more AI image generation specialists**.

## Decisions

- No process changes this meeting — knowledge-transfer only.
- The team is **actively expanding** with more AI image gen specialists (not yet introduced to us).

## Open questions

| Question | Raised by | Status |
|---|---|---|
| How do you produce "crop shots" beyond full / upper / lower body? Current pipeline can't. | Aaron | open |
| How will pocket rendering bug be fixed (hands don't position correctly)? | Aaron | open (workaround in place) |
| Reference photos from phone cameras break proportions — who owns input-photo standards doc? | Aaron + Mark | open |
| Documentation for "optimal input photo standards" — who writes it? | (us) | open |

(Mirrored in [`../open-questions.md`](../open-questions.md).)

## Action items

| Owner | Item | Due | Status |
|---|---|---|---|
| Mark | Continue overnight prompt work for bags project | ongoing | in progress |
| Image gen team | Recruit specialists for inpainting / pose library / try-on pipeline | rolling | open |
| (us, eventually) | Write input-photo standards doc for clients | TBD | open |
| Heidi + Terry | QC review every image (industry tech-pack background helps) | ongoing | in progress |

(Mirrored in [`../action-items.md`](../action-items.md).)

## Notes

### AI product pipeline overview

- Automated system producing AI imagery across **3+ brands today**, expanding toward **8**.
- Per brand: **200–500 SKUs → ~5,000 images + video content**.
- Three focus areas:
  1. **Avatar creation** — brand-specific pose + lighting libraries.
  2. **Try-on generation** — same avatar across multiple angles via collage technique.
  3. **Quality control** — automated where possible, manual review on every image.
- Customer profile: **creative directors who lead vision**. The team translates intent, does NOT lead creatively.
- Required **first-delivery approval rating: 90%+**.
- Live brands: North Face, Ferragamo, Timberland, Vans.

### Technical workflow

- **Avatar creation**: brand-specific poses + lighting libraries built upfront.
- **Try-on generation**: collages keep avatar likeness consistent across angles.
- **Auto-inpainting**: detail recovery (stitching, logos, textures) — same JAR/SCREAM + OpenAI pipeline from sync 1.
- **API-based cloud system** for batch processing.
- **Spreadsheet logic** drives automated combinations (which avatar × which garment × which pose).
- **Naming conventions** link garments → outputs deterministically.

### Known limitations / workarounds

- **Pockets don't render correctly** when hand positioning is involved. No fix yet.
- **Crop shots** stuck at full / upper / lower body. Anything tighter needs dev work.
- **Color accuracy** breaks when input lighting varies — biggest single quality risk.

### Current urgent project — bags

- **8 bags total, 7 views each** (front, side, back, top, diagonal among them).
- **Very short deadline** — whole team collaborating.
- Input photos come **from phone cameras** → quality + proportion inconsistencies.
- **Size accuracy** is critical — AI struggles with dimensional understanding (bag scale relative to model).
- **Studio lighting + shadows + brand guidelines** must match exactly.
- Tooling in use right now for bags:
  - **Nano Banana** → 4K generation.
  - **Image2** with grain removal → texture issues.

### Team collaboration / next steps

- Mark is **leading technical implementation**, working overnight on prompts.
- Hiring specialists in three areas:
  - Inpainting processes for detail recovery.
  - **Pose library development per brand.**
  - Try-on pipeline completion.
- **QC team reviews every image** — they have industry background in tech packs.
- **Documentation needed for optimal input photo standards** so clients deliver photos the pipeline can actually use.
- Immediate priority: divide bags work across available team members.

## Raw source

Granola export: [`../sources/granola/2. Pipeline.md`](../sources/granola/2.%20Pipeline.md) (formatted screenshot in `.jpg`).

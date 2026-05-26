# Nines Image Generation — Knowledge Base

Parallel workstream to the main Nines platform. Captures everything we learn about the **image generation team's pipeline** (Aaron + Mark) so we can plan the AWS deployment and integration without losing context between meetings.

> This is a documentation repo, not a code repo. Code lives elsewhere (linked from `sources/links.md`).

## TL;DR — what this project is

The image generation team produces **AI-generated product imagery** for high-end fashion brands (North Face, Ferragamo, Timberland, Vans, plus a pipeline expanding toward ~8 brands). Per brand they handle **200–500 SKUs producing ~5,000 images + video**, with a **90%+ first-delivery approval bar**. Clients are creative directors; the team translates, doesn't lead creatively.

Today the pipeline runs **locally on individual machines**, hitting ~30 images per API call. Target: cloud-batched, **2–4k images daily**. That cloud move is what we (5thPivot) are being brought in for.

We are NOT yet touching the Nines platform integration — that's blocked on Aaron/Mark documenting their process so Eric can build it in. Our scope first is shadowing the workflow and planning AWS infra.

## Who's who

See [`people.md`](./people.md) for full roster + roles + time zones.

Short version: **Aaron + Mark** drive image gen, **Nare** owns content/data/Product UX, **Heidi** owns QA, **Mindy** is Nines PM, **Eric** owns Nines platform integration, **Terry** is the Berlin retoucher, **Lu (us)** owns cloud backend (building at [5thPivot/5p-nines](https://github.com/5thPivot/5p-nines)), **Enoc** facilitates.

## Map of this repo

| Path | What lives there |
|---|---|
| [`meetings/`](./meetings) | Date-prefixed notes per sync. Each has decisions + action items + open questions + raw notes. |
| [`people.md`](./people.md) | Roster, roles, time zones, who-acts-on-what. |
| [`glossary.md`](./glossary.md) | Vocabulary the team drops without defining (JAR/SCREAM, Nano Banana, Image2, inpainting, etc). |
| [`open-questions.md`](./open-questions.md) | Single source of truth for unanswered questions. Each row tagged with date + source meeting. |
| [`action-items.md`](./action-items.md) | Aggregated TODO list with owner + due + status. |
| [`sources/pdfs/`](./sources/pdfs) | Figma board exports — full pipeline breakdown (5 process PDFs + 1 training pptx). Compressed copies. |
| [`sources/pdfs-originals/`](./sources/pdfs-originals) | Original uncompressed PDFs (~200MB total). Reference only. |
| [`sources/granola/`](./sources/granola) | Raw Granola exports (markdown + screenshot). |
| [`sources/links-original.md`](./sources/links-original.md) | Original flat URL list. Curated version in [`sources/links.md`](./sources/links.md). |
| [`sources/links.md`](./sources/links.md) | External resources with context. |

## How to read this

**First time?** Read in this order:
1. This README (you're here)
2. `meetings/2026-05-20-integration-kickoff.md` — first sync, sets the frame
3. `meetings/2026-05-21-pipeline-deep-dive.md` — pipeline details
4. `glossary.md` to decode anything that confuses you
5. `sources/links.md` for the Figma board + training deck

**Coming back for a meeting?** Skim the latest `meetings/*.md` and `open-questions.md`. Add a new file under `meetings/` with the same template.

## Meeting template

Every new meeting should follow `meetings/_template.md`. Copy it, date-prefix the filename, fill it in. Don't re-invent structure per meeting — it makes the history grep-able.

## Conventions

- Filenames are kebab-case, date-prefixed (`YYYY-MM-DD-slug.md`).
- One `meetings/*.md` per sync. Don't merge multiple syncs into one file even if they're the same day.
- Decisions, action items, open questions live in their own dedicated trackers AND in the source meeting. The trackers are the index; the meeting is the why.
- Don't edit raw `sources/granola/*.md` — those are the audit trail. Re-process into `meetings/*.md` instead.

## Status

| What | Where we are |
|---|---|
| Pipeline understanding | Three syncs done (kickoff, pipeline deep dive, cloud infra with Aaron). Modular cloud architecture agreed. |
| Cloud deployment plan | Build started — Lu owns AWS infra at [5thPivot/5p-nines](https://github.com/5thPivot/5p-nines). |
| Nines platform integration | Decoupled — mini admin app separate from main Nines initially. Module APIs plug in later. Eric still blocked on prompts/examples. |
| Tooling inventory | Mostly confirmed. "JAR/SCREAM" resolved to Florence. Fal + Replicate documented. Nano Banana vendor still unconfirmed. |

## Open questions surface

See [`open-questions.md`](./open-questions.md). High-priority ones right now:

- Cost ownership: $5–6k per 10k images in API credits + cloud compute. Who pays?
- Avatar/pose library — built per brand or shared?
- Naming conventions per client — who normalizes?
- What part of the workflow is genuinely automatable vs always-manual?

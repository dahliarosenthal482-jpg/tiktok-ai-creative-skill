# VP-US-003 Video Data Quality Report

Review Date: 2026-08-07

Selected: 30 unique videos

Quality Distribution: A=0, B=25, C=5

## Quality Matrix

|Dataset range|Selection Tier|Quality Grade|Count|Missing Fields|Verification Status|Usage Permission|Analysis Readiness|
|---|---|---|---:|---|---|---|---|
|VPV-001–010|A|B|10|Direct URL, Creator/ID/account/followers, Likes/Comments/Shares/Saves, audio, playable scenes, first product appearance|Identity/commerce/product association verified; creative playback incomplete|Read-only analysis; no media reuse|Commerce and caption-pattern analysis ready; scene analysis not ready|
|VPV-011–025|B|B|15|Direct URL, Creator/ID/account/followers, engagement, audio, scenes, per-video positive commerce|Identity/views/product association verified; zero orders/GMV observed in window|Read-only analysis; no media reuse|Relative traffic/caption-pattern analysis only|
|VPV-026–030|C|C|5|Same as Tier B plus very weak performance evidence|Identity/source/product association verified; trend relevance only|Read-only analysis; no media reuse|Visual/text trend reference only; not core training data|

## Completion Gate

- Selection Tier assigned: PASS.
- Quality Grade assigned: PASS.
- Missing fields explicit: PASS.
- Source/product association status: PASS.
- Duplicates excluded: PASS.
- Evidence classes separated: PASS.
- Usage permission recorded: PASS.
- Complete playable Hook/Scene/Product Integration analysis: FAIL.

Collection task status: `EXECUTED`.

Full Video Intelligence status: `INCOMPLETE` because no selected record is Quality A and playable creative evidence is absent.

## Per-Video Grade Index

- Quality B / Tier A: VPV-001–VPV-010.
- Quality B / Tier B: VPV-011–VPV-025.
- Quality C / Tier C: VPV-026–VPV-030.

No record was promoted to Grade A merely because it had GMV or Orders.

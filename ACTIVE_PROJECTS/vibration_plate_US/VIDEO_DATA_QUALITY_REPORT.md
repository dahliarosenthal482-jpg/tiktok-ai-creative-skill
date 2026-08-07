# VP-US-003-R1 Video Data Quality Report

Review Date: 2026-08-07

Original Dataset: 30 unique videos

Verified Set: 10 unique videos — Commerce Validation=5; Traffic Validation=5

Corrected original distribution: Tier A=10, Tier B=0, Tier C=20; Quality A=0, B=10, C=20.

Verified Set quality distribution: Quality A=0, B=10, C=0.

## Quality Matrix

|Dataset|Selection Class|Quality|Count|Evidence|Missing Fields|Readiness|
|---|---|---|---:|---|---|---|
|VPV-001–VPV-010|Original Tier A|B|10|Stable Video/Product IDs and per-video commerce/performance|Direct URL, creator, engagement, playback|Commerce/caption-level analysis only|
|VPV-011–VPV-025|Tier C after R1 downgrade|C|15|Stable IDs, product association and 12–647 Views|Meaningful traffic benchmark, engagement, direct URL, creator, playback|Trend reference only|
|VPV-026–VPV-030|Tier C|C|5|Stable IDs and weak trend signal|Strong performance plus identity/engagement/playback|Trend reference only|
|R1 Commerce Verified Set|Commerce Validation|B|5|Video ID, Product ID, GMV, Orders, Views, Date, cover path and screenshot|Direct URL, creator, engagement, playback|Commerce prioritization ready; scenes not ready|
|R1 Traffic Verified Set|Traffic Validation|B|5|Declared Views-descending benchmark, 79.7K–160.2K Views, Product IDs, traffic labels, cover paths and screenshot|Direct URL, creator, engagement, playback|Traffic prioritization ready; organic/scene analysis not ready|

## Original Tier B Re-audit

All 15 original RELIFE Tier B records were downgraded. They ranked only inside a zero-order product subset, had 12–647 Views, and had no Likes, Comments, Shares or Saves. This does not meet the traffic-validation threshold.

Downgraded count: 15.

## Completion Gate

- Ten-record Verified Set: PASS.
- Five commerce-validated records: PASS.
- Five traffic-validated records under declared benchmark: PASS.
- Unsupported original Tier B removed: PASS.
- Source screenshots committed: PASS.
- Missing fields explicit: PASS.
- AD vs Natural/unknown separated: PASS.
- Direct playable Hook/Scene/Product Integration evidence: FAIL.
- Quality A record: FAIL.

Task status: `EXECUTED`.

Deep Video Intelligence status: `PARTIAL / INCOMPLETE`.

No record was promoted to Quality A merely because it had GMV, Orders, high Views or a cover thumbnail.

# Video Source Matrix

Project: vibration_plate_US

Task ID: VP-US-003 / VP-US-003-R1

Market: United States TikTok Shop

Collection Window: Kalodata displayed windows 2026-07-29 to 2026-08-04 (global video search) and 2026-07-06 to 2026-08-04 (RELIFE product detail); collected 2026-08-07.

Usage Permission: Read-only analysis of visible data in the user's authorized Kalodata session. No source media was downloaded or republished.

## Source Entries

|Source ID|Selected Videos|Source|Evidence|Confidence|Verification Status|Risk|
|---|---:|---|---|---|---|---|
|VID-SRC-001|10|Kalodata US Video & Ads search, keyword `vibration plate`, displayed 7-day window|Video ID from cover asset; caption/duration; displayed GMV, Orders, Views, publish date; associated Product ID from product cover|Medium|Verified in visible signed-in table on 2026-08-07|Currency displayed as `¥`; no conversion attempted. Creator, direct TikTok URL, engagement and playable timeline unavailable.|
|VID-SRC-002|20|Kalodata RELIFE product detail ID `1729386006181548061`, displayed 30-day window|Video ID, caption/duration, displayed USD GMV, Orders, Views, publish date and direct product association|Medium|Verified in visible signed-in product video table on 2026-08-07|Creator, direct TikTok URL, engagement and playable timeline unavailable. Zero GMV/orders cannot prove absence of later sales outside displayed window.|

Source URLs:

- `https://www.kalodata.com/video`
- `https://www.kalodata.com/product/detail?id=1729386006181548061&language=zh-CN&currency=USD&region=US&dateRange=%5B%222026-07-06%22%2C%222026-08-04%22%5D&cateValue=%5B%5D`

## Per-Video Traceability

|Dataset IDs|Video IDs|Source ID|Product Association|Collection Date|Confidence|Status|
|---|---|---|---|---|---|---|
|VPV-001–VPV-010|7603191848135314718; 7662767009171574030; 7662927236860890398; 7628577773920996638; 7663110782778903838; 7666177498652167438; 7666234405022878989; 7510829962765667614; 7660511649928875278; 7630152948177227021|VID-SRC-001|Specific Kalodata Product ID retained for every row|2026-08-07|Medium|Selected Tier A; Quality B|
|VPV-011–VPV-025|7531476418354597151; 7669439959547301133; 7663232707974925599; 7669452353208159502; 7668654775872851213; 7670121117054455071; 7670200858105171213; 7669761651570216206; 7661378200475421982; 7667328320765250829; 7670121245329116446; 7662642578407378190; 7664626674868194590; 7668385765696572686; 7668281598072114446|VID-SRC-002|RELIFE Product ID 1729386006181548061|2026-08-07|Low|Downgraded to Tier C; Quality C by VP-US-003-R1|
|VPV-026–VPV-030|7665679357624601869; 7667601275747388685; 7666086858148908301; 7666861595712032013; 7662173974687763742|VID-SRC-002|RELIFE Product ID 1729386006181548061|2026-08-07|Low–Medium|Selected Tier C; Quality C|

## URL Boundary

Kalodata exposed stable Video IDs and cover-asset identities but did not expose direct TikTok Video URLs in the inspected tables. Dataset `Video URL` is therefore `Unavailable`; the corresponding Kalodata Source URL remains the auditable record. A guessed TikTok URL was not created.

## VP-US-003-R1 Classification Override

- Original VPV-011 through VPV-025: downgraded from Tier B to Tier C. Their 12–647 Views and missing engagement do not validate meaningful traffic.
- Direct Video URL remains `Unavailable`; no URL was guessed.

## VP-US-003-R1 Verified Set Traceability

|Set|Video IDs|Source|Selection Evidence|Screenshot Evidence|Status|
|---|---|---|---|---|---|
|Commerce Validation|7603191848135314718; 7662767009171574030; 7662927236860890398; 7628577773920996638; 7663110782778903838|Kalodata US Video & Ads search, GMV descending|Product ID, positive per-video GMV/orders, Views and Date|`EVIDENCE/kalodata_vibration_plate_gmv_desc_20260807.png`|Verified, Quality B|
|Traffic Validation|7656098323740265742; 7596936239232683277; 7635048871382633741; 7666033402969361695; 7592601750364851486|Kalodata US Video & Ads search, Views descending|Five highest-view eligible product-associated records remaining after commerce reservation; 79.7K–160.2K Views|`EVIDENCE/kalodata_vibration_plate_views_desc_20260807.png`|Verified, Quality B|

Every verified record has an observed cover path in the form `https://img.kalocdn.com/tiktok.video/{Video ID}/cover.png`. This is a cover asset, not a direct TikTok video URL or verified first frame.

# Market Source Matrix

Project: vibration_plate_US

Task ID: VP-US-002-UPGRADE-v1.1-REVISION

Executor: WORK-MARKET-001

Schema: Source ID · Source Type · Source Role · Evidence · Information Covered · Confidence · Status

Status: EXECUTED — WAITING SUPERVISOR REVIEW

## Source Registry

|Source ID|Source Type|Source Role|Evidence|Information Covered|Confidence|Status|
|---|---|---|---|---|---|---|
|SRC-001|Kalodata Commerce Data|Market Signal|Existing `kalodata_vibration_plate_us_30d_top10.csv`, `kalodata_vibration_plate_us_30d_rank11_30.csv` and retained normalized table in `COMMERCE_INTELLIGENCE.md`|30-day US product-link ranking; ASP; GMV; Video GMV; Live GMV; Product Card GMV for 30 links; Orders/Units for ranks 11–30; period 2026-07-06 to 2026-08-04|Medium overall; High for retained ranks 11–30 rows; top-10 units unavailable|Available — derived project table retained; original export files are not stored in the current repository tree|
|SRC-002|Amazon Customer Review|Customer Insight|13 visible Verified Purchase reviews documented in `CUSTOMER_INTELLIGENCE.md`; Amazon Parent ASIN B0FP2JPLZ6; collected 2026-08-06|Customer-reported purchase motivations, use scenarios, language, sound/comfort concerns and outcome uncertainty across Black, White and Silver family variants|Medium for recurring signals; Low for single-review signals|Available — parent-family customer evidence only; not TikTok comments and not Product Truth|
|SRC-003|Product Production Ready|Product Truth|`PRODUCT_PRODUCTION_READY.md`, Task VP-US-001-FINALIZE|HTM identity; TikTok Product ID; Black/White selling SKUs; Silver rejection; Visual Lock; included Resistance Bands; approved facts, claims and restrictions; temporary $49.99 classification|High within approved project scope|Approved project entry — read-only for this task|
|SRC-004|Owner Task Brief|Product Truth; Validation|User task assignments for VP-US-002 Upgrade and Revision|Project/task scope, executor, existing-data boundary, protected areas, required repair items and status requirement|High|Owner Authorized|
|SRC-005|Existing Kalodata Narrative Analysis|Content Insight; Market Signal|`kalodata_vibration_plate_us_30d_report.md` as referenced by existing VP-US-002 records; normalized limitations retained in `VIDEO_INTELLIGENCE.md`|Summarized Hook, Scene, CTA and Selling Angle patterns; isolated Merach/HOPHORSE performance examples|Low–Medium|Partially Available — raw video records and original report are not stored in the current repository tree|
|SRC-006|Commerce Intelligence|Market Signal|`COMMERCE_INTELLIGENCE.md`, derived from SRC-001|Competitor ranking, price bands, channel contribution, available units, GMV concentration and data-quality limitations|Medium|Derived Analysis — Executed, not independently sourced|
|SRC-007|Video Intelligence|Content Insight|`VIDEO_INTELLIGENCE.md`, derived from SRC-005 and existing planning notes|Observed/retained content-pattern summaries and complete list of missing per-video fields|Low–Medium|Incomplete — not a raw competitor-video database|
|SRC-008|Customer Intelligence|Customer Insight|`CUSTOMER_INTELLIGENCE.md`, derived from SRC-002|Amazon review scope, recurring customer signals, purchase motivations, usage scenarios, concerns and customer language|Medium|Derived Analysis — Customer Insight only|
|SRC-009|Competitive Strategy Map|Market Signal; Content Insight|`COMPETITIVE_STRATEGY_MAP.md`, derived from SRC-001, SRC-003, SRC-006 and SRC-007|Premium/Core/Entry positioning, premium education opportunity, similar-price competition and HTM counter-strategy|Medium for commerce position; Low–Medium for content interpretation|Inference clearly labeled — Executed, waiting review|
|SRC-010|Content Commerce Analysis|Content Insight|`CONTENT_COMMERCE_ANALYSIS.md`, derived from SRC-002, SRC-003, SRC-007 and SRC-008|Attention/Interest/Desire/Action framework; playback versus purchase distinction; objection and CTA test directions|Low–Medium|Future Test Direction — not verified conversion causality|
|SRC-011|Market Opportunity Analysis|Market Signal; Content Insight|`MARKET_OPPORTUNITY_ANALYSIS.md`, derived from SRC-001–SRC-010|Market gap, product/content opportunity and suggested strategy|Medium|Derived Analysis — Executed, waiting review|

## Evidence Class Boundary

- Product Truth: only approved product-entry and Owner-authorized scope facts. Customer or competitor statements do not change Product Truth.
- Customer Insight: Amazon parent-family review evidence. It may inform language, motivation and objection analysis but does not prove HTM outcomes.
- Market Signal: Kalodata estimates and their project-level derived commerce analysis. GMV or channel contribution does not independently prove creative causality.
- Content Insight: retained competitor-pattern summaries and derived adaptations. Missing raw video records keep exact hook, scene and CTA conclusions provisional.

## Data Integrity Notes

- The structured rank11–30 table sums to $380,744.49; it is used instead of the legacy narrative approximation of $394.2K.
- Orders/Units are unavailable for ranks 1–10 and are not inferred.
- No creative matrix is registered as competitor evidence.
- No TikTok comment, fabricated video record or newly collected external data is registered.

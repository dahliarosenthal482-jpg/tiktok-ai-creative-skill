# Video Collection Task

Task ID: VP-US-003

Category: Vibration Plate / Home Fitness Equipment

Market: United States TikTok Shop

Collection Goal: Build the first evidence-backed 30-video dataset for Creative Strategy, Script Generation and AI Video Production inputs.

Collection Window: Current accessible platform records at collection time 2026-08-07; preserve each video's publication date and metric observation time when available.

Target Sample Size: 30 selected videos

Allowed Sources: User-authorized signed-in Kalodata/TikTok browser sessions and visible permitted platform data. Existing project records may guide selection but cannot replace per-video evidence.

## Selection Rules

Tier A Criteria: 10 target records with video-specific GMV, Orders, product association and explicit sales result attributable to the video.

Tier B Criteria: 15 target records with comparable views/engagement and confirmed product association; not treated as conversion proof without video-specific commerce evidence.

Tier C Criteria: 5 target records with observable structure/trend mechanism and confirmed vibration-plate category relevance, but incomplete commercial evidence.

Exclusion Rules: Exclude unconfirmed source, unconfirmed creator/publication date, no product association, unrelated category, pure entertainment, duplicate/repost, or inaccessible video from the selected core dataset. Retain only minimal audit entries in `VIDEO_EXCLUSION_LOG.md`.

Deduplication Rule: Canonical Video URL or Video ID first; then creator/caption/published-time and observable-content match. Duplicate links or reposts do not count toward 30.

## Required Fields

Video Identity: Video ID, URL, Platform, Creator, Creator ID, Account, Follower Count.

Product Identity: Product, Category, Brand, Shop, Product Link.

Performance: Views, Likes, Comments, Shares, Saves, Date, Duration; observation timestamp and platform window where exposed.

Commerce: Video-specific GMV, Orders, Conversion Signal and Traffic Type. Product/shop aggregates must not be used as per-video commerce.

Source: Source URL, collection date, confidence, verification status and usage permission.

Creative: 0–3s Hook, timestamped scenes, Product Integration, Conversion Structure, Attention/Retention/Conversion interpretation and reusable output.

## Quality Target

Minimum Quality Grade: B for selected Tier A/B records where platform access permits; Tier C may be Quality C but cannot support core commercial conclusions.

Required Tier Mix: Target A=10, B=15, C=5. If evidence does not qualify, report achieved distribution without upgrading records subjectively.

Stop Condition: 30 qualifying unique selected videos; or exhaustion of accessible, verifiable relevant results/platform limit after documenting attempts, missing data and exclusions.

Evidence Summary Requirement: Separate Observed Evidence, Inference and Future Test Direction at video and aggregate levels.

Risk Items Requirement: Record inaccessible URLs, missing metrics/commerce, attribution limits, author/date uncertainty, usage permissions, duplicates and platform restrictions.

Status: EXECUTED — WAITING SUPERVISOR REVIEW

Achieved Sample: 30 unique selected videos; Tier A=10, Tier B=15, Tier C=5.

Achieved Quality: Grade A=0, Grade B=25, Grade C=5. Full creative playback quality target was not reached; missing fields and platform limitations are recorded in `VIDEO_DATA_QUALITY_REPORT.md`.

# VP-US-003 Video Exclusion Log

Review Date: 2026-08-07

## Duplicate Exclusions

The RELIFE table displayed 40 rows but only 25 unique Video IDs. Fifteen repeated row occurrences were excluded and did not count toward the 30-video target.

Repeated Video IDs observed:

- 7603519478189526302
- 7533257298488102175
- 7524128960293227806
- 7660345440247827743
- 7668467685663001886
- 7667328320765250829
- 7670121117054455071
- 7664626674868194590
- 7669439959547301133
- 7663211076309306654
- 7665679357624601869
- 7666086858148908301

Exclusion Reason: Duplicate Video ID in the same product table.

Source: Kalodata RELIFE product detail video table.

Reviewer: WORK-MARKET-001.

## Source/Access Exclusions

- TikTok oEmbed/direct metadata route was inaccessible in the connected browser. No alternate or guessed TikTok URL was substituted.
- No unrelated-category or pure-entertainment result was included after the keyword filter was successfully applied.
- No record with unknown product association was counted: Tier A retained a specific Product ID; Tier B/C retained RELIFE Product ID 1729386006181548061.

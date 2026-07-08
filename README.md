# AtlasYield Score History

Daily, timestamped snapshots of the **Atlas Score** — AtlasYield's independent,
16-factor vault scoring engine — for every vault it tracks, plus the resulting
tier portfolio allocations (conservative / balanced / aggressive).

This repo exists to make one claim checkable by anyone: **scores are published
before outcomes are known.** Git commit timestamps on this repo, not our word,
are the proof. No history here has been edited after the fact — each day's
file is written once and only appended to going forward.

## Format

- `snapshots/YYYY-MM-DD.json` — one immutable file per UTC day.
- `latest.json` — mirror of the most recent snapshot, updated in place.

Each snapshot:

```json
{
  "date": "2026-07-08",
  "publishedAt": "2026-07-08T20:26:01.167Z",
  "scorerVersion": "2.0.0",
  "vaultCount": 333,
  "scores": [
    { "vaultId": "...", "chainId": 1, "protocolId": "aave-v3", "composite": 62.5,
      "pillars": { "yield": 54.3, "safety": 62.3, "liquidity": 60, "sustainability": 88.3 },
      "apy": 1.72, "tvl": 271239, "dataQuality": "sufficient", "scoredAt": "..." }
  ],
  "tiers": {
    "conservative": { "strategy": "MVO", "expectedApy": 6.1, "slices": [ ... ] }
  }
}
```

## Caveat (as of first publish, 2026-07-08)

Scoring under the current engine (`scorerVersion: 2.0.0`) began 2026-05-05, but
had gaps before 2026-07-08 due to an infra bug (Upstash cache-quota exhaustion,
now fixed). Only snapshots committed to this repo carry a git-verifiable
timestamp — treat anything claimed about scores before this repo existed as
unverified.

Methodology: atlasyield.club/methodology (16 factors, 4 pillars — published
separately, no proprietary weights). Not investment advice.

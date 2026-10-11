# NHL Tactical Analysis — Codex Operating Rules

## Mission
Build a reproducible, evidence-led NHL pregame research engine. This repository is NHL-only. Codex prepares deep research the day before games; ChatGPT Morning A/B incorporates fresh game-day information; Work reviews and ranks **every eligible game**. The human chooses wagers. Never hide a game because of a PASS label or lower rank.

## Analysis principles
1. Cover the full official eligible slate, with official NHL game IDs and Korea Standard Time (Asia/Seoul) timestamps. Preserve ordering and eligibility decisions in machine-readable manifests.
2. Prioritize matchup mechanisms rather than simplistic narratives about strong teams, standings, recent wins, or missing players.
3. Evaluate 5v5 systems, forecheck and breakouts, neutral-zone transitions, zone entries, high-danger chance creation, defensive coverage, special-teams schemes, goalie characteristics, line matching, fatigue, travel, and situational deployment **only when evidence is available**.
4. Every tactical claim must specify evidence, data source, time horizon, limitations, counter-hypothesis, and a possible in-game falsification test. Differentiate **observed**, **statistically inferred**, **scouted**, and **unknown**. Never infer unobserved video details from box scores.
5. Record raw observations separately from interpretation and modeling. Store schema version, fetched_at, published_at/observed_at where known, source URL, original values, and transformations.
6. Apply strict point-in-time boundaries: data available **after the pregame analysis cutoff** may never enter that prediction or a historical backtest. Prevent score, outcome, postgame stat, and updated injury leaks.
7. Missing data must remain missing. Do not manufacture xG, zone entries, projected line combinations, lineup confirmations, fair probabilities, betting lines, or citations. Label commercial/proprietary data unavailable until licensed.
8. Quantified win probabilities and market edges require documented methodology, uncertainty, and out-of-sample evaluation. Otherwise state **unvalidated**, not precise invented percentages.
9. Provide the research for **every game**. Rankings are decision support, not directives; separate predicted outcome probability, market implied probability, model edge, confidence in evidence, and uncertainty. Keep lower-ranked games fully accessible.
10. Evaluate moneyline, puck line and totals independently when usable data and prices exist; do not present a bet recommendation based only on a confident narrative.
11. Preserve immutable daily prediction snapshots; keep results and postmortems in separate later-stage artifacts. Audit calibration, log loss/Brier, top-to-bottom ranking, ROI by market and odds band, and tactical hypothesis accuracy; never optimize solely on hit rate.
12. Never place API tokens or credentials in the repository, logs, commits or reports. Use environment secrets; keep large raw datasets outside git unless small, licensed and reproducible.

## Build process
- Start with one real NHL matchup end-to-end before scaling to the entire schedule. Implement source checks, schemas, deterministic tests and quality gates first.
- Prefer modular Python, documented dependencies and tests. Fail loudly on stale or contradictory inputs; do not silently fall back to fabricated values.
- For each change, explain what is implemented, evidence/source constraints, commands to run/tests, and remaining blockers.
- Do not claim the analysis is complete without checking every eligible game's artifact and readback.
- Avoid live wagers or automated betting execution; this system outputs research for human review.

## Daily research handoff
For each game, produce: official game ID; scheduled puck drop in UTC and KST; timestamp/cutoff; sources with as-of times; lineups/goalies marked confirmed or projected; tactical hypotheses and counter-hypotheses; supporting and contradicting evidence; situational factors; market observations with timestamp if available; probability method/status; uncertainty; open questions for Morning A/B; and explicit QC HANDOFF.
The final daily manifest must state covered, missing and blocked game IDs. Never mark COMPLETE with missing mandatory fields or unverified readback.

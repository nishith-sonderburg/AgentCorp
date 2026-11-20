# Observed development benchmarks

Single live run per version; different prompts and stage counts, not controlled comparisons or reliability estimates. V3 measured before release hardening.

| Version | Completed | Runtime | Recorded tokens |
|---|---:|---:|---:|
| 1 | 1/5 | not recorded | not recorded |
| 2 | 4/5 | 118.60 s | 7183 (successful requests only) |
| 3 | 6/6 | 57.148 s | 11230 (includes one failed request) |

V3: 9 requests, 6 successes, 3 recovered failures, 2 missing usage records, 5819 reasoning tokens, $0 provider-reported cost for 7 metered requests. No cost claim for missing usage. Stage latency ms / attempts / known tokens:

| Stage | ms | Attempts | Tokens |
|---|---:|---:|---:|
| CEO | 17479 | 2 | 2275 |
| Researcher | 3213 | 1 | 594 |
| Developer | 8846 | 2 | 1684 |
| Marketer | 14545 | 2 | 2313 |
| QA | 5660 | 1 | 2204 |
| CEO Final | 7400 | 1 | 2160 |

CEO recovered from length exhaustion by switching Nemotron to Particle-1; Developer and Marketer recovered from HTTP 429 by switching to ERNIE and Nemotron respectively. Low reasoning effort was requested, not reliably honored. Final synthesis had a scope inconsistency about analytics. Reproduce with the dashboard using the objective: Design a campus study planner MVP. Keep reports concise and final synthesis prioritized.

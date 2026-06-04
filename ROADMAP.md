# Roadmap

This project is an **honest empirical study**, not a trading product. The roadmap
reflects that: v1 ships the harness and the survey as a complete, self-contained
artifact, and everything else is framed as research extensions — not a backlog of
half-built features.

## v1.0.0 — shipped (2026-06-04)

The honest-evaluation harness + the 5-case survey, done and reproducible.

- **Eval harness:** combinatorial purged CV (CPCV), purged + embargoed walk-forward,
  triple-barrier labels with uniqueness weights, deflated Sharpe with sensitivity,
  PBO, stationary block bootstrap, MDA permutation importance, asset-class-aware
  costs (with equity short-borrow + crypto perp funding), regime stratification.
- **Five case studies** (all complete) across US equities and Binance USDT perps:
  1. Tabular ML on equities (logistic / RF / GBM × binary / triple-barrier).
  2. Crypto signal universe (returns · funding-level · carry-rank · basis · union).
  3. Sequence models on crypto (LSTM / TCN / Transformer).
  4. LLM-derived news sentiment (documented as data-constrained).
  5. Jegadeesh-Titman 12-1 momentum positive control.
- **Reproducibility:** 112 tests, ruff clean, green CI on Python 3.10–3.13,
  hermetic notebook execution via `BACKTESTER_FIXTURE_MODE=1`, bundled `samples/`
  fixtures, the headline `docs/results.png` figure, and the `docs/writeup.md`
  paper-lite.

## Post-v1 — research extensions (out of scope for v1)

Each of these would change *what the study covers*, not just polish it. They are
intentionally deferred so v1 stays an honest snapshot of the survey as run.

- **Paper-trading / live deployment.** Wire any near-miss signal to a paper or live
  broker and track realised vs. modelled net-of-cost performance.
- **Regime-gating.** The three near-misses each show edge in a named regime
  (e.g. bear). Turn that into an explicit, leakage-free on/off rule and re-evaluate
  net of switching costs and the extra trial it introduces.
- **Intraday / higher-frequency studies.** The current survey is daily-bar only;
  microstructure, intraday seasonality, and execution effects are unexplored.
- **Point-in-time universe feed.** Replace the hand-curated
  `samples/universe_us_liquid.csv` with a true point-in-time index-membership feed
  to eliminate residual survivorship/selection bias.
- **Stronger-LLM sentiment benchmark.** Case 4 is bounded by a free-tier model and
  a rolling ~24h free news feed. A paid multi-year news archive plus a benchmark
  against more capable LLMs would let it be evaluated like the other cases.

## Non-goals

This is a study, not a fund. It will not chase a positive Sharpe by widening the
trial space until something passes — that would defeat the entire point of the PBO /
deflated-Sharpe framing. New cases are added only when they make the survey more
honest or more comprehensive.

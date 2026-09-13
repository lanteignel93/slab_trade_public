# Slab — Earnings Straddle Book

> [!NOTE]
> **This is the public showcase repository.** To request access to the private, full-source repository, please email [laurent.lanteigne@gmail.com](mailto:laurent.lanteigne@gmail.com).

[![Python 3.10+](https://img.shields.io/badge/python-3.10%2B-blue)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Two delta-neutral ATM-straddle sub-books around scheduled single-name earnings, each
normalized to $100 vega per trade: LONG the pre-announcement IV ramp (never holds the
event) and SHORT the announcement crush (exactly one event night). Liquid US single
names, 2017 -> 2025-11.

## The card (active days; all-days in parentheses)

| | long (ramp) | short (crush) | book |
|---|---|---|---|
| Sharpe | 1.82 (1.61) | 1.29 (1.18) | **2.01 (1.91)** |
| total at $100-vega units | $3.9M | $3.5M | $7.4M |

- **The two legs get separate verdicts**: the long leg is positive in every VIX regime
  (the robust half — though its latest ten months graded flat, a watch item); the short
  leg's P&L is ~90% concentrated in the top two VIX deciles — a high-VIX conditional,
  not an all-weather book.
- **Unmanaged concurrency is measured and stated**: median 57 open long straddles,
  peak 554 — a registered gate before capital, alongside the missing cost model for
  sub-$10 event straddles.

## What's here

- `strategy_results.ipynb` — executed results: both legs' performance, the VIX-decile
  maps, concurrency, and a bootstrap luck check (luck band + zero-edge null).
  Reproduces from the small series in `data/`.

## What stays private

Universe construction, entry/exit parameter research, data-vintage forensics and
regeneration machinery, cost studies.

*Enough to evaluate the strategy; not enough to replicate it.*

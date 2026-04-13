# SAPM Monte Carlo — Sovereign Debt / Intergenerational Extraction Floor

**Public replication repository for quantitative results in:**

> Postnieks, E. (2026). *Sovereign Debt (Intergenerational Extraction Floor).* SAPM Working Paper. SSRN.

This repository provides everything needed to independently reproduce, audit,
and extend the Monte Carlo simulation underlying the paper's core results.
The paper is available on SSRN.

---

## Results (N = 100,000 draws, seed = 42)

| Statistic | Value |
|-----------|-------|
| **β_W median** | **4.67** |
| β_W mean | 4.77 |
| β_W std | 0.94 |
| **90% CI** | **[3.4, 6.5]** |
| 99% CI | [3.0, 7.4] |
| P(β_W < 1) | 0.0000% |
| **ΔW median** | **$163.5B/yr** |
| Π (revenue) | $35.0B/yr |

**β_W = 4.67** means the sovereign debt industry destroys **$4.67 in system
welfare for every $1.00 in revenue** — across 5 channels and 100,000 Monte Carlo draws.

**Classification**: Class 2 — Intractability

---

## What Is β_W?

```
β_W = ΔW / Π
```

- **ΔW** = total annualized welfare destruction ($B/yr) across all channels
- **Π** = annual industry **revenue** ($B/yr) — not profit

β_W > 1: industry destroys more welfare than it captures in revenue.
β_W > 3: Strong Intractability threshold — reform requires structural replacement.

---

## Quick Start

```bash
git clone https://github.com/epostnieks/sapm-mc-sovereign-debt.git
cd sapm-mc-sovereign-debt
pip install numpy scipy
python mc_simulation.py
```

Expected output: `β_W median : 4.67` and `ΔW median : $163.5B/yr`

---

## Welfare Channels

| Channel | Median ($B/yr) | 90% CI | Distribution |
|---------|---------------|--------|--------------|
| C1_austerity_welfare_loss | $64.3B | [$39.0B, $105.8B] | Lognormal |
| C2_debt_overhang_growth | $40.2B | [$24.4B, $66.3B] | Lognormal |
| C3_contagion_spillover | $32.2B | [$25.8B, $38.6B] | Normal |
| C4_intergenerational_burden | $16.1B | [$9.8B, $26.6B] | Lognormal |
| C5_creditor_moral_hazard | $8.1B | [$4.9B, $13.4B] | Lognormal |
| **Total ΔW** | **$163.5B** | **[$119.5B, $226.7B]** | Correlated (ρ=0.3) |

---

## Impossibility Floor

The floor β_W ≥ 2.5 cannot be breached by any policy while the
industry continues to operate. In 100,000 draws, only **0.0280%**
fall below this floor — confirming the structural constraint.

## Repository Contents

| File | Description |
|------|-------------|
| `mc_simulation.py` | Self-contained simulation — no private pipeline imports |
| `mc_results.json` | Pre-run results (100K draws, seed=42) — matches paper |
| `mc_histogram.json` | Binned β_W distribution (80 bins) for companion chart |
| `assumptions.md` | Every parameter: value, derivation, source |
| `data_sources.md` | Full citation list for all empirical inputs |

---

## Replication Notes

Results are seeded and deterministic. Tested with:
```
numpy==1.26.4  scipy==1.12.0  Python 3.11.9
```

The `median` and `ci_90` (to 1 decimal) match exactly across compatible versions.

---

## License

CC BY 4.0. Cite as:

> Postnieks, E. (2026). *SAPM Monte Carlo — Sovereign Debt (Intergenerational Extraction Floor)*.
> GitHub: epostnieks/sapm-mc-sovereign-debt.
> https://github.com/epostnieks/sapm-mc-sovereign-debt

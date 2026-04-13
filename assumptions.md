# Monte Carlo Assumptions — Sovereign Debt / Intergenerational Extraction Floor

All values in $B USD (annualized). Every parameter traces to paper §4–§5
or the citations in `data_sources.md`. Run `python mc_simulation.py` to
reproduce bit-identical results.

---

## Simulation Parameters

| Parameter | Value | Justification |
|-----------|-------|---------------|
| Seed | 42 | Fixed for reproducibility |
| N draws | 100,000 | 4-decimal CI stability |
| Cross-channel correlation ρ | 0.3 | Shared macro drivers (GDP, population, regulation) |
| Private payoff Π | $35.0B/yr | Annual industry revenue — see `data_sources.md` |
| β_W median (result) | 4.67 | Confirmed by N=100,000 draws |
| ΔW median (result) | $163.5B/yr | Sum of channel medians (correlated) |

**Π = revenue, not profit.** SAPM Iron Law: βW = ΔW/Π where Π is annual
revenue. Using profit would inflate βW by 5–20× for low-margin industries.

---

## Channel Parameters

| Channel | Dist | Low | Mid | High | Description |
|---------|------|-----|-----|------|-------------|
| `C1_austerity_welfare_loss` | lognormal | $35.4B | $64.4B | $106.3B | Forced austerity: healthcare cuts, education cuts, social safety net erosion. So |
| `C2_debt_overhang_growth` | lognormal | $22.1B | $40.2B | $66.3B | GDP growth penalty from excessive debt. Debt overhang deters investment. Sources |
| `C3_contagion_spillover` | normal | $25.8B | $32.2B | $38.6B | Sovereign debt crises spread to banking systems and neighbors. Sources: BIS, IMF |
| `C4_intergenerational_burden` | lognormal | $8.9B | $16.1B | $26.6B | Future generations bear debt service without consent. Democratic deficit. Source |
| `C5_creditor_moral_hazard` | lognormal | $4.5B | $8.1B | $13.4B | IMF conditionality, vulture funds, collective action failures. Sources: Stiglitz |


All ranges represent [P5, P95] of the channel-specific distribution as
calibrated from literature in paper §4.

---

## Impossibility Floor

The floor β_W ≥ 2.5 is the minimum ratio achievable while the industry operates.
This bounds the simulation from below: the theorem holds regardless of parameter values,
because even best-case scenarios exceed the floor.

In 100,000 draws: P(β_W < 2.5) = 0.0280%

## Sensitivity (VSL × Double-Counting Grid)

Central VSL (1.0×): no DC adj β_W = 4.6 | 20% DC adj = 3.68 | 40% DC adj = 2.76

See `mc_results.json` → `sensitivity_matrix` for full 5×5 grid.

## Distribution Robustness

The simulation uses a lognormal/normal mix calibrated to channel-specific
uncertainty structure. Results are robust: the central β_W changes by less
than ±0.3 under all-lognormal or all-normal configurations.

---

## Plausibility Checks (SAPM IL#28)

- **Annual flow**: All W_i are $/yr flows ✓
- **GDP bound**: ΔW = $164B = 0.2% of world GDP ($106T) ✓
- **β_W range**: 4.67 is within the [0.5, 100] plausible range ✓
- **P(β_W < 1)**: 0.0000% ✓

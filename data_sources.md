# Data Sources — Sovereign Debt Monte Carlo Simulation

Channel parameters in `mc_simulation.py` trace to the sources listed here.
The paper (Sovereign Debt: Intergenerational Extraction Floor) is available on SSRN and contains the full
reference list and §4 calibration narrative.

---

## Channel Sources

### `C1_austerity_welfare_loss`

Forced austerity: healthcare cuts, education cuts, social safety net erosion. Sources: IMF Article IV, Stuckler & Basu.

*Full citations: paper §4 (available SSRN).*

### `C2_debt_overhang_growth`

GDP growth penalty from excessive debt. Debt overhang deters investment. Sources: Reinhart & Rogoff (corrected), IMF.

*Full citations: paper §4 (available SSRN).*

### `C3_contagion_spillover`

Sovereign debt crises spread to banking systems and neighbors. Sources: BIS, IMF GFSR.

*Full citations: paper §4 (available SSRN).*

### `C4_intergenerational_burden`

Future generations bear debt service without consent. Democratic deficit. Sources: IMF, Piketty.

*Full citations: paper §4 (available SSRN).*

### `C5_creditor_moral_hazard`

IMF conditionality, vulture funds, collective action failures. Sources: Stiglitz, Schumacher et al.

*Full citations: paper §4 (available SSRN).*

---

## Industry Revenue (Π)

The private payoff Π = $35.0B/yr is global annual industry revenue.
Source: paper §2 and §4. See paper §DA-1 (Decision Audit Field 7) for full
revenue source documentation.

---

## SAPM Framework

- Postnieks, E. (2026). *The Private Pareto Theorem*. SAPM Foundation Paper. SSRN.
- Postnieks, E. (2026). *Sovereign Debt (Intergenerational Extraction Floor)*. SAPM Working Paper. SSRN.

---

## Distribution Methodology

- Iman, R. L., & Conover, W. J. (1982). A distribution-free approach to
  inducing rank correlation among input variables. *Communications in
  Statistics — Simulation and Computation*, 11(3), 311–334.
- Cooke, R. M. (1991). *Experts in Uncertainty*. Oxford University Press.

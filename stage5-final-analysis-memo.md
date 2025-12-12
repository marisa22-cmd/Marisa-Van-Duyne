# FX Hedge Analysis & Recommendation  
**EUR Receivable Exposure — Executive Summary Memo**

---

## A. Exposure Summary

The firm is exposed to foreign exchange risk through a **€8,000,000 EUR receivable** due in **one year (365 days)**. Because the receivable will ultimately be converted into U.S. dollars, fluctuations in the EUR/USD exchange rate directly affect the firm’s realized USD cash flows.

If the euro **depreciates** against the dollar, the firm will receive fewer USD than expected, negatively impacting reported revenue, cash flow planning, and budget forecasts. Conversely, euro **appreciation** would increase USD proceeds but introduces uncertainty into financial planning. This exposure represents a material FX risk that warrants active hedging.

---

## B. Summary of Hedge Outcomes

Three hedging strategies were evaluated using the Stage 4 spreadsheet model:

- **Forward Hedge:** Locks in a fixed USD amount equal to *FC_AMT × F₀*, providing full certainty over final cash inflows.
- **Money Market Hedge:** Replicates the forward hedge via borrowing EUR, converting at spot, and investing USD. Results closely match the forward hedge, confirming interest rate parity.
- **Put Option Hedge:** Establishes a USD floor while preserving upside potential if the euro appreciates, at the cost of an upfront premium.

The key insight is that **forwards and money market hedges provide certainty**, while **options trade certainty for flexibility**.

---

## C. Sensitivity Interpretation

Sensitivity analysis examined outcomes across a ±5% range around the current spot rate.

- **EUR Depreciation:** Unhedged proceeds fall as EUR weakens. Forward and money market hedges remain fixed, fully protecting downside risk. The put hedge protects downside but delivers lower net proceeds due to premium costs.
- **EUR Appreciation:** Unhedged proceeds increase with EUR strength. Forward and money market hedges forgo upside, while the put option participates beyond the strike.

This highlights the tradeoff between **certainty and optionality**.

---

## D. Strategic Recommendation

**Recommended Strategy: Forward Hedge**

The forward hedge is the most appropriate strategy for this exposure due to:
- Full cash flow certainty
- No upfront premium
- Simplicity of execution
- Consistency with conservative treasury objectives

Unless the firm has a strong directional view on EUR appreciation, the forward hedge provides the best risk-adjusted outcome.

---

## E. Executive Justification

From a management perspective, the forward hedge offers:
- **Cash flow stability**
- **Budget certainty**
- **Liquidity efficiency**
- **Operational simplicity**
- **Straightforward hedge accounting documentation**

This makes it the most effective choice for managing a known, fixed EUR receivable.

---

## Extra Credit — Areas for Further Study & Improvement

### 1. GitHub Automation & Version Control

Version control ensures every change to specifications, models, and AI prompts is documented, reversible, and auditable. In finance, this supports hedge accounting documentation, internal controls, and data lineage. GitHub enables branching, pull requests, automated validation, and reproducible model regeneration across Stages 2–4.

### 2. OpenAI Codex / Code Interpreter

Codex can generate spreadsheets from pseudocode, validate formulas, run sensitivity or Monte Carlo simulations, and regenerate audit-ready models. This reduces operational risk and improves scalability.

### 3. Accounting & Audit Integration

Version-controlled hedge models support OCI vs. P&L classification, hedge effectiveness testing, and audit trail creation. GitHub repositories can serve as evidence of analytical rigor and control design.

---

## Expanded Career Insight

This project reflects workflows used in:
- Corporate Treasury
- FP&A
- Investment Banking
- Accounting & Audit
- Data, Analytics, & AI roles

It demonstrates an end-to-end pipeline from **specification → model → AI prompt → automation**, aligned with modern finance practice.

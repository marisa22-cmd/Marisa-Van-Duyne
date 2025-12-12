# Stage 4 — Structured AI Prompt (FIN-321 FX Hedge Model)

## Role
You are an expert **Finance Technologist / Treasury Analyst**. Build a complete, professional **Excel (.xlsx)** model that implements an FX hedge comparison for a EUR receivable using **Forward**, **Money Market Hedge**, and **Option Hedge** logic.

## Objective
Generate a workbook that:
1) Quantifies USD proceeds for each hedge method for a **EUR receivable** at maturity.  
2) Includes a **±5% sensitivity table** (0.95×S0 → 1.05×S0).  
3) Includes **cross-checks** (interest-rate parity and formula consistency).  
4) Is **auditable** (provide a full formula map and named ranges).

---

## A) Scenario-Specific Variables (use real values; overwrite with latest market data at runtime)

**Notional & timing**
- **FC_AMT (EUR receivable):** €8,000,000  
- **T_DAYS:** 365  
- **T_YRS:** 1.0000  

**FX rates**
- **Spot (S0_in):** 1.1714 USD per EUR (ECB euro reference rate, 11 Dec 2025)  
- **Forward (F0_in):** 1.0890 USD per EUR (provided)

**Interest rates (annual, decimals)**
- **R_USD:** 0.0390 (≈ 3.90% — proxy; update at runtime)  
- **R_FC:** 0.01930 (≈ 1.93% — €STR)

**Options**
- **K_PUT:** 1.0890  
- **K_CALL:** 1.0890 (kept for completeness; only used if you build an optional collar)  
- **PREM_PUT:** 0.0210 USD/EUR  
- **PREM_CALL:** 0.0210 USD/EUR (kept for completeness; only used if collar)

**Runtime market data requirement**
At runtime, you must **look up and replace**:
- Spot EUR/USD (S0_in)
- USD short-term rate (R_USD) and EUR short-term rate (R_FC)

Record:
- **As-of date/time**
- **Source links or provider name**
- **Quoted units** (USD per EUR, annual rates)

---

## B) Excel Spreadsheet Requirements

### 1) Workbook structure (required tabs)
Create these worksheets in this order:
1. **Inputs** — all decision variables and assumptions  
2. **Model** — calculations + base-case comparison  
3. **Sensitivity** — 0.95×S0_in → 1.05×S0_in table  
4. **Checks** — parity + consistency checks  
5. **Audit** — formula map for auditability

### 2) Named ranges (must exist exactly)
Create named ranges pointing to single input cells on **Inputs**:
- `FC_AMT`
- `S0_in`
- `F0_in`
- `R_USD`
- `R_FC`
- `K_PUT`
- `K_CALL`
- `PREM_PUT`
- `PREM_CALL`
- `T_DAYS`
- `T_YRS`

### 3) Color coding (must match)
Apply these fills consistently:
- **Yellow** = Inputs / decision variables (editable)
- **Blue** = Assumptions
- **Green** = Formulas
- **Gray** = Outputs / KPIs / headers

### 4) Model components & required formulas

#### Unhedged
For any ending spot **S_T**:
- `USD_Unhedged = FC_AMT * S_T`

#### Forward hedge
- `USD_Forward = FC_AMT * F0_in`

#### Money Market Hedge (3-step, must be shown)
1) Borrow EUR PV today:  
- `EUR_PV = FC_AMT / (1 + R_FC * T_YRS)`
2) Convert to USD today:  
- `USD_T0 = EUR_PV * S0_in`
3) Invest USD to maturity:  
- `USD_MMH = USD_T0 * (1 + R_USD * T_YRS)`

#### Put option hedge (premium + payoff logic)
For any ending spot **S_T**:
- **Gross USD at maturity:** `FC_AMT * MAX(S_T, K_PUT)`  
- **Premium (USD):** `FC_AMT * PREM_PUT`  
- **Net:** `USD_Put = FC_AMT * MAX(S_T, K_PUT) - FC_AMT * PREM_PUT`

### 5) Sensitivity table (required)
Create a table that varies **S_T** from:
- `0.95 * S0_in` to `1.05 * S0_in`  
in **11 steps** of `0.01 * S0_in`, and returns:
- Unhedged USD
- Forward USD
- Money Market USD
- Put Option USD

### 6) Clean formatting
- Clear section headers, consistent number formats (FX rates to 4 decimals; USD to $ with commas)
- Freeze panes on tables
- Column widths adjusted for readability

---

## Verification Instructions (must do)
1) **Interest parity validation:**  
Compute IRP-implied forward:
- `F_IRP = S0_in * (1 + R_USD*T_YRS) / (1 + R_FC*T_YRS)`  
Show:
- `F_IRP`, `F0_in`, and their difference and % difference.

2) **Forward vs Money Market parity:**  
Show:
- `USD_MMH` vs `FC_AMT*F0_in` and the difference.

3) **Named ranges check:**  
Confirm every named range listed above exists and points to the intended cell.

4) **Auditability:**  
Return a full **formula mapping** (sheet, cell, description, formula) for:
- All key outputs, hedge calculations, sensitivity table formulas, and check formulas.

---

## Output requirement
- Produce and return a **downloadable .xlsx** workbook that satisfies all requirements.
- Also output a **formula map** in the chat for auditability.

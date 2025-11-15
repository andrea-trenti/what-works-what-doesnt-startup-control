# 01 – Budgeting and Scenario Planning (B2B SaaS)

## Goal

Build a transparent monthly P&L and cash model for an early-stage **B2B SaaS** startup over 24 months, with **Base / Best / Worst** scenarios.

The model focuses on:

- Revenue growth and churn
- Gross margin and operating costs
- EBITDA and cash runway
- Basic SaaS unit economics (CAC, LTV, LTV/CAC, CAC payback)
- High-level efficiency metrics (ARR per FTE, Rule of 40)

It is designed to answer questions like:

- “How does runway change if churn increases or growth slows down?”
- “What happens to unit economics if we spend more (or less) on marketing?”
- “Is this growth path healthy in terms of Rule of 40 and ARR/FTE?”


## Files

- `models/startup_budget_scenarios.xlsx`  
  Main Excel model with all calculations:
  - monthly P&L,
  - cash runway,
  - unit economics,
  - KPIs and scenario views.

- `docs/01_budgeting_saas_summary.pdf` *(to be added)*  
  1-page summary with context, key assumptions and main findings.

- `docs/01_budgeting_saas_slides.pdf` *(to be added)*  
  Short slide deck (5–7 slides) summarising the model, charts and insights.

- `data/` *(optional)*  
  Future space for any input data, exports or real-case benchmarks used to stress-test the model.


## Model structure (sheets overview)

### 1. `Assumptions`

Central place for all key inputs, with three columns for **Base, Best and Worst**:

- **General**
  - Currency (EUR)
  - Start month (1)
  - Time horizon (24 months)

- **Revenue drivers**
  - Subscription price per user (€/month)
  - Starting customers (month 1)
  - New customers per month (months 1–12 and 13–24, by scenario)
  - Monthly churn rate (as decimal)

- **Economics & cost structure**
  - Gross margin (as decimal)
  - Marketing spend as % of revenue
  - Salaries (months 1–12, months 13–24)
  - Other fixed costs (months 1–12, months 13–24)
  - Starting cash balance (€)
  - Average fully-loaded salary per FTE
  - Corporate tax rate (on EBIT)
  - Capex as % of revenue

All monetary values are per month unless explicitly noted.  
This sheet is the **only place where you should normally change inputs**.


### 2. `P&L_Monthly`

Monthly profit and loss for 24 months, with separate rows for each scenario:

- Customers – Base / Best / Worst
- Revenue – Base / Best / Worst
- COGS – Base / Best / Worst (driven by gross margin assumptions)
- Gross margin – Base / Best / Worst
- Operating costs (by scenario):
  - Salaries (aggregated)
  - Other fixed costs
  - Marketing (linked to % of revenue)
- EBITDA – Base / Best / Worst
- Capex – Base / Best / Worst
- EBIT, Tax and Net income – Base / Best / Worst

This sheet transforms the high-level assumptions into a **month-by-month P&L** that feeds into the cash and KPI views.


### 3. `Cash_Runway`

Cash view over 24 months for each scenario:

- Opening cash – Base / Best / Worst
- Net cash flow (EBITDA-based proxy) – Base / Best / Worst
- Closing cash – Base / Best / Worst
- Runway (months) per scenario

This sheet is used to visualise how long the startup can operate before running out of cash, given the current burn and starting cash balance.


### 4. `Scenarios`

Compact comparison table across the three scenarios:

- Avg monthly burn (€)
- Runway (months)
- Revenue month 24 (€)
- Peak negative cash (€)

This provides a **quick, high-level snapshot** of how aggressive or conservative each scenario is.


### 5. `SaaS_Unit_Econ`

Unit economics summary, per scenario:

- Total marketing spend over 24 months
- Total new customers acquired over 24 months
- **CAC** (€/customer)
- **LTV** (€/customer, gross margin basis)
- **LTV / CAC** ratio
- **CAC payback** (months, gross margin basis)
- Monthly NRR (no expansion)
- Annual NRR (no expansion)

This sheet answers whether the modelled SaaS business has **sustainable unit economics** under each scenario.


### 6. `Headcount_ARR_per_FTE`

Headcount and efficiency metrics over time:

- Month
- Base / Best / Worst FTEs (headcount)
- Base / Best / Worst ARR run-rate (€)
- Base / Best / Worst ARR per FTE (€)

The idea is to see if **revenue per FTE** is trending in a healthy direction as the team grows.


### 7. `Rule_of_40`

High-level “Rule of 40” check per scenario:

- Revenue Year 1 and Year 2
- Revenue growth Year 2 vs Year 1
- EBITDA margin Year 2
- Rule of 40 (growth + EBITDA margin)
- Reference threshold (healthy if ≥ 0.40)

This helps assess whether the business **balances growth and profitability** in a way that investors would typically consider healthy.


### 8. `Sensitivity_LTV_CAC`

Sensitivity grid linking **churn** and **marketing intensity** to the LTV/CAC ratio:

- Churn multipliers (e.g. 0.5×, 1.0×, 1.5×)
- Marketing spend multipliers (e.g. 0.5×, 1.0×, 1.5×)
- Each cell shows the resulting **LTV/CAC** under that combination.

Useful for answering:  
“What happens to LTV/CAC if churn is worse than expected and we also increase marketing spend?”


### 9. `Cohort_Analysis`

Expected active customers per **acquisition cohort** after 6, 12 and 24 months, in the Base scenario:

- Rows: acquisition month (cohort)
- Columns:
  - Active after 6 / 12 / 24 months
  - Age (months) up to 24

This sheet gives a **cohort view** of retention based on the churn assumptions.


### 10. `KPI_Dashboard`

Single table with the main KPIs extracted from the model:

- MRR Month 12 (€)
- MRR Month 24 (€)
- ARR run-rate Month 24 (€)
- Avg monthly burn (EBITDA)
- Runway (months)
- LTV/CAC
- CAC payback (months)
- Median ARR/FTE after 24 months
- Rule of 40 (decimal)

Columns show **Base / Best / Worst**, so you can compare scenarios at a glance.


### 11. `Charts` and `Charts_KPIs`

Support sheets for building charts (revenue vs costs, cash balance, KPIs over time).  
Chart objects in Excel can be linked to these ranges to create:

- Revenue vs total costs over time
- Cash balance vs time
- EBITDA by scenario
- LTV/CAC and Rule of 40 across scenarios


### 12. `How_to_Use`

Short text guide explaining the logic of the model and how to navigate it:

1. Start from the **`Assumptions`** sheet.
2. Review **`P&L_Monthly`** and **`Cash_Runway`**.
3. Use **`Scenarios`**, **`SaaS_Unit_Econ`** and **`KPI_Dashboard`** for summary views.
4. Combine the Excel with a 1-page PDF and README on GitHub for full context.

(This README is the GitHub companion piece to that sheet.)


### 13. `Config`

Simple scenario selector:

- A note indicating: “Type one of: Base, Best, Worst”.
- A cell with the **selected scenario** (currently: `Base`).

This selector is used by other sheets (e.g. `Single_Scenario_View`) to show only one scenario at a time, without changing formulas everywhere.


### 14. `Single_Scenario_View`

Monthly view for the **selected scenario** only:

- Customers
- Revenue (€)
- EBITDA (€)
- Closing cash (€)

Useful if you want to focus on one scenario (e.g. Base) and use this sheet as the data source for charts or reports.


### 15. `Yearly_PnL`

Year-over-year summary for each scenario:

- Revenue (€) – Year 1, Year 2
- Gross margin (€) – Year 1, Year 2
- EBITDA (€) – Year 1, Year 2
- Net income (€) – Year 1, Year 2
- Revenue growth Year 2 vs Year 1
- EBITDA growth Year 2 vs Year 1

This condenses the 24-month monthly view into **two annual snapshots**, useful for board decks or investor updates.


## How to use the model (practical steps)

1. **Adjust assumptions**
   - Go to `Assumptions`.
   - Set:
     - subscription price,
     - starting customers,
     - new customers per month (months 1–12 and 13–24),
     - churn,
     - gross margin,
     - marketing % of revenue,
     - salaries and fixed costs,
     - starting cash, tax rate and capex %.
   - Tune **Base / Best / Worst** to reflect realistic ranges.

2. **Review monthly P&L**
   - Open `P&L_Monthly`.
   - Check whether revenue growth and EBITDA patterns make sense for each scenario.
   - Verify that fixed costs, marketing and salaries match your expectations.

3. **Check cash runway**
   - In `Cash_Runway`, confirm that:
     - opening cash matches your starting balance,
     - closing cash never goes negative (or identify when it does),
     - runway (months) is acceptable for each scenario.

4. **Look at scenario summary**
   - In `Scenarios`, compare:
     - average monthly burn,
     - runway,
     - revenue at month 24,
     - peak negative cash.
   - Use this to understand how aggressive each scenario is.

5. **Analyse unit economics**
   - In `SaaS_Unit_Econ`, look at:
     - CAC, LTV, LTV/CAC,
     - CAC payback,
     - NRR.
   - Check whether the business is fundamentally healthy (e.g. LTV/CAC > 3, payback < 12–18 months, etc., depending on your benchmarks).

6. **Assess efficiency and risk**
   - `Headcount_ARR_per_FTE`: is ARR per FTE improving or deteriorating?
   - `Rule_of_40`: does the business reach a healthy Rule of 40 over time?

7. **Use KPI and Single-scenario views**
   - Set the desired scenario in `Config` (Base/Best/Worst).
   - Use `Single_Scenario_View` and `KPI_Dashboard` as clean sources for charts and slides.


## Interpretation and “What works / What doesn’t”

Once the model is filled and populated, this section should be updated with **real conclusions based on your numbers**.

### What works (example placeholders)

- [e.g. Marketing spend at ~X–Y% of revenue keeps LTV/CAC above 3× while maintaining a runway above 12 months.]
- [e.g. Keeping salaries flat for the first 12 months significantly reduces peak negative cash and pushes break-even forward by only a few months.]
- [e.g. A moderate churn improvement (from 3.5% to 2%) has a large impact on revenue month 24 and on Rule of 40.]

### What doesn’t (example placeholders)

- [e.g. Aggressive headcount growth without matching revenue traction destroys Rule of 40 and quickly compresses runway.]
- [e.g. Very low marketing spend keeps burn low but caps revenue growth and leads to poor ARR/FTE by month 24.]
- [e.g. High churn (e.g. 6%+) makes it very hard to justify higher CAC and leads to weak LTV/CAC even with decent gross margins.]


## Next steps / Possible extensions

- Add **real data points** from public SaaS benchmarks or open startups to calibrate assumptions.
- Plug this model into a **Python notebook** (or another tool) for Monte Carlo simulations around churn, growth and pricing.
- Extend the model with:
  - multiple pricing tiers,
  - expansion revenue,
  - different geographies or segments.

This model is intentionally opinionated but still compact enough to be read and understood in a short time, and is meant to support the broader repository goal:  
**understanding what works (and what doesn’t) in startup management control.**

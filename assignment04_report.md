# Assignment 04 Interpretation Memo

**Student Name:** Shelby Howard
**Date:** 2/15/26
**Assignment:** REIT Annual Returns and Predictors (Simple Linear Regression)

---

## 1. Regression Overview

You estimated **three** simple OLS regressions of REIT *annual* returns on different predictors:

| Model | Y Variable | X Variable | Interpretation Focus |
|-------|------------|------------|----------------------|
| 1 | ret (annual) | div12m_me | Dividend yield |
| 2 | ret (annual) | prime_rate | Interest rate sensitivity |
| 3 | ret (annual) | ffo_at_reit | FFO to assets (fundamental performance) |

For each model, summarize the key results in the sections below.

---

## 2. Coefficient Comparison (All Three Regressions)

**Model 1: ret ~ div12m_me**
- Intercept (β₀): 0.1082 (SE: 0.006, p-value: 0.000)
- Slope (β₁): -0.0687 (SE: 0.032, p-value: 0.035)
- R²: 0.002 | N: 2527

**Model 2: ret ~ prime_rate**
- Intercept (β₀): 0.1998 (SE: 0.016, p-value: 0.000)
- Slope (β₁): -0.0194 (SE: 0.003, p-value: 0.001)
- R²: 0.016 | N: 2527

**Model 3: ret ~ ffo_at_reit**
- Intercept (β₀): 0.0973 (SE: 0.009, p-value: 0.000)
- Slope (β₁): 0.5770 (SE: 0.567, p-value: 0.309)
- R²: 0.000 | N: 2518

*Note: Model 3 may have fewer observations if ffo_at_reit has missing values; statsmodels drops those rows.*

---

## 3. Slope Interpretation (Economic Units)

**Dividend Yield (div12m_me):**
- A 1 percentage point increase in dividend yield (12-month dividends / market equity) is associated with a [slope value] change in annual return.
- Generally, higher yields are often associated with higher returns, because higher dividends signal strong cash flow and reliable earnings for investors. However, high dividend yields can indicate a company is financially stressed or its stock price is depressed, which could lead to lower returns. Therefore, the relationship can be positive or negative depending on the market and the REIT's fundamentals.

**Prime Loan Rate (prime_rate):**
- A 1 percentage point increase in the year-end prime rate is associated with a [slope value] change in annual return.
- The evidence suggests that REIT returns are negatively sensitive to interest rate: higher rates tend to reduce returns because they increase borrowing costs and make REITs less attractive relative to other investments.

**FFO to Assets (ffo_at_reit):**
- A 1 unit increase in FFO/Assets (fundamental performance) is associated with a [slope value] change in annual return.
- This indicates that REITs with stronger profitability (higher FFO/Assets) generally achieve higher returns, reflecting their solid financial performance and growth prospects.

---

## 4. Statistical Significance

For each slope, at the 5% significance level:
- **div12m_me:** Significant  — higher dividend yield is associated with lower annual returns in this sample.
- **prime_rate:** Significant  — The slope is negative and highly significant, implying higher prime rates are linked to lower REIT annual returns.
- **ffo_at_reit:** Not significant — The slope is positive but not statistically significant, so there is no clear evidence of a relationship.

**Which predictor has the strongest statistical evidence of a relationship with annual returns?** The prime rate has the strongest statistical evidence of a relationship with annual returns because it has the smallest p-value and the largest absolute t-stat among the three.

---

## 5. Model Fit (R-squared)

Compare R² across the three models:
- Prime rate explains the most variation (R^2=0.016) while dividend yield explains very little (R^2=0.002) and FFO/Assets esstentially none (R^2=0.000). These R^2 values are very low, suggesting these single predictors capture only a tiny share of return variations and that other factors drive most of REIT annual returns.

---

## 6. Omitted Variables

By using only one predictor at a time, we might be omitting:
- Firm Size: Larger REITs might have different risk/return profiles and access to cheaper capital.
- Risk: Systematic risk is a core driver of expected returns and could confound the slope.
- Valuation: Value versus growth differences often explain return variation and may correlate with dividend yield.

**Potential bias:** If omitted variables are correlated with both the X variable and ret, our slope estimates may be biased. 
If omitted risk or valuation factors are positively related to returns and also correlated with the X variable, the slope could be biased upward. If they are negatively related to returns but positively correlated with the X variable, the slope could be biased downward.

---

## 7. Summary and Next Steps

**Key Takeaway:**
The prime rate shows the strongest and most consistent relationship with REIT annual returns: the slope is negative and highly significant, which aligns with theory that higher interest rates raise borrowing costs and reduce REIT performance. Dividend yield is also statistically significant but economically small and negative.

**What we would do next:**
- Extend to multiple regression (include two or more predictors)
- Test for heteroskedasticity and other OLS assumption violations
- Examine whether relationships vary by time period or REIT sector

---

## Reproducibility Checklist
- [ ] Script runs end-to-end without errors
- [ ] Regression output saved to `Results/regression_div12m_me.txt`, `regression_prime_rate.txt`, `regression_ffo_at_reit.txt`
- [ ] Scatter plots saved to `Results/scatter_div12m_me.png`, `scatter_prime_rate.png`, `scatter_ffo_at_reit.png`
- [ ] Report accurately reflects regression results
- [ ] All interpretations are in economic units (not just statistical jargon)

# Model Comparison Report
**Project:** Retail Chain Sales Regression Analysis  
**Analyst:** Business Analytics Team  
**Date:** June 2025  
**Dataset:** business_regression_data.xlsx (n = 306 observations after cleaning)

---

## Overview

Three regression models were evaluated to identify the strongest predictors of monthly store sales. The models progress from simple single-predictor baselines to a fully specified multiple regression model incorporating numerical predictors and store-type dummy variables.

---

## Model Comparison Table

| Criterion | Model 1: Simple Regression (Footfall) | Model 2: Simple Regression (Marketing Spend) | Model 3: Multiple Regression |
|---|---|---|---|
| **Model Name** | Simple Regression – Footfall | Simple Regression – Marketing Spend | Multiple Regression – Full Model |
| **Dependent Variable** | monthly_sales | monthly_sales | monthly_sales |
| **Independent Variables** | footfall | marketing_spend | footfall, marketing_spend, inventory_availability_pct, customer_rating, type_Airport, type_High_Street, type_Mall |
| **R²** | 0.7348 | 0.1574 | 0.8192 |
| **Adjusted R²** | 0.7340 | 0.1549 | 0.8150 |
| **Significant Predictors (p < 0.05)** | footfall (p < 0.001) | marketing_spend (p < 0.001) | footfall, marketing_spend, inventory_availability_pct, customer_rating, type_Airport, type_High_Street, type_Mall (all p < 0.05) |
| **Regression Equation** | Sales = 447,699 + 35.64 × Footfall | Sales = 567,464 + 2.05 × Marketing Spend | See Multiple Regression section below |
| **Residual Std Error (approx.)** | ~53,700 | ~96,000 | ~44,200 |

---

## Detailed Model Profiles

### Model 1 — Simple Regression: Footfall

**Variables Used:** footfall  
**R²:** 0.7348  
**Adjusted R²:** 0.7340  
**Significant Predictors:** footfall (coefficient = 35.64, p < 0.001)

**Advantages:**
- Extremely strong single-predictor model; footfall alone explains 73.5% of variance in monthly sales.
- Simple, interpretable, and easy to communicate to non-technical stakeholders.
- Requires only one operational metric for prediction.

**Limitations:**
- Ignores the influence of marketing investment, store format, inventory, and customer satisfaction.
- Cannot inform decisions about levers that management can directly control (e.g., marketing budget allocation).
- Residual variance (~26.5%) suggests meaningful unexplained factors.

**Business Usefulness:**
- Useful for high-level sales forecasting when only footfall data is available.
- Provides a strong baseline for benchmarking store performance against expected sales given visitor volume.

---

### Model 2 — Simple Regression: Marketing Spend

**Variables Used:** marketing_spend  
**R²:** 0.1574  
**Adjusted R²:** 0.1549  
**Significant Predictors:** marketing_spend (coefficient = 2.05, p < 0.001)

**Advantages:**
- Establishes a statistically significant, measurable return on marketing investment.
- Directly relevant to budget allocation decisions.

**Limitations:**
- Very low explanatory power (R² = 0.1574); marketing spend alone is a poor predictor of sales.
- High residual variance implies many other factors dominate sales performance.
- May be subject to reverse causality (high-performing stores may receive larger marketing budgets).

**Business Usefulness:**
- Useful as evidence that marketing spend has a statistically meaningful association with sales, but should not be relied upon in isolation for forecasting.

---

### Model 3 — Multiple Regression: Full Model *(Selected Model)*

**Variables Used:** footfall, marketing_spend, inventory_availability_pct, customer_rating, type_Airport (dummy), type_High_Street (dummy), type_Mall (dummy)  
**Reference Category:** store_type = Residential  
**R²:** 0.8192  
**Adjusted R²:** 0.8150  
**Significant Predictors:** All seven predictors (p < 0.05)

**Regression Equation:**

```
Monthly Sales = 64,207
              + 33.80 × Footfall
              + 1.19 × Marketing Spend
              + 2,947 × Inventory Availability (%)
              + 13,313 × Customer Rating
              + 40,131 × type_Airport
              + 16,200 × type_High_Street
              + 26,343 × type_Mall
```

**Advantages:**
- Highest explanatory power (R² = 0.8192; Adjusted R² = 0.8150).
- Captures the incremental contribution of each driver after controlling for others.
- Includes operational levers (marketing spend, inventory), traffic metrics (footfall), and structural factors (store type).
- All predictors are statistically significant at the 5% level or better.

**Limitations:**
- More complex to interpret for non-technical audiences.
- Does not capture time-series effects, seasonality, or store-level fixed effects.
- Missing value imputation was required for customer_rating (8 observations) and competitor_distance_km (6 observations); competitor_distance_km was excluded from the final model due to low correlation.
- Regression demonstrates association, not causation.

**Business Usefulness:**
- Provides the most comprehensive and actionable insight for leadership.
- Enables decomposition of expected sales by each driver, supporting scenario planning and budget decisions.

---

## Final Selected Model

**Selected Model: Model 3 — Multiple Regression (Full Model)**

**Justification:**  
Model 3 is selected as the final model on the following grounds:

1. **Highest R² and Adjusted R²:** The model explains approximately 81.9% of variance in monthly sales — a substantial improvement over Model 1 (73.5%) and Model 2 (15.7%). The Adjusted R² of 0.8150 confirms that the improvement is not merely an artefact of adding more variables.

2. **All predictors statistically significant:** Every coefficient in Model 3 carries a p-value below 0.05, with footfall, marketing spend, inventory availability, airport dummy, and mall dummy all significant at the 0.001 level. This eliminates the risk of overfitting through noise variables.

3. **Business completeness:** Unlike the simple regressions, Model 3 simultaneously captures customer traffic, marketing investment, operational performance, and store-type effects — providing leadership with a multi-dimensional view of what drives sales.

4. **Actionability:** Of the seven predictors, four are directly controllable by the business (marketing spend, inventory availability, store type through investment decisions, and indirectly customer rating through service quality). This makes the model directly useful for strategic planning.

---

## Model Comparison Summary Chart

| Metric | Model 1 | Model 2 | Model 3 |
|---|---|---|---|
| R² | 0.7348 | 0.1574 | **0.8192** |
| Adjusted R² | 0.7340 | 0.1549 | **0.8150** |
| No. of Predictors | 1 | 1 | 7 |
| All Predictors Significant? | Yes | Yes | **Yes** |
| Actionable for Leadership? | Partially | Partially | **Yes** |
| Recommended? | Baseline only | Supplementary only | **✓ Yes — Final Model** |

---

*This document forms part of the Business Analytics Assignment — Part 3: Regression Insights.*

# Final Business Recommendation
**Project:** Retail Chain Monthly Sales — Regression Analysis  
**Prepared For:** Executive Leadership Team  
**Prepared By:** Business Analytics Team  
**Date:** June 2025  
**Analytical Method:** OLS Multiple Regression  
**Dataset:** 320 store-month observations across 80 stores, 4 regions, 4 store types

---

## Executive Summary

This analysis used Ordinary Least Squares (OLS) regression to identify and quantify the factors most strongly associated with monthly sales performance across the retail chain. The final selected model — a multiple regression incorporating footfall, marketing spend, inventory availability, customer satisfaction rating, and store-type dummy variables — explains **81.9% of the variation in monthly sales** (R² = 0.8192, Adjusted R² = 0.8150) using data from 306 cleaned observations.

**Key finding:** Footfall (customer visit volume) is the dominant driver of monthly sales, followed by store type, inventory availability, marketing spend, and customer rating. All five categories of predictor are statistically significant at the 5% level or better.

Leadership is recommended to prioritise footfall generation, inventory availability optimisation, and store-type-informed investment allocation as the primary levers for sustainable sales growth.

---

## Key Drivers of Monthly Sales

The following table ranks each identified driver by the strength of its association with monthly sales, based on the multiple regression coefficients and significance levels:

| Priority | Driver | Coefficient | p-value | Significance |
|---|---|---|---|---|
| 1 | **Footfall** | +£33.80 per additional visitor | < 0.001 | *** Highly Significant |
| 2 | **Store Type: Airport** | +£40,131 vs Residential | < 0.001 | *** Highly Significant |
| 3 | **Store Type: Mall** | +£26,343 vs Residential | < 0.001 | *** Highly Significant |
| 4 | **Inventory Availability (%)** | +£2,947 per 1 pp increase | < 0.001 | *** Highly Significant |
| 5 | **Marketing Spend** | +£1.19 per £1 spent | < 0.001 | *** Highly Significant |
| 6 | **Store Type: High Street** | +£16,200 vs Residential | 0.010 | * Significant |
| 7 | **Customer Rating** | +£13,313 per 1-point increase | 0.007 | ** Significant |

*Note: Competitor distance, staff count, and discount percentage were excluded from the final model due to low correlation with monthly sales (all below 0.10 in absolute terms) or data quality limitations.*

---

## Variables Leadership Should Prioritise

### 1. Footfall — Highest Priority

Footfall is the single most powerful predictor of monthly sales (R² = 0.7348 in isolation). Every additional 1,000 visitors generates approximately **£33,800 in additional monthly revenue** after controlling for other factors.

**Recommended Actions:**
- Invest in footfall analytics at store level to identify peak and trough periods.
- Design localised marketing campaigns and in-store events specifically aimed at increasing visitor volume.
- Prioritise store formats and locations (Airport, Mall) that structurally generate higher footfall.
- Monitor competitor openings and closures, as these directly affect catchment-area footfall.

---

### 2. Inventory Availability — Operational Priority

Each one-percentage-point improvement in inventory availability is associated with **£2,947 in additional monthly sales**. A store improving from 80% to 90% availability would expect approximately **£29,470 more per month** — equivalent to roughly £353,600 annually.

**Recommended Actions:**
- Implement real-time inventory tracking and automated re-ordering thresholds.
- Identify stores with chronically low availability scores and prioritise supply chain intervention.
- Investigate which SKU categories drive the most out-of-stock events and implement demand-responsive replenishment.

---

### 3. Marketing Spend — Investment Lever

Marketing spend carries a statistically significant positive coefficient (+£1.19 per £1 invested) but with a **diminishing returns caveat.** The data shows that the store with the highest marketing spend in the dataset (STR-1007, £172,415 in a single month) generated below-predicted sales, suggesting that raw spend above a threshold may not yield proportionate returns.

**Recommended Actions:**
- Establish a marketing spend efficiency dashboard tracking revenue per £1 of marketing by store and campaign type.
- Redirect investment from high-spend, low-return stores toward medium-spend stores with strong footfall conversion potential.
- Test different campaign formats (digital, in-store, loyalty) to identify optimal spend allocation.

---

### 4. Customer Rating — Service Quality Investment

Each one-point improvement in average customer rating is associated with **£13,313 in additional monthly sales**. While this is smaller in magnitude than footfall or store type effects, it represents a controllable variable that compounds over time through repeat visits and word-of-mouth.

**Recommended Actions:**
- Establish a quarterly service quality review programme across all stores.
- Investigate stores with below-average ratings (below 3.5) for staffing, training, or operational issues.
- Link customer satisfaction scores to store management performance reviews.

---

## Variables That Should Not Be Over-Interpreted

### Average Discount Percentage (avg_discount_pct)

This variable showed a low and slightly negative correlation with monthly sales (−0.076) and was not included in the final model. This does not mean discounting is ineffective in all contexts; rather, within this dataset, across all store types and months, the discount level does not have a strong linear relationship with total sales revenue. Heavy discounting may increase unit volume while reducing revenue value.

**Caution:** Do not interpret this finding as evidence that discounts should be eliminated. Discounting strategy interacts with margin management (see monthly_profit) and should be evaluated in a separate profitability analysis.

### Competitor Distance (competitor_distance_km)

Low correlation with monthly sales (−0.099) and missing values (6 observations) led to exclusion from the final model. This variable may have indirect effects through footfall that are already captured in the footfall coefficient.

### Holiday Flag (holiday_flag)

This binary variable was not included in the final model due to low marginal contribution. The single binary flag does not differentiate between major commercial holidays (Christmas, Easter) and minor ones, which likely dilutes its explanatory power.

---

## Recommended Business Actions — Summary

| Action | Driver | Expected Impact | Priority |
|---|---|---|---|
| Launch footfall-driving local marketing events | Footfall | +£33,800 per 1,000 additional visitors | Immediate |
| Improve inventory availability across all stores | Inventory Availability | +£29,470/month per 10pp improvement | Immediate |
| Reallocate marketing budget from low-ROI to high-ROI stores | Marketing Spend | Improve revenue per £1 marketing | Short-term |
| Implement service quality training programme | Customer Rating | +£13,313 per 1-point improvement | Short-term |
| Prioritise Airport and Mall store investments | Store Type | +£40,131 (Airport) or +£26,343 (Mall) vs Residential | Medium-term |
| Investigate and replicate top residual store practices | Best practice sharing | Reduce unexplained variance | Short-term |
| Audit marketing ROI for STR-1007 and similar stores | Marketing Efficiency | Recover misallocated spend | Immediate |

---

## Risks

1. **Multicollinearity:** Footfall and staff count are highly correlated (r ≈ 0.80). Staff count was excluded from the final model to avoid inflation of standard errors. If staffing is a primary management lever, a separate regression model with staff count as the key predictor is recommended.

2. **Omitted Variable Bias:** The model explains 81.9% of variance but not 100%. Unmeasured variables such as local demographic profile, competitor promotions, weather, and store-specific operational quality may account for the remaining unexplained variation.

3. **Reverse Causality:** Some relationships may run in the opposite direction. For example, high-performing stores may receive larger marketing budgets — making it appear that marketing drives sales when the causation is partially reversed. Experimental methods (e.g., A/B testing of marketing campaigns) would be required to establish causality.

4. **Temporal Limitations:** The dataset covers only four months (January–April 2025). Seasonal effects, annual trends, and long-run dynamics are not captured.

5. **Outlier Influence:** A small number of observations (notably STR-1007 in January 2025 with marketing spend of £172,415 — approximately 3× the average) may exert disproportionate influence on the marketing coefficient.

---

## Limitations

1. **Regression measures association, not causation.** The regression model identifies statistically significant relationships between predictor variables and monthly sales, but this does not mean that changing a predictor *causes* a change in sales. Confounding variables, reverse causality, and omitted factors all limit causal inference. Business decisions informed by this analysis should be validated through controlled experiments wherever possible.

2. **Linear relationships assumed.** OLS regression assumes linear relationships between predictors and the outcome. In practice, relationships such as between marketing spend and sales may exhibit diminishing returns (a concave curve) that a linear model underestimates at extreme values.

3. **Data quality:** Eight observations had missing customer_rating values and six had missing competitor_distance_km values. These were excluded from the analysis. If missing values are non-random (e.g., poorly performing stores are less likely to collect ratings), this could introduce selection bias.

4. **Aggregation effects:** The dataset operates at the store-month level. Results may not translate directly to individual transaction or customer-level decisions.

5. **Generalisability:** Findings are based on 80 stores observed over four months. The model's accuracy for new stores, different time periods, or significantly different market conditions is uncertain.

---

## Why Regression Demonstrates Association Rather Than Causation

Regression analysis identifies the statistical relationship between variables — how much monthly sales tend to change when a predictor changes, holding other modelled variables constant. However, three fundamental reasons prevent regression alone from establishing causation:

**1. Reverse Causality:** The direction of influence may be the opposite of what is modelled. Stores with high sales may attract larger marketing budgets, meaning marketing spend is a consequence of sales performance rather than a cause.

**2. Confounding Variables:** Variables not included in the model may simultaneously influence both a predictor and monthly sales. For example, store location quality may drive both footfall and sales independently — making footfall appear to cause sales when both are caused by a third unobserved factor.

**3. Selection Effects:** Stores that adopt certain strategies (e.g., high inventory availability) may differ systematically from others in ways that also influence sales, creating a spurious association that does not represent a general causal relationship.

**Establishing causation requires:** controlled experiments (randomised allocation of marketing budgets across comparable stores), longitudinal panel analysis (tracking changes within the same store over time), or natural experiments (exploiting exogenous shocks such as sudden competitor closures).

Leadership is advised to use this regression analysis as a foundation for hypothesis generation and targeted experimentation, rather than as definitive evidence for causal mechanisms.

---

*This document forms part of the Business Analytics Assignment — Part 3: Regression Insights.*

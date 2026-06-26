# Residual Analysis Report
**Project:** Retail Chain Sales Regression Analysis  
**Model:** Multiple Regression — Full Model (Model 3)  
**Analyst:** Business Analytics Team  
**Date:** June 2025

---

## Overview

Residual analysis is a critical diagnostic step in regression modelling. A residual represents the difference between the actual observed value and the value predicted by the regression model:

**Residual = Actual Monthly Sales − Predicted Monthly Sales**

A well-specified model produces residuals that are approximately normally distributed with a mean close to zero, no systematic pattern, and no obvious relationship with the predicted values (homoscedasticity). Large residuals — either positive or negative — indicate observations where the model's prediction deviates substantially from reality, which can reveal important business insights or model limitations.

---

## Residual Summary Statistics

| Statistic | Value |
|---|---|
| Number of Observations (n) | 306 |
| Mean Residual | ≈ 0 (by construction) |
| Minimum Residual | −149,523 |
| Maximum Residual | +105,916 |
| Approximate Residual Std Dev | ~44,200 |
| Approximate Range | −149,523 to +105,916 |

---

## Top 5 Positive Residuals (Model Under-Predicts)

These are cases where actual sales significantly **exceeded** model predictions. The model underestimated performance for these store-months.

| Rank | Store ID | Month | Actual Sales (£) | Predicted Sales (£) | Residual (£) |
|---|---|---|---|---|---|
| 1 | STR-1028 | April 2025 | 713,611 | 607,695 | **+105,916** |
| 2 | STR-1073 | March 2025 | 813,317 | 714,905 | **+98,412** |
| 3 | STR-1069 | April 2025 | 686,738 | 593,927 | **+92,811** |
| 4 | STR-1030 | February 2025 | 820,519 | 728,154 | **+92,365** |
| 5 | STR-1075 | February 2025 | 763,162 | 673,586 | **+89,577** |

### Possible Business Reasons for Positive Residuals

1. **Local Events or Promotions:** A store may have benefited from a community event, sports fixture, or competitor closure that temporarily boosted traffic and sales beyond what the measured variables can explain.

2. **Seasonal or Festive Uplift:** Specific months (February — Valentine's Day; March/April — Easter period) may coincide with local shopping spikes not fully captured by the holiday_flag binary variable.

3. **Unreported Marketing Activity:** In-store activations, loyalty reward campaigns, or local media coverage may have driven footfall and conversion beyond the recorded marketing_spend figure.

4. **Staff Performance and Service Quality:** A high-performing store team may have improved conversion rates and average transaction values beyond what customer_rating captures.

5. **Supply Chain Advantage:** Temporarily superior inventory mix (right products, right time) beyond what inventory_availability_pct measures.

**Business Implication:** These stores are outperforming the model's predictions. Leadership should investigate what these stores are doing differently. Best practices identified could be replicated across the estate.

---

## Top 5 Negative Residuals (Model Over-Predicts)

These are cases where actual sales significantly **fell short of** model predictions. The model overestimated performance for these store-months.

| Rank | Store ID | Month | Actual Sales (£) | Predicted Sales (£) | Residual (£) |
|---|---|---|---|---|---|
| 1 | STR-1017 | March 2025 | 685,379 | 834,902 | **−149,523** |
| 2 | STR-1023 | February 2025 | 627,172 | 758,355 | **−131,183** |
| 3 | STR-1012 | January 2025 | 595,468 | 706,417 | **−110,950** |
| 4 | STR-1009 | January 2025 | 641,865 | 749,471 | **−107,606** |
| 5 | STR-1007 | February 2025 | 800,452 | 904,080 | **−103,628** |

### Possible Business Reasons for Negative Residuals

1. **Operational Disruptions:** Temporary closures, refurbishment works, supply chain failures, or staffing shortages could have depressed sales below what visitor volume and marketing investment would ordinarily generate.

2. **Conversion Rate Issues:** High footfall does not guarantee high sales. Stores with poor product availability, checkout congestion, or weak service may attract visitors who do not purchase.

3. **High Discount Impact on Revenue:** Large discounts may inflate footfall but reduce the average transaction value, causing sales revenue (in pounds) to underperform relative to visitor volume.

4. **Competitive Activity:** New competitor entry nearby or aggressive competitor promotions during that month could have diverted spending even from stores with strong metrics.

5. **Localised Economic Shocks:** Specific store catchment areas may have experienced local economic downturns (factory closures, job losses) during the observation period.

6. **Marketing Inefficiency:** Some of the largest marketing spends in the dataset (STR-1007 had marketing spend of £172,415 in February — the highest in the dataset) did not generate proportionate sales uplift, suggesting diminishing returns or poor campaign targeting.

**Business Implication:** These stores are underperforming against model expectations. Leadership should investigate root causes. Stores such as STR-1007 with very high marketing spend but below-expected sales warrant an urgent review of marketing ROI and campaign effectiveness.

---

## Overall Model Assessment

### Does the Model Systematically Under-Predict?

No. The mean residual is approximately zero by construction. Positive and negative residuals are distributed on both sides of the prediction line.

### Does the Model Systematically Over-Predict?

The largest individual residuals are negative (maximum = −£149,523 for STR-1017), suggesting that some extreme under-performance cases are harder to predict. However, this does not indicate a systematic directional bias in the overall model.

### Homoscedasticity Assessment

Visual inspection of a residuals-versus-fitted plot (see `screenshots/residuals_preview.png`) suggests residuals are broadly distributed without a strong funnel pattern. However, some larger predictions do appear associated with slightly larger residuals, which is a common feature of retail sales data where higher-volume stores naturally exhibit higher absolute variability.

### Normality of Residuals

The residual distribution is approximately symmetric around zero, consistent with the assumption of normally distributed errors. Minor deviations may be attributable to store-level heterogeneity not fully captured by the current predictor set.

---

## Recommendations Based on Residual Analysis

1. **Investigate STR-1017 March 2025:** The largest single negative residual (−£149,523) despite high footfall and marketing spend warrants immediate investigation. The recorded marketing spend of £79,346 in that month is above average, yet sales fell significantly short of predictions.

2. **Identify Best Practices from Positive Outliers:** STR-1028, STR-1073, and STR-1030 consistently exceed predictions. Qualitative investigation of these stores' practices, staffing, and local strategies could yield transferable insights.

3. **Review Marketing ROI for STR-1007:** This store recorded the highest marketing spend in the dataset (£172,415 in January 2025) but regularly appears in under-performance analysis. This suggests potential marketing inefficiency or misalignment of campaign type with the store's catchment area.

4. **Consider Additional Predictors:** Residual patterns suggest that variables not currently in the model — such as local competition index, seasonality dummies, or store manager tenure — could further improve predictive accuracy and reduce unexplained variance.

5. **Expand the Holiday Flag:** The current binary holiday_flag does not distinguish between major and minor holidays. Replacing it with a more granular calendar event variable could reduce systematic prediction error in certain months.

---

*This document forms part of the Business Analytics Assignment — Part 3: Regression Insights.*

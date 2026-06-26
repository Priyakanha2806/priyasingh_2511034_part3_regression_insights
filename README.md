# priyasingh_2511034_part3_regression_insights

## Business Analytics Assignment – Part 3: Regression-Based Business Insights

---

# Business Problem Summary

This project analyzes the factors influencing monthly sales across retail stores using regression analysis. The objective is to identify which business variables have the strongest association with monthly sales and provide data-driven recommendations for management.

---

# Dataset Description

**Dataset:** business_regression_data.xlsx

The dataset contains retail store performance data including:

- Monthly Sales (Dependent Variable)
- Marketing Spend
- Footfall
- Inventory Availability (%)
- Customer Rating
- Average Discount (%)
- Store Type
- Region
- Staff Count
- Holiday Flag
- Competitor Distance

After cleaning the data, regression analysis was performed on the prepared dataset.

---

# Dependent Variable

- **monthly_sales**

---

# Independent Variables

The following variables were considered:

- footfall
- marketing_spend
- inventory_availability_pct
- customer_rating
- avg_discount_pct
- store_type
- region

Variables such as Store ID and Month were excluded because they are identifiers rather than predictors.

---

# Regression Approach

The following analyses were completed:

- Data cleaning
- Dummy variable creation
- Simple Linear Regression Model 1
- Simple Linear Regression Model 2
- Multiple Linear Regression
- Model comparison
- Predicted value calculation
- Residual analysis

Regression models were created using Microsoft Excel Regression ToolPak.

---

# Dummy Variable Approach

The categorical variable **store_type** was converted into dummy variables.

Reference Category:

**Residential**

Dummy variables created:

- type_Airport
- type_High_Street
- type_Mall

Residential was omitted to avoid the dummy variable trap.

---

# Model Comparison Summary

Three regression models were compared.

### Model 1
Simple Regression

Dependent Variable:
- monthly_sales

Predictor:
- footfall

---

### Model 2
Simple Regression

Dependent Variable:
- monthly_sales

Predictor:
- marketing_spend

---

### Model 3
Multiple Regression

Dependent Variable:
- monthly_sales

Predictors:

- footfall
- marketing_spend
- inventory_availability_pct
- customer_rating
- type_Airport
- type_High_Street
- type_Mall

The Multiple Regression model achieved the highest explanatory power and was selected as the final model.

---

# Final Model Selected

The Multiple Regression model was selected because:

- Highest R²
- Better explanatory power
- Includes multiple business drivers
- Includes dummy variables for store type
- Provides stronger business insights

---

# Business Recommendation

Based on the regression analysis:

- Increase customer footfall through marketing campaigns.
- Maintain high inventory availability.
- Improve customer satisfaction.
- Continue investing in effective marketing.
- Consider store type while making expansion decisions.

Regression identifies association between variables but does not prove causation.

---

# Assumptions

The analysis assumes:

- Linear relationships between predictors and sales.
- Independent observations.
- No severe multicollinearity.
- Reasonable residual behavior.
- Cleaned dataset represents actual business conditions.

---

# Limitations

- Regression shows association rather than causation.
- External economic conditions were not included.
- Seasonal effects were not modeled.
- Results depend on available variables.

---

# Repository Structure

```
part3_regression_insights/

├── data/
│   └── business_regression_data.xlsx

├── analysis/
│   ├── regression_workbook.xlsx
│   ├── model_comparison.md
│   └── residual_analysis.md

├── outputs/
│   ├── regression_summary.xlsx
│   ├── final_recommendation.md
│   └── model_equations.md

├── screenshots/
│   ├── simple_regression_output.png
│   ├── multiple_regression_output.png
│   ├── residuals_preview.png
│   └── model_comparison_preview.png

└── README.md
```

---

# Screenshots Included

The repository includes the following screenshots:

- simple_regression_output.png
- multiple_regression_output.png
- residuals_preview.png
- model_comparison_preview.png

These screenshots provide evidence of the regression analysis performed.

---

# Conclusion

This project demonstrates the use of simple and multiple linear regression to identify key drivers of monthly retail sales. The analysis supports business decision-making by highlighting the importance of customer footfall, marketing expenditure, inventory availability, customer ratings, and store type.

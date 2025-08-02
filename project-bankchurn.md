---
layout: default
title: "Bank Churn Prediction"
date: 2025-02-01
categories: [Business Intelligence, Predictive Analytics]
tags: [Excel, Decision Trees, Churn Prediction, Banking Analytics, Manual Modeling]
---

# Bank Churn Prediction 💰

**Project Date:** February 2025  
**Category:** Business Intelligence  

## Project Overview

**Objective:** Identify top predictors of customer churn and build an interpretable model to support retention strategy.

**Data:** Proprietary client attributes dataset (age, credit score, balance, tenure, etc.)

**Methods:**
- Data Cleaning & Preprocessing (Excel)
- Exploratory Data Analysis
- Churn-Weighted Feature Ranking
- Volatility Scoring via Standard Deviation
- Manual Decision Tree Modeling (Lucidchart)
- Model Validation by Logical Split Testing

---

## Key Insights

### 1. Not All High-Churn Groups Are High-Priority

**Critical Finding:** Categories with higher churn rates can represent small population segments—targeting these groups would yield minimal impact despite eye-catching exit scores.

**Example:** Customers aged 31-40 show the highest churn rate but represent under 20% of the client base. Prioritizing them might have less overall impact than focusing on larger segments.

**Statistical Caution:** Clients aged 71-82 showed no churn but make up less than 1% of the dataset—sample size too small for reliable conclusions.

### 2. Sometimes the Right Choice Is Not to Impute—Especially for Complex and Sensitive Variables

**Credit Scores:** Driven by nonlinear historical transaction patterns, credit scores are ethically and statistically problematic to impute. Any fill-in risks misrepresenting individual risk and fairness.

**Estimated Salary Analysis:**
- Explored imputation using subgroup means (by age, gender, country)
- Small group sizes and high variance mean imputation would add more noise than clarity
- No meaningful linear relationship between Estimated Salary and Balance (R² = 0.001) ruled out regression-based imputation

**Decision:** Sensitive fields left as NA to preserve data integrity.

### 3. Highest Exit Risk = No Credit Card + 3+ Products + ≤3 Years Tenure

**Decision Tree Methodology:**
- Used standard deviation of churn scores to prioritize splits (proxy for information gain)
- Split order (tenure before age) balanced generalization and sample size, avoiding over-fragmentation

**Key Risk Groups Identified:**

1. **Highest Risk:** No Pig E. Bank credit card + 3+ products + ≤3 years tenure
2. **Age-Based Risk:** 
   - 41-50 years: Highest weighted exit score
   - 31-40 years: Close second, largest segment by size
3. **Tenure-Based Risk:** Outside 31-50 age range but ≤3 years tenure → 66% exit rate

---

## Exploratory Analysis

### "Decision Gain" Heuristic Attempt

**Approach:** Flagged features by the percentage of their unique values with >50% exit rate ("How often does a value in this feature strongly predict churn?")

**Why It Failed:**
- **Ignores Value Frequency:** Doesn't account for how common each value is
- **No Population Weighting:** Overlooks actual impact on dataset
- **Unique Value Count Issues:** Binary features (e.g., Has Credit Card) appear "flat" even if impactful
- **Misses Variance:** Only counts threshold-passing values, not spread or contrast in churn rates

**Key Lesson:** Early heuristics can mislead if they ignore distribution and variance. Standard deviation (feature volatility) better surfaces features with real decision-making power.

---

## Recommendations

### 1. Cross-check Product Inquiries with Credit Card Ownership
Use "Has Credit Card" as a leading indicator—customers exploring new products without one may be at greater risk of churn.

### 2. Target Feedback Outreach to Newer Clients (≤3 Years Tenure)
Identify early dissatisfaction by proactively surveying or checking in with this high-risk group to address issues before churn occurs.

### 3. Design Loyalty Incentives for Older, Long-term Clients
Reinforce retention among your most stable customer segment (50+ years old with high tenure) to maintain this reliable base.

---

**Tools Used:** Excel, Lucidchart, Statistical Analysis  
**Skills Demonstrated:** Manual Decision Tree Construction, Ethical Data Handling, Feature Engineering, Churn Analysis
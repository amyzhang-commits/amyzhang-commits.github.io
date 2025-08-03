---
layout: default
title: "ClimateWins: Predicting Rain & Climate Drift with Machine Learning"
date: 2025-08-01
categories: [Machine Learning, Climate Science, Advanced Analytics]
tags: [Python, Random Forest, Climate Drift, Proxy Modeling, Feature Engineering, Time Series]
---

# ClimateWins: Predicting Rain & Climate Drift with Machine Learning 🌧️

**Project Date:** August 2025  
**Category:** Machine Learning & Climate Science  
**Project Type:** Final Project Report

## Project Overview

**Objective:** Identify three distinct applications of machine learning that can transform ClimateWin's baseline weather dataset into high-leverage insight workflows for weather forecast and climate change modeling goals.

**Data Source:** European Climate Assessment & Data Set Project (ECA&D)
- **Date Range:** 1960-2022 (62 years of daily observations)
- **Coverage:** 18 weather stations across 10 countries (post data cleaning)
- **Geographic Scope:** Switzerland, Serbia, Austria, Hungary, Spain, Germany, Ireland, Norway, United Kingdom, Sweden, France, Slovenia

**Three Core Experiments:**
1. **From Rainfall to Rainfall Risk** - Binary target transformation for station-level prediction
2. **Derived Drift** - Climate instability detection using time-aware validation
3. **Munich "Proxycraft"** - Missing data reconstruction through proxy modeling

---

## Experiment 1: From Rainfall to Rainfall Risk ☔

### Problem Statement

**Data Quality Issues:**
- Precipitation values inconsistent across stations
- VALENTIA: Single 90mm spike (valid but distributionally extreme)
- Other stations: Max ~14mm/day (implausibly low for regional norms)
- No safe scaling method without major assumptions

### Solution: Binary Reframing

**Approach:** Transform to binary target: "Did it rain tomorrow?"

**Benefits:**
- Simplifies target, avoids raw measurement pitfalls
- Supports weather risk forecasting despite messy input
- Provides actionable signal over precise data

### Methodology

**ML Preparation Decisions:**
1. Trimmed date range to 1960–2019 for consistency
2. Retained imperfect stations to:
   - Test real-world incomplete dataset scenarios
   - Evaluate ML's ability to learn from proxy patterns
   - Leverage feature correlations to fill semantic gaps
   - Assess robustness with incomplete data

### Results: Feature Importance Analysis

**Key Findings from Random Forest per Station:**

**Dominant Predictors:**
- **Air Pressure:** Most predictive feature across majority of stations
- **Hyperlocal Variation:** Shared top features but varying weights by station
- **Coefficient of Variance:** 0.56 – 1.07 in importance weights

**Adaptive Behavior:**
- **Kassel** (missing Cloud Cover): Compensates with Sunshine
- **Tours** (missing Cloud Cover + Sunshine): Relies on Temp Max + Humidity

### Performance Overview

**Results:** Macro F1 Score ~0.65 with narrow interquartile range

**Key Insights:**
- **Strong Consistency:** Similar performance across stations despite inconsistent inputs
- **Notable Outliers:**
  - **MUNCHENB:** Poor performance likely due to missing pressure readings
  - **BUDAPEST:** Poor performance despite complete feature set

**Conclusion:** Per-station models enable tailored learning amid data variability; performance consistency reinforces feasibility of ML-driven rain risk detection from messy legacy datasets.

---

## Experiment 2: Derived Drift 📈

### Motivation
Investigation of BUDAPEST's poor performance revealed potential climate drift between training and test periods.

### Step 1: Distribution Check

**Method:** Used rainy day counts to probe baseline class balance across stations.

**Key Findings:**
- **VALENTIA & KASSEL:** High rain counts + high Macro-F1
- **MADRID:** Lowest rain count but strong performance (class imbalance benefits recall)
- **SONNBLICK:** High rain, average Macro-F1 (not all high-rain stations overperform)
- **BUDAPEST:** Low rain, very poor Macro-F1 (45.8%) suggesting alternative failure mode

### Step 2: Temporal Distribution Analysis

**Insight:** BUDAPEST's poor macro-F1 despite typical accuracy (~67%) signals temporal drift.

**Distribution Comparison Results:**
- **KASSEL & VALENTIA:** Test sets show sharp spikes in months with 28+ rainy days
- **KASSEL:** Spike has no overlap with training distribution
- **Stable Stations** (e.g., SONNBLICK): Training/test distributions remain aligned

**BUDAPEST Specific Finding:**
Training set (1960–2007) shows clear spike around 12–13 rainy days/month, absent in test period (2007–2019). This mismatch signals climate drift, likely impacting model performance through overfitting to diminished regime.

### Step 3: Smoothed Predictor Testing

**Method:** Applied rolling averages and momentum metrics as climate drift sensitivity test.

**Results:**
- Minimal change in macro-F1 (±0.01–0.03)
- Station ranking largely unchanged
- Slight accuracy improvement: 65.2% → 65.7%
- Pressure-related predictors remain top features

### Step 4: Limitations & Future Directions

**Current Limitations:**
- Neither K-Means nor manual grouping revealed clear regional drift patterns
- Rain rate delta serves as coarse proxy; excludes seasonality, pressure, humidity
- Madrid case suggests smoothing may suppress edge signals

**Innovation Opportunity:** Reframe model misses as potential climate signals rather than errors.

**Next Steps:**
- Monitor probabilistic residuals and confidence drift
- Apply unsupervised detectors (Isolation Forest) to feature space
- Develop multi-factor drift index for richer change sensitivity

---

## Experiment 3: Munich "Proxycraft" 🔧

### Problem
Munich severely underperformed (Macro F1: 54.4%) due to complete absence of pressure readings—the most globally important rain predictor.

### Solution: Feature-Based Proxy Modeling

**Approach:**
1. Trained nonlinear regression model on stations with complete feature sets
2. Learned pressure behavior patterns across input variables
3. Applied model to reconstruct synthetic pressure values for Munich
4. Re-ran Random Forest with reconstructed data

### Results

**Performance Improvement:**
- **Before:** Macro F1 = 54.4%
- **After:** Macro F1 = 63.6%
- Munich's performance now aligns with global station average

**Key Insight:** Feature-based proxy modeling proves more accurate and scalable than geographic clustering for reconstructing missing sensor data.

---

## Technical Innovations

### 1. Binary Target Transformation
**Innovation:** Converting messy precipitation measurements to actionable binary risk predictions.
**Impact:** Enables robust forecasting despite data quality issues.

### 2. Climate Drift Detection Framework
**Innovation:** Time-aware validation combined with derived features to identify temporal instability.
**Impact:** Model failures become climate change signals rather than mere errors.

### 3. Meteorological Proxy Modeling
**Innovation:** Learning relationships between weather variables to reconstruct missing data.
**Impact:** Favors scientific relationships over spatial assumptions for data reconstruction.

---

## Final Recommendations

### 🌍 1. From Rainfall to Rainfall Risk
Use binary station-level models to forecast rain likelihood, not raw volume—enabling smarter, localized risk assessments that are robust to measurement inconsistencies.

### 🌍 2. Detecting Drift, Not Just Decay
- Leverage derived features + time-aware validation to probe for model instability
- Develop multi-factor drift index and apply unsupervised methods to detect shifting climate signals
- **Key Insight:** For ClimateWins, model failures may indicate where climate is shifting fastest, helping prioritize high-fidelity data collection in volatile regions

### 🌍 3. Proxy with Purpose
- For missing sensor data, use feature-based proxy modeling, not geographic duplication
- Favor meteorological relationships over spatial assumptions for reconstructing high-impact variables like pressure
- **Scalability:** Approach generalizes to other missing variables and sensor networks

---

## Strategic Impact for ClimateWins

**Operational Advantages:**
- **Risk-Based Forecasting:** More actionable than raw precipitation values
- **Quality-Agnostic Models:** Function effectively with imperfect legacy data
- **Adaptive Reconstruction:** Systematic approach to missing data challenges
- **Climate Signal Detection:** Transform model limitations into scientific insights

**Future Applications:**
- Early warning systems for extreme weather events
- Regional climate monitoring and intervention prioritization
- Sensor network optimization based on proxy model performance
- Long-term climate trend validation through drift detection

---

**Tools Used:** Python, Random Forest, Feature Engineering, Time Series Analysis, Proxy Modeling  
**Skills Demonstrated:** Advanced ML Pipeline Design, Climate Data Science, Missing Data Imputation, Temporal Validation, Scientific Problem Reframing
---
layout: default
title: "ClimateWins: Weather Conditions & Climate Change Analysis"
date: 2025-06-01
categories: [Machine Learning, Climate Science, Public Policy]
tags: [Python, Machine Learning, Neural Networks, Decision Trees, Climate Data, Ethical AI]
---

# ClimateWins: Weather Conditions & Climate Change Analysis 🌍

**Project Date:** June 2025  
**Category:** Machine Learning & Climate Science  
**Project Type:** Interim Research Report

## Project Overview

**Objective:** Assess machine learning tools for enabling ClimateWins, a non-profit, to predict climate change impacts—beginning with the categorization of mainland Europe weather data.

**Data Source:** European Climate Assessment & Data Set Project (ECA&D)
- **Date Range:** 1960-2022 (62 years of daily observations)
- **Coverage:** 18 weather stations across mainland Europe
- **Provenance:** Public initiative established in 1998 by EUMETNET with European Commission support

**Research Structure:**
1. **Data Provenance & Ethical Considerations**
2. **Machine Learning Foundations & Hypotheses**
3. **Preliminary ML Model Evaluations**

---

## I. Data Provenance: Ethical Considerations & Data Integrity

### Dataset Overview
- **Full Weather Dataset:** Daily records across 18 stations with comprehensive weather metrics
- **Pleasant Weather Subset:** Binary classification dataset (1 = Pleasant, 0 = Unpleasant)

### Critical Bias Identification

#### #1: Geographic Coverage Bias
**Problem:** Tours (France), Roma (Italy), and Gdansk (Poland) excluded from "pleasant weather" subset—each was the only station representing its country.

**Impact:** 
- Spain now the sole warm-climate representative
- Germany has 3 stations, Netherlands has 2
- Geographic gaps risk model overfitting to well-sampled regions

#### #2: Feature Completeness Bias
**Problem:** Only 7 of 18 stations record snow depth; only Basel, Düsseldorf, and Oslo have complete weather records.

**Impact:** Incomplete features often dropped for ML compatibility, leading to overrepresentation of simple weather profiles over complex/volatile contexts.

#### #3: Subjectivity in Labeling
**Examples:**
- Sonnblick (Austria): 0 "pleasant" days
- Madrid (Spain): ~50/50 split, average pleasantness ~45%

**Impact:** Boolean labels encode narrow thresholds reflecting implicit normative assumptions about comfort, potentially shaping downstream model behavior and resource allocation decisions.

---

## II. Machine Learning Foundations & Hypotheses

### Hypothesis #1: Unlocking Emergent Patterns with ML
**Traditional Analysis Limitation:** Shows broad seasonal trends but short-term fluctuations often defy visual explanation.

**ML Advantage:** Can analyze complex, nonlinear relationships to identify subtler climate dynamics beyond visual patterns.

### Hypothesis #2: Weather as Web – Tapping Feature Interdependencies
**Identified Relationships:**
- ☁️ Humidity ↔ Cloud Cover ↔ Precipitation
- ☀️ Radiation ↔ Sunshine ↔ Temperature

**Hypothesis:** ML models can leverage correlated feature clusters as composite predictors, achieving more robust, context-aware forecasts.

### Hypothesis #3: Temporal Drift in Weather Dynamics
**Observation:** Color-coded outliers reveal emerging "new normals"—rising temperatures and reduced snowfall make older data points increasingly appear as outliers.

**Hypothesis:** ML models trained on historical climate data may underperform as key variables drift over time, reducing predictive accuracy.

---

## III. Preliminary ML Model Evaluations

### Models Tested
- 🤖 **ANN:** Artificial Neural Network (Logistic Regression & Multi-Layer Perceptron)
- 📍 **KNN:** K-Nearest Neighbor  
- 📈 **Linear Regression:** (Univariate models with gradient descent)
- 🌳 **Decision Tree:** (Greedy vs. gradient-based optimization)

### Linear Regression Analysis: Oslo 2019

**Model Comparison:**
1. **Temperature vs. Time:** θ₁ = 0.16, Final MSE = 0.487
2. **Temperature vs. Global Radiation:** θ₁ = 0.69, Final MSE = 0.260

**Key Insight:** Global radiation proved more relevant due to stronger linear relationship, creating more informative gradient terrain for optimization.

**Surface Plot Analysis:**
- **Model 1 (Time):** Shorter, misaligned trajectory indicating flatter, noisier surface with weaker gradient signals
- **Model 2 (Radiation):** Longer, curved path reflecting directional loss surface with strong gradients guiding toward minimum

### Classification Results

#### 🤖 Artificial Neural Network
**Architecture Tested:**
- Logistic Regression (single-layer)
- Multi-Layer Perceptron (MLP)

**Result:** MLP outperformed logistic regression in both starting performance and generalization capability.

#### 📍 K-Nearest Neighbor (KNN)
**Performance:** 96% accuracy on unseen data with optimal K=8

**Precision & Recall:**
- **Unpleasant class:** 98% precision, 97% recall
- **Pleasant class:** 85% precision, 91% recall

**Note:** Lower precision on Pleasant class reflects class imbalance—fewer Pleasant examples make accurate predictions harder despite good coverage.

#### 🌳 Decision Tree
**Performance:** Perfect accuracy and recall

**Validation:** Audit confirmed DT rules exactly match original labels, indicating fully separable dataset rather than overfitting.

---

## Model Recommendations & Analysis

### 1. 🌳 Decision Tree (Recommended)
**Strengths:**
- Perfect accuracy and recall for this dataset
- Ideal for deterministic, rule-based data
- High interpretability

**Caveat:** Future data might be less clean—need clearer "pleasant weather" definitions

### 2. 🤖 Multi-Layer Perceptron ANN (Future-Ready)
**Strengths:**
- Strong performance across all metrics
- Better suited for complex, real-world patterns
- Capacity for nonlinear relationships

**Trade-off:** Higher computational cost but manageable

### 3. 📍 KNN (Solid Baseline)
**Strengths:**
- Solid accuracy and recall
- Instance-based approach

**Limitations:**
- Non-inductive nature limits adaptability
- May struggle with data drift common in weather data

### 4. 🤖 Logistic Regression ANN (Prototype-Friendly)
**Strengths:**
- Lowest computational cost
- Simple architecture
- Good for fast prototyping

**Limitations:** May require hyperparameter tuning for performance improvements

---

## Final Recommendations

### 1. Model Selection
**Choose Decision Tree (🌳)** for current task and dataset—combines accuracy with interpretability.

### 2. Bias Mitigation
**Subset data by region** to address geographic and feature biases while handling subjective "pleasantness" definitions.

### 3. Future Expansion Strategy
- Develop more nuanced "pleasantness" criteria
- Broaden dataset coverage
- Explore flexible models like MLP when complexity grows

---

## Technical Contributions

**Methodological Innovations:**
- Comprehensive bias audit of climate datasets
- Multi-dimensional model comparison framework
- Integration of ethical considerations into ML pipeline
- Gradient descent visualization for feature selection validation

**Skills Demonstrated:** Machine Learning Pipeline Development, Ethical AI Assessment, Climate Data Analysis, Model Interpretation, Bias Detection

---

**Tools Used:** Python, Machine Learning (ANN, KNN, Decision Trees, Linear Regression), Data Visualization  
**Domain Impact:** Climate Science, Non-Profit Strategy, Environmental Policy
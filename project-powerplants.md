---
layout: default
title: "Electricity Grid Water Usage Anomaly Detection"
date: 2025-06-01
categories: [Public Policy, Infrastructure, Machine Learning]
tags: [Python, SQL, Machine Learning, Anomaly Detection, Environmental Data, Public Policy]
---

# Hidden Currents: Water Data Quality in the U.S. Power Sector (2015-2023) 🌊

**Project Date:** June 2025  
**Category:** Public Policy & Infrastructure  

## Project Overview

**Objective:** Detect patterns and risks in thermoelectric cooling data to inform real-time anomaly detection for water use reporting.

**Data:** Public datasets from EIA Forms 860 & 923 (2015-2023)

**Methods:**
- Python & SQL
- Data wrangling & subsetting
- Schema normalization & relational modeling
- Data merging & feature engineering
- Machine Learning: Unsupervised (agglomerative clustering, K-means)

**Deliverables:**
- [GitHub: Forthcoming](link-placeholder)
- [Tableau: Hidden Currents Water Data Quality 2015-2023](link-placeholder)

---

## Key Insights

### 1. Missingness Is Structural, Not Random

**Finding:** Reporting gaps cluster by plant type, technology, and scale.

**Raw Missingness Patterns:**
- Highest among Large Thermal Combustion (fossil fuel) plants—mirroring their prevalence
- Non-Steam fossil fuel plants edge out Large Non-Combustion Steam plants
- Reflects post-2015 shifts toward renewables while nuclear remained stagnant

**After Normalization:**
- Medium Thermal Combustion plants rank highest in missing data per plant
- Non-Steam plants (excluding solar and nuclear) show high average missingness rates

**Data Complexity Note:** Apparent label contradictions (e.g., "Non-Steam | Fossil Fuel" and "Large Non-Combustion | Fossil Fuel") reflect mixed-generation facilities and dataset complexity.

**Ranking System:**
- **Rank Total Plants:** Number of unique plants in each group (Rank 1 = most plants)
- **Rank Total Missing:** Total missing data flags (Rank 1 = most missingness)
- **Rank Avg Missing:** Average missingness per plant (Rank 1 = highest average)
- **Rank Avg Plant Missing:** Average missingness rate for individual plants (Rank 1 = highest rate)

### 2. Anomalies Beyond Absence

**Physical Impossibilities:** Some plants report negative water values—implying water is produced during energy generation, which is physically impossible.

**Four Extreme Anomaly Types:**

1. **Implausible Efficiency:** Plants 676 & 6639 show near-identical withdrawal and consumption—suggesting a 1:1 water-use ratio, unlikely for thermal plants

2. **Outlier Spike:** Plant 710 shows a one-time dip in consumption, followed by return to baseline—likely a data entry error

3. **Phantom Activity:** Plant 1262 reports intermittently despite being inactive, distorting missingness metrics

**Implication:** These anomalies should inform a broader suspicion score beyond missingness alone.

### 3. Features That Distinguish Anomalous Plants

**Measuring Influence:** Used variance in normalized suspicion scores to proxy feature influence.

**High-Risk Categories:**
- **Large Non-Combustion plants** (often nuclear) have highest average suspicion score
- **Prime mover = CP (Solar Thermal)** and **fuel type = Solar** rank highly—suggesting reporting irregularity risk
- **Cooling type = Dry/Hybrid** likely ranks due to complexity and paradox of having water data at all
- **Configuration types MC, IG, IB** and **Single Shaft Combined Cycle** consistently high-risk due to technical complexity
- **Combined Heat & Power systems** show elevated risk—tied to operational complexity and edge-case setups

---

## Exploratory Analysis

### 1. Sector Level Water Trends

**Original Goal:** Estimate future water demand from U.S. data centers using EIA datasets as proxy inputs.

**Outcome:** Infeasible—key identifiers (like NAICS) are absent.

**Key Lesson:** Survey-based EIA water data is deeply inconsistent at sector level. United States Geological Survey (USGS)—not EIA—is the more authoritative source for long-term water-use insights.

**Seasonal Trends Observed:**
- Electric Utility may show gradual decline in water withdrawal—possibly efficiency gains
- 2019: Notably elevated consumption across electric utilities
- IPP CHP sector reports implausible spikes and erratic volatility

### 2. From Suspicion Score Logic to the Black Box

**Experiment:** Applied K-Means to 2023 plant data, clustering by Net Generation (MWh) and Water Withdrawal (MG).

**Results:**
- Cluster 1 isolates extreme outliers
- Overlap between Clusters 1 & 3 flags fuzzy boundary—zones worth deeper scrutiny

**Key Reflection:** K-Means proved useful as EDA tool for surfacing promising slices for closer focus. Future work could study how manually generated suspicion scores align with machine-discovered clusters.

---

## Recommendations

### 1. Formalize Suspicion Scoring
Use the suspicion score to label high-suspicion vs. low-suspicion plants (e.g., top 10%, bottom 10%) and train a classifier to distinguish between them. This can reveal which features are most predictive and validate scoring logic consistency with emergent patterns.

### 2. External Validation with USGS Data
Cross-reference water metrics from EIA with USGS datasets to evaluate reporting accuracy in highly suspicious plants. This can help refine and calibrate the scoring system.

### 3. Targeted Investigations & EDA Enhancements
- Use weighted suspicion score to validate clustering outputs—do higher-scoring plants fall into specific unsupervised clusters?
- Dive deeper into 2019's consumption anomalies across sectors
- Develop real-time anomaly detection system for ongoing data quality monitoring

---

**Tools Used:** Python, SQL, Machine Learning (K-Means, Agglomerative Clustering), Tableau  
**Skills Demonstrated:** Anomaly Detection, Data Quality Assessment, Environmental Policy Analysis, Unsupervised Learning
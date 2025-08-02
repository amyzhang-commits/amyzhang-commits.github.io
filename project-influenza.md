---
layout: default
title: "Historical Influenza Patterns in the U.S.: Preparing for the Flu Season"
date: 2024-11-01
categories: [Public Policy, Infrastructure, Healthcare Analytics]
tags: [Tableau, Python, Geospatial Analysis, Public Health, Data Integration]
---

# Historical Influenza Patterns in the U.S.: Preparing for the Flu Season 💉🏥

**Project Date:** November 2024  
**Category:** Public Policy & Infrastructure  

## Project Overview

**Objective:** Identify high-impact times and regions for staffing and vaccination campaigns using flu death trends.

**Data:** 
- CDC Influenza Deaths (2009-2017)
- U.S. Census Population Estimates (2009-2017)

**Methods:**
- Data cleaning, integration, and transformation
- Grouping, sorting, filtering
- Exploratory correlation analysis
- Visual analysis and forecasting in Tableau
- Narrative storytelling for decision support

**Deliverables:**
- [Tableau: Influenza_vers1](link-placeholder)
- [Tableau: Influenza_vers2](link-placeholder)
- [YouTube: Influenza_vers1](link-placeholder)
- [YouTube: Influenza_vers2](link-placeholder)

---

## Key Insights

### 1. Regional & Seasonal Patterns

**Seasonal Trends:**
- Flu season peaks in winter, with possible spring resurgence
- Southern U.S. consistently leads in mortality rates

**Note:** Y-axis scaling may exaggerate visual differences in some charts—an important consideration for data integrity.

### 2. Age-Related Vulnerability

**Critical Finding:** Adults 65+ represent only 10% of the population but account for nearly 66% of flu fatalities.

**Geographic Impact:** States with larger 65+ populations show higher total death counts, highlighting the intersection of demographics and public health outcomes.

### 3. Population-Normalized Risk Analysis

**Key Insight:** Total death counts ≠ individual risk levels

**Example:** California leads in total deaths but ranks low in deaths per capita when normalized by population (deaths per 100,000 residents).

**Implication:** Resource allocation decisions must consider both absolute numbers and per-capita risk.

---

## Exploratory Analysis

### 1. Flu Severity Parsing Index (FSPI)

**Innovation:** Domain-aware proxy for healthcare system context

**Formula:** FSPI = 65+ death rate ÷ overall population death rate

**Benchmark Logic:** In typical systems, 65+ death rate should exceed overall death rate

**Application:** 
- Map FSPI against senior death rate to flag unusual patterns
- Use residuals from trendline as proxy signal for systemic stress or resilience

**Limitations:** Only 9 annual data points per state—insufficient for consistent trend tracking

**Value:** Serves as hypothesis-generation tool for identifying state-specific intervention priorities

### 2. Query Clusters

**Approach:** Hand-crafted clustering using 2D feature space

**Method:** 
- Plotted FSPI against its residual
- Sized points by state population
- Revealed interpretable, cross-regional groupings

**Innovation:** Enables "informed random sampling" for hypothesis generation, moving beyond simple geographic aggregation

**Outcome:** Visual patterns suggest new, data-driven approaches to query healthcare context diversity

---

## Recommendations

### 1. Synchronize National Vaccination Campaigns
Adjust support regionally based on death rates per 100K population. Prioritize the Southern region, which shows both elevated death rates and higher average monthly flu mortality.

### 2. Broaden Priority Metrics Beyond Mortality
Examine patient volume and capacity, not just mortality rates. The medical agency should staff facilities that struggle to manage all flu cases, not only the most severe outcomes.

### 3. Expand Vulnerability Criteria Beyond Age
Integrate additional population segmentation beyond age—such as health insurance status or socioeconomic indicators. Spatial analysis of uninsured populations could refine resource allocation and staffing priorities.

---

**Tools Used:** Tableau, Python, Data Integration  
**Skills Demonstrated:** Geospatial Analysis, Public Health Analytics, Custom Metric Development, Visual Storytelling
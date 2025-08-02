---
layout: default
title: "Instacart Market Basket Analysis"
date: 2025-01-01
categories: [Business Intelligence, Python Analytics]
tags: [Python, Market Basket Analysis, Customer Segmentation, E-commerce, Behavioral Analysis]
---

# Instacart Market Basket Analysis 🛒

**Project Date:** January 2025  
**Category:** Business Intelligence  

## Project Overview

**Objective:** Uncover customer behavior patterns and product purchasing trends to support segmentation and marketing efforts.

**Data:** Instacart online shopping dataset (2017), including orders, products, departments, and customer profiles.

**Methods:**
- Python for data cleaning, merging, aggregation, feature engineering, and exploratory visualization

**Deliverables:**
- [GitHub: Python_InstacartAnalysis](link-placeholder)

---

## Key Insights

### 1. Time-Based Revenue Patterns

**Key Finding:** Revenue spikes outside 1-2pm driven by distinct shopper segments:
- **Early Birds**
- **Evening Shoppers** 
- **Night Owls**

**Strategic Insight:** These non-peak shopper segments drive growth with larger carts and higher-value items. Timing matters—targeted non-peak hours outperform midday in revenue impact.

### 2. Loyalty & Reorder Behavior

**Critical Threshold:** Reorder rates rise sharply after 40-50 orders.

**Behavioral Shift:** Customers transition from exploration phase to habitual buying patterns.

**Business Impact:** Loyalty builds predictable, high-reorder purchase patterns that can be leveraged for inventory planning and personalized marketing.

### 3. Income-Driven Department Trends

**Methodology:** Department purchases were normalized by the number of users in each demographic group to compare average behavior per person rather than total volume—mitigating proportional scaling bias and producing a behavior-adjusted purchasing matrix.

**Key Patterns:**
- **High/Mid-Income:** Dominant in meat & seafood purchases
- **Low-Income:** Dominant in snack buying
- **Staples (frozen, dairy, pantry):** Under-purchased by low-income groups—indicates possible price sensitivity
- **Beverages:** Consistent purchasing across all income groups

---

## Exploratory Analysis

### Department Opportunity Index (Multifactor)

**Innovation:** Built a custom index ranking departments by revenue potential and customer novelty behavior.

**Objective:** Spotlight departments that are high-revenue yet suggestible to experimentation (low reorder rates, potential for "whim" or trial-driven purchases).

**Index Components:**
- **Average revenue per order** → financial value
- **Reorder rate** → habit/loyalty indicator  
- **Non-reorder rate** → novelty/impulse potential

**Strategic Application:** Use insights to design growth campaigns targeting underutilized but high-value departments.

**Technical Lessons Learned:**
- Used rank inversion to weight behavioral gaps—complex but powerful approach
- Ranking-based indexes are intuitive for comparison but sensitive to directionality
- Must stay organized when layering multiple metrics
- Future consideration: Explore z-score or percent-based normalization for smoother weighting, though ranks effectively identified "standouts"

---

## Recommendations

### 1. Align Marketing with Shopper Timing
Proactively adjust marketing campaigns to match time-based shopper profiles—**Early Bird, Midday Shopper, Evening Shopper, and Night Owl**—to capture revenue during peak purchasing windows outside traditional midday hours.

### 2. Boost Customer Adventurousness & Loyalty
- **For Non-Reordering Customers:** Target with promotions that encourage product sampling and experimentation
- **For Regular Shoppers:** Use loyalty programs and personalized offers to increase repeat business and build on established purchasing habits

### 3. Address Price Sensitivity for Staple Goods
For high-volume staple items, implement price-sensitive strategies such as lower price points, bulk discounts, and value packs to counter reduced purchases among low-income groups and expand market accessibility.

---

**Tools Used:** Python, Pandas, Data Visualization  
**Skills Demonstrated:** Feature Engineering, Customer Segmentation, Behavioral Analysis, Custom Metric Development
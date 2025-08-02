---
layout: default
title: "Rockbuster Stealth LLC"
date: 2024-12-01
categories: [Business Intelligence, SQL Analytics]
tags: [SQL, Tableau, Customer Segmentation, Streaming Strategy, Database Management]
---

# Rockbuster Stealth LLC 📼

**Project Date:** December 2024  
**Category:** Business Intelligence  

## Project Overview

**Objective:** Use historical rental data to inform customer segmentation and content prioritization for Rockbuster's upcoming streaming service.

**Data:** SQL-based database including rental transactions, customer demographics, film inventory details, and payment data.

**Methods:**
- Queried and managed relational data using SQL
- Cleaned, filtered, and summarized data for trend analysis
- Joined tables to unify customer, rental, and film information
- Used subqueries and CTEs for layered insights
- Compiled a data dictionary to clarify schema relationships

**Deliverables:**
- [Tableau: Rockbuster_Data_Analysis](link-placeholder)
- [GitHub: SQL_RockbusterStealthAnalysis](link-placeholder)

---

## Key Insights

### 1. Customer Fragmentation: Signal vs. Noise in Geographic Trends

**Challenge:** 87% of countries and 73% of districts have fewer than 10 and 1 customer(s), respectively. Small sample sizes create highly volatile geographic trends.

**Solution:** Normalized key customer metrics by population and tenure, using a behavior-adjusted engagement rate (average rentals per active customer month).

**Key Benchmarks After Normalization:**
- Average monthly rentals per customer: **8.18**
- Average revenue per rental: **$3.81**

### 2. Customer Tenure vs. Engagement

**Critical Finding:** Clear negative correlation between tenure and engagement.

As tenure increases, average monthly rentals per customer decrease, highlighting the need for retention strategies tailored to later stages of the customer lifecycle.

### 3. Revenue Streams: Rentals vs. Late Fees

**Concerning Discovery:** Over 25% of revenue comes from late fees, not actual movie rentals.

**Implications:**
- Indicates a heavily penalty-driven model rather than usage-driven
- Raises sustainability concerns for streaming transition where late fees disappear
- Suggests need for fundamental business model restructuring

---

## Exploratory Analysis

### Product Transition Opportunity: Tiered Plans

**Objective:** Identify behavioral segments to inform a data-driven streaming subscription model.

**Approach:** 
- Plotted each customer's most frequently rented price point (rental rate mode) against population size (proxy for country)
- Used color and size encoding to highlight clusters by rental frequency
- Identified high-engagement users as prime candidates for rewards, loyalty programs, or tiered plans

**Key Insights:**

**Fragmentation Warning:** Top-engaged users are often the only customer in their country—small sample sizes risk over-representing individual behavior.

**Price Segment Patterns:**
- **$0.99:** Most widespread rental rate—broad appeal across geographies
- **$2.99:** Dominant in very small markets (<10 customers)
- **$4.99:** Attracts smaller but concentrated mid-size clusters

**Limitation Identified:** Mode analysis can obscure nuance—doesn't capture price dominance.

**Future Enhancement:** Suggest composite metric: rental frequency × mode strength × price

---

## Recommendations

### 1. Focus on Platform Offerings
Instead of region-based strategies (due to small sample sizes), prioritize expanding inventory in genres with the highest rental rates per available title: **Sci-Fi, Action, and Animation**.

### 2. Retention Strategies Needed
Implement subscription models or loyalty programs to stabilize long-term revenue and address the tenure-engagement decline pattern.

### 3. Late Fees: A Risky Crutch
Introduce tiered subscription plans to transition away from penalty-dependent revenue toward a sustainable, usage-based model that will translate effectively to streaming.

---

**Tools Used:** SQL, Tableau, Database Management  
**Skills Demonstrated:** Complex SQL Queries, Customer Segmentation, Business Model Analysis, Data Normalization
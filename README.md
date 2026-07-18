Olist E-Commerce Logistics & Pricing Optimization

Author: Sienna Yan (Carnegie Mellon University)

Core Stack: Python, Pandas, Matplotlib, Seaborn, Optimization (Greedy Algorithm), Feature Engineering

Business Domain: E-Commerce, Logistics Delay, Dynamic Subsidy, LTV (Life-Time Value)

Executive Summary

This project analyzes over 100,000 real e-commerce transactions from Olist (a leading Brazilian marketplace) to identify critical revenue leakages caused by logistics delays. By developing an LTV-based optimization model and constructing a multi-dimensional "Pain Index", I designed a targeted freight subsidy strategy that maximized customer retention under strict budget constraints, achieving an estimated 30.6x Return on Investment (ROI).

1. Situation (The Business Pain Point)
Olist operates across Brazil, a country with a highly complex and unequal logistics infrastructure.
Customers in remote regions (e.g., Northern states such as AL and MA) pay the highest freight costs across the platform.
Despite paying premium shipping fees, these users suffer the longest delivery delays.
The Impact: This service-price mismatch leads to severe customer dissatisfaction (1-star reviews) and permanent churn among high-net-worth users.

2. Task (The Objective)
To stop the revenue bleeding, the goal was to identify the most heavily impacted geographic regions and deploy a highly efficient financial intervention (subsidies) to retain the most valuable VIP customers, while staying within a tight marketing budget of 5,000 BRL.

3. Action (The Data & Optimization Strategy)
ETL & Data Merging: Merged 4 fragmented databases (Orders, Items, Customers, Reviews) to map the entire customer journey and engineered a new metric, Delay_Days.
Composite "Pain Index" Construction (V2): Recognizing that both extreme delays and exorbitant freight costs drive churn, I developed a weighted Pain Index. Since 'days' and 'currency' have different units, I applied Min-Max Scaling to normalize both variables (0-1 range) before combining them. (Weights: 70% Delay + 30% Freight, derived from business heuristics regarding customer complaints).
Geospatial Analysis: Used grouping and aggregation to pinpoint the Top 5 "Logistics Black Holes" based on the newly calculated Pain Index.
Operations Research (Optimization): Formulated a resource allocation model using a Greedy Algorithm. Instead of subsidizing users randomly, the algorithm ranked at-risk customers by their historic spending (Life-Time Value) and systematically allocated the budget top-down.

4. Result (The Business Impact)
Simulated under a strict financial constraint of a 5,000 BRL budget (offering a 50 BRL targeted freight subsidy per user):
Retained Customers: Successfully targeted and retained 100 top-tier VIP customers in the highest-risk regions.
Revenue Protected: Secured over 153,000 BRL in historical top-line revenue that was at immediate risk of churn.
ROI: Achieved an outstanding ~3060% ROI, proving that data-driven, optimized resource allocation dramatically outperforms baseline marketing strategies.

Visualizations
<img width="1589" height="590" alt="Weixin Image_20260718160926_269_45" src="https://github.com/user-attachments/assets/ee01a6c9-57b6-49e2-8f1a-5dc47870cf14" />


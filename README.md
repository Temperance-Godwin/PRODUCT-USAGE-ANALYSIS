## INTRODUCTION
Imagine a banking institution with thousands of clients and millions in assets under management, yet still struggling to understand how its products are truly being used. While product offerings continue to expand—business lending, investment accounts, and foreign currency services, the institution lacks granular insight into who is using what, how frequently, and what drives usage.
As a Product Analyst within the organization, I led a comprehensive Product Usage Analysis to help the bank uncover patterns in client behavior, identify high-value clients, evaluate underutilized services, and guide product targeting across different customer segments.

## PROBLEM STATEMENTS
The bank has minimal visibility into:
1. The number of products used per client
2. Demographic or risk-based patterns in product usage
3. The value concentration across product types and client groups
4. Gaps between customer relationships and actual usage behavior

This lack of insight limits the institution’s ability to make data-driven decisions in product development, marketing, and relationship management.

## OBJECTIVE
The objective of this analysis is to:
1. Understand the distribution and intensity of product usage across the customer base
2. Identify high-value clients and segments underutilizing key products
3. Assess the risk-product relationship to guide risk-aware growth
4. Provide actionable recommendations for sales, marketing, and strategic planning

## DATA SOURCE
The dataset comprises four Excel sheets:
- banking_data: Contains client-level data including demographics, risk weighting, and usage across major product types (business lending, foreign currency account)
- Gender, Relationship, Investment Advisors: Lookup tables for relational joins

## DATA MODELLING
![Data Modelling](https://github.com/Temperance-Godwin/PRODUCT-USAGE-ANALYSIS/blob/main/Data%20Modelling.png)

## ANSWERING BUSINESS QUESTIONS
1. Top 10 High Value Clients
```sql
SELECT top 10
    Name,
   ROUND ((SUM(Business_Lending) + SUM(Foreign_Currency_Account)),2) AS Total_Value
FROM banking_data
GROUP BY Name
ORDER BY Total_Value DESC;
```

Data Visualization
Two dashboards were designed in Power BI:

1. Product Penetration Overview
KPIs: % clients using each product, average number of products per client

Slicers: Age, Gender, Relationship Type, Occupation

Charts: Heatmap, Pie (loyalty), Bar (product use by segment)

2. High-Value & Risk Insight Dashboard
KPIs: Total product value, avg. product usage by risk class

Slicers: Loyalty Tier, Risk Weighting, Investment Advisor

Charts: Treemap (product value by occupation), Scatter (risk vs value), Donut (top 10 clients)

Insights
Over 60% of clients use only one product, indicating significant cross-sell opportunity.

Retail clients use products more diversely than institutional clients.

Business Lending is highly concentrated in clients aged 30–50, mostly male.

Some clients with high risk weightings are also among the top value contributors, highlighting a need for closer monitoring.

Foreign currency accounts are underutilized by female clients, suggesting a possible gap in financial advisory.

Recommendations
Launch targeted cross-sell campaigns for clients with only one product.

Create risk-balanced tiered offers for high-value, high-risk clients.

Equip relationship managers with usage dashboards for real-time advisory.

Initiate a financial inclusion drive among underrepresented groups (e.g., female forex users).

Empower investment advisors with product-usage alerts to boost proactive outreach.

Which Way Forward for the Company
This analysis should inform a data-driven client engagement strategy, where every advisor, manager, and executive has visibility into product behavior. By embedding product usage insights into core decision-making, the company can:

Increase revenue through better client-product matching

Reduce churn by enhancing relevance and experience

Balance risk exposure while maintaining value focus

Going forward, I recommend the implementation of a Product Intelligence Hub, combining BI dashboards, predictive analytics, and client segmentation tools—paving the way for smarter banking and strategic growth.





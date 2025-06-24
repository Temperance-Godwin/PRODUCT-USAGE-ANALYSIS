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
1. Top 10 High Value Clients.
```sql
SELECT top 10
    Name,
   ROUND ((SUM(Business_Lending) + SUM(Foreign_Currency_Account)),2) AS Total_Value
FROM banking_data
GROUP BY Name
ORDER BY Total_Value DESC;
```
2. Which products are mostly used by customers?
```sql
SELECT 
    'Credit Cards' AS Product,
    COUNT(*) AS Users
FROM banking_data
WHERE Amount_of_Credit_Cards > 0
UNION ALL
SELECT 'Savings Accounts', COUNT(*) FROM banking_data WHERE Saving_Accounts > 0
UNION ALL
SELECT 'Checking Accounts', COUNT(*) FROM banking_data WHERE Checking_Accounts > 0
UNION ALL
SELECT 'Foreign Currency Account', COUNT(*) FROM banking_data WHERE Foreign_Currency_Account > 0
UNION ALL
SELECT 'Business Lending', COUNT(*) FROM banking_data WHERE Business_Lending > 0
UNION ALL
SELECT 'Bank Loans', COUNT(*) FROM banking_data WHERE Bank_Loans > 0
ORDER BY USERS DESC;
```

## PRODUCT ADOPTION REVIEW
![Product Adoption Review](https://github.com/Temperance-Godwin/PRODUCT-USAGE-ANALYSIS/blob/main/Production%20Adoption%20Review.png)


1. **Client Growth & Product Penetration:** The organization has a client base of **3,000,** with a Year-to-Date growth of **194 clients,** suggesting slow but steady acquisition. With 8,281 products across **3,000 clients,** the average product usage is approximately **3 products per client,** indicating moderate cross-sell effectiveness.
2. **Banking Relationship vs Product Value:** Private Banking clients contribute the highest product value at **$1.21bn,** making up nearly half of the total product value **($2.7bn).** Retail clients contribute significantly less **($0.59bn),** while Institutional and Commercial segments trail closely behind.
3. **Loyalty Tiers and Product Usage:** The Jade loyalty tier is the highest-performing in terms of product usage, contributing **$52M,** more than triple that of Platinum clients **($16M).** There is a clear positive correlation between loyalty tier level and product engagement/value.
4. **Monthly Product Usage Trends:** Product usage shows a cyclical pattern, with noticeable dips in March, June, and November, and strong peaks in **February, May, August, and December.** The second half of the year (July to December) demonstrates more consistent usage, implying stronger engagement or campaign effects in H2.

## INSIGHTS


## RECOMMENDATIONS


## STRATEGIC NEXT STEP
This analysis should inform a data-driven client engagement strategy, where every advisor, manager, and executive has visibility into product behavior. By embedding product usage insights into core decision-making, the company can:
1. Increase revenue through better client-product matching
2. Reduce churn by enhancing relevance and experience
3. Balance risk exposure while maintaining value focus

Going forward, I recommend the implementation of a Product Intelligence Hub, combining BI dashboards, predictive analytics, and client segmentation tools—paving the way for smarter banking and strategic growth.





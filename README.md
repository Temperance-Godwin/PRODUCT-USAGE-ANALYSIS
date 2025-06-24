## INTRODUCTION
Imagine a banking institution with thousands of clients and millions in assets under management, yet still struggling to understand how its products are truly being used. While product offerings continue to expand, the institution lacks granular insight into who is using what, how frequently, and what drives usage.

As a Product Analyst within the organization, I led a comprehensive Product Usage Analysis to help the bank uncover patterns in client behavior, identify high-value clients, evaluate underutilized services, and guide product targeting across different customer segments.

## PROBLEM STATEMENT
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

## DATA MODELLING
![Data Modelling](https://github.com/Temperance-Godwin/PRODUCT-USAGE-ANALYSIS/blob/main/Data%20Modelling.png)

## ANSWERING BUSINESS QUESTIONS
1. Product usage across customers
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
### Output

| Employee	 |Total_Customer |
| :--------      |-----------: 	
| Credit Cards   | 3000
| Foreign Currency Account | 3000
| Business Lending |2986
| Bank Loans | 2973
|Checking Accounts |2966
|Savings Accounts	 |2966


Credit Cards and Foreign Currency Accounts are used by 100% of clients, while Checking and Savings Accounts are the least used, with 2,966 users out of 3,000.

2. Product usage by income group
```sql
WITH Income_Classified AS (
    SELECT *,
        CASE 
            WHEN Estimated_Income < 50000 THEN 'Low Income'
            WHEN Estimated_Income BETWEEN 50000 AND 150000 THEN 'Middle Income'
            ELSE 'High Income'
        END AS Income_Group
    FROM banking_data
)
SELECT 
    Income_Group,
    ROUND(SUM(Amount_of_Credit_Cards), 2) AS Total_Credit_Cards,
    ROUND(SUM(Credit_Card_Balance), 2) AS Total_Card_Balance,
    ROUND(SUM(Bank_Loans), 2) AS Total_Loans,
    ROUND(SUM(Saving_Accounts),2) AS Total_Savings,
    ROUND(SUM(Business_Lending), 2) AS Total_Business_Lending
FROM Income_Classified
GROUP BY Income_Group;
```
Product usage increases significantly with income level. High-income clients show the highest values across credit cards, loans, savings, and business lending. Middle-income clients follow closely, while low-income clients contribute marginally across all products.

## PRODUCT ADOPTION OVERVIEW
![Product Adoption Review](https://github.com/Temperance-Godwin/PRODUCT-USAGE-ANALYSIS/blob/main/Production%20Adoption%20Review.png)


1. **Client Growth & Product Penetration:** The organization has a client base of **3,000,** with a Year-to-Date growth of **194 clients,** suggesting slow but steady acquisition. With **8,281 products** across **3,000 clients,** the average product usage is approximately **3 products per client,** indicating moderate cross-sell effectiveness.
2. **Banking Relationship vs Product Value:** Private Banking clients contribute the highest product value at **$1.21bn,** making up nearly half of the total product value **($2.7bn).** Retail clients contribute significantly less **($0.59bn),** while Institutional and Commercial segments trail closely behind.
3. **Loyalty Tiers and Product Usage:** The Jade loyalty tier is the highest-performing in terms of product usage, contributing **$52M,** more than triple that of Platinum clients **($16M).** There is a clear positive correlation between loyalty tier level and product engagement/value.
4. **Monthly Product Usage Trends:** Product usage shows a cyclical pattern, with noticeable dips in March, June, and November, and strong peaks in **February, May, August, and December.** The second half of the year (July to December) demonstrates more consistent usage, implying stronger engagement or campaign effects in H2.

## HIGH-VALUE CLIENTS & RISK SEGMENT
![High-Value Clients & Risk Segments](https://github.com/Temperance-Godwin/PRODUCT-USAGE-ANALYSIS/blob/main/High-Value%20Clients%20%24%20Risk%20Segments.png)

1. **Client Risk Distribution:** A large portion of clients fall into Low **(41%)** and Very Low **(28%)** risk categories, indicating a generally stable and low-risk portfolio. Only **5%** are classified as Very High risk, suggesting limited exposure to credit or default risks.
2. **High-Value Client Insights:** The top 5 clients each hold between **$4.0M–$5.0M** in product value, representing a concentrated pool of high-net-worth individuals. The Jade tier continues to show dominance, not just in product value but also in property ownership, holding **9 out of 15 properties.**
3. Occupation-Based Lending Value: Structural Analysis Engineers contribute the most to business lending at **$31.7M,** followed by Automation Specialists and Database Administrators. The presence of highly skilled technical professions suggests a client base with stable income and long-term lending potential.
4. Client Asset Ownership: Property ownership is highest among loyal clients in the Jade tier, reinforcing their profile as high-value, asset-rich customers. Silver, Gold, and Platinum clients show lower property ownership, which may reflect different wealth levels or engagement stages.

To interact with dashboard, [Click Here](https://app.powerbi.com/view?r=eyJrIjoiNWU2NzMwNDItMDdiMS00ZTUyLTg2OTUtNmE2ZmQ3NTZlOGZjIiwidCI6Ijg0ZGZiOGY5LWYzMTItNDk1NC05ZTk5LWYzZjcxMTgzZDZmMSJ9)

## RECOMMENDATION
1. Double Down on High-Value Loyalty Tiers (Especially Jade)
Prioritize the Jade tier for elite services and tailored experiences. Build a premium offering exclusively for Jade clients (e.g., concierge banking, early access to investment products, loyalty-linked mortgage discounts).
This impact will boost client retention, increase lifetime value, and turn high-value clients into brand advocates with deeper product engagement.

3. Unlock Product Growth Through Occupation-Based Personalization
Segment product usage strategies by occupation. Tailor financial solutions to the specific needs of high-value professions (e.g., customized lending plans, bundled investment tools. This will increase product adoption through relevant offerings, expands penetration in high-yield professions, and enables smarter targeting.

3. Expand Adoption During Low Engagement Months
Product usage dips noticeably in March, June, and November. Design and execute seasonal product usage campaigns focused on these periods. Tactics can include limited-time offers, reward incentives, and targeted education campaigns. This will reduce inactivity during lull periods, improves monthly usage consistency, and increases year-round product engagement.

4. Maximize Monetization of Low-Risk Clients
Introduce a low-risk growth portfolio with bundled savings, investment, and advisory products tailored to conservative yet valuable clients. This will drive revenue from a stable, low-risk group while encouraging gradual adoption of more complex products.

5. Leverage Property Ownership to Trigger Cross-Selling
Use property ownership as a trigger for upselling financial products such as home equity loans, wealth planning, or premium insurance. This action enables contextual cross-selling, increases product per client ratio, and deepens financial relationships through wealth-linked offerings.

## STRATEGIC NEXT STEP FOR THE ORGANIZATION
The organization should establish a Product Usage Optimization Program (PUOP). A cross-functional initiative focused on driving deeper product adoption, increasing average products per client, and expanding value across client segments.

This program should implement:
1. Loyalty Tier Experience Mapping
2. Occupation-Based Product Personalization
3. Seasonal Product Engagement Campaigns
4. Risk-Smart Client Monetization Framework
5. Property-Triggered Product Bundling

This initiative should be led at the executive level with KPIs around:
- Product adoption growth
- Monthly usage stability
- Client-level product penetration
- Cross-sell conversion rates




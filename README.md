# Supply Chain Service Level Tracking Analysis
___

## Executive Summary:
I analysed supply chain service level data and found that On-Time and In-Full service levels were consistently less than targets with at least 23% difference over a period of six months. "Delivered" quantity fall short of "Orders" by 400,000. Three customers out of the top 5 having over one million order quantity representing ___% of total order quantity were conspicuously underserved with On_Time delivery as down to 28%. Other customers had less than 800,000 order quantity.

Base on these findings, I recommend targeted product manufacturing schedules and real-time inventory tracking to boost operational efficiency.

## Business Problem:
For supply chain–driven organisations, service level performance directly affects customer satisfaction, retention, and contractual compliance. In this organisation, management observed recurring complaints from customers and inconsistent service level outcomes but lacked clear visibility into where and why performance was falling short. The objective was to analyse supply chain service level data by tracking On-Time (OT), In-Full (IF), and On-Time-In-Full (OTIF) deliveries against agreed targets, alongside Line Fill Rate and Volume Fill Rate across multiple customers.

This analysis aimed to identify key gaps in service performance, highlight customers or order types most impacted, and provide actionable insights to improve delivery reliability and overall service levels.

## Methodology:

**PostgreSQL:**

1. Created database, "SupplyChain_DB" alongside five tables (dim_customers, dim_date, dim_products, dim_targets_orders, fact_order_lines) using PostgreSQL.
2. Imported CSV files and populated all five tables.
3. Converted the three date columns to text in the "fact_order_lines" table.
4. Calculated the difference between the agreed and actual delivery dates in two different columns - one involving postive, zero negative values......
5. Added three binary features (on-time, in-full, on-time-in-full) to "fact_order_lines". On-time records 1 for all timely deliveries but 0 for delayed deliveries. In-full records 1 for deliveries made in full and 0 for incomplete delivery per order. On-time-in-full records 0 for a delivery that is both on time and in full but records 0 when any of the two (on-time, in-full) is 0.
6. Created a VIEW from the cleaned "fact_order_lines" table and saved as "fact_order_lines_view".
7. Furthermore, another VIEW, "fact_orders_aggregate_view" was created from "fact_order_lines_view" to aggregate orders base on "order_id" and "customer_id" with the "order_placement_date" as an aedded feature to relate to the date (calendar) table. This view groups many order lines into a single entity. If one of the order lines is not fulfilled, the result is 0, while 1 means all line items are delivered. On-time is 1 only when all line items are delivered on time, otherwise, 0. In-full is 1 only when all line items are delivered in full, otherwise, 0. On-time-in-full is 1 only when both on-time and in-full are 1 each, otherwise, 0.
8. Four TABLES and two VIEWS were imported into Power BI for visualisation.

**Power Query:**

9. Coolblue to Cool Blue in the dim_customers table to be consistent with other customers names.
10. Added month number, month name and week number to the dim_date table.
11. "beverages" to "Beverages" in the dim_products table.

**Power BI:**

12. DAX: list key metrics
13. Visuals: list with simple descriptions.

## Skills:
- SQL: schema design, data transformation & modelling, data querying, PostgreSQL
- Power Query: data transformation
- Power BI: DAX measures, data visualization

## Insights & Recommendation:
1. Over the past six months, the company consistently failed to meet Service Level Agreement (SLA) targets, recording an average **delivery delay of +0.5 days per order** and an average **order-line shortfall of 8 units per order line**, indicating persistent lead-time variability and significant gaps in inventory availability and order fill rate.
> Improve demand forecasting and inventory planning by **adjusting safety stock levels for high-volume SKUs** based on recent demand trends.

2. Lotus Mart, Acclaimed Stores, and Cool Blue recorded the highest delivery delays, with an average lead-time variance of approximately **+1.5 days**. Notably, **two of these customers rank among the top five by order volume**, each exceeding **one million units ordered**, amplifying the operational and service impact of these delays.
> - Prioritise high-volume customers for targeted service recovery by reviewing allocation, fulfilment, and last-mile delivery processes.
> - Implement account-level SLA monitoring to track performance for each key customer and quickly address delays or shortages.

3. On-Time (OT) and In-Full (IF) delivery rates have remained consistently low at approximately **59%** and **52%** respectively over the past six months, with minimal variation. This indicates a structurally constrained operating performance rather than a temporary disruption.
> - Reassess operational capacity across warehousing and last-mile delivery, including **staffing levels**, by adding temporary or permanent staff in critical areas such as picking, packing, and dispatch, to reduce delays.
> - Set phased OTIF improvement targets and monitor performance to ensure capacity adjustments translate into measurable service-level gains.
  
4. The **Dairy product category**, excluding AM Ghee, recorded the **top 9 orders** by volume and **highest delivery shortfall**, averaging **10–14 units per order line**, well above the overall average of **8**. Notably, dairy products are also the **highest-volume category**, with over **10.56 million units ordered**, accounting for **___% of total order quantity**, thereby magnifying the operational impact of these shortages.
> **Increase inventory coverage for high-volume dairy products** by reviewing replenishment frequency and minimum stock thresholds.

5. Although a significant share of orders were delivered early or on time, **over 13,000 (40%) of total orders were delivered late**, highlighting persistent delivery reliability issues and a high risk of SLA breaches.
___

### `Additional Materials`

#### `Supply Chain Service Level Tracking Report:`

#### `Model View:`

#### 


[Data set](https://codebasics.io/challenges/codebasics-resume-project-challenge/5)

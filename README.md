# Supply Chain Service Level Tracking Analysis
___

## Executive Summary:
I analysed supply chain service level data and found that On-Time and In-Full service levels were consistently less than targets with at least 23% difference over a period of six months. "Delivered" quantity fall short of "Orders" by 400,000. Three customers out of the top 5 having over one million order quantity representing ___% of total order quantity were conspicuously underserved with On_Time delivery as down to 28%. Other customers had less than 800,000 order quantity.

Base on these findings, I recommend targeted product manufacturing schedules and real-time inventory tracking to boost operational efficiency.

## Business Problem:
For supply chain–driven organisations, service level performance directly affects customer satisfaction, retention, and contractual compliance. In this organisation, management observed recurring complaints from customers and inconsistent service level outcomes but lacked clear visibility into where and why performance was falling short. The objective was to analyse supply chain service level data by tracking On-Time (OT), In-Full (IF), and On-Time-In-Full (OTIF) deliveries against agreed targets, alongside Line Fill Rate and Volume Fill Rate across multiple customers.

This analysis aimed to identify key gaps in service performance, highlight customers or order types most impacted, and provide actionable insights to improve delivery reliability and overall service levels.

## Methodology:
1. Created database, "SupplyChain_DB" alongside five tables (dim_customers, dim_date, dim_products, dim_targets_orders, fact_order_lines) using PostgreSQL.
2. Imported CSV files and populated all five tables.
3. Converted the three date columns to text in the "fact_order_lines" table.
4. Added three binary features (on-time, in-full, on-time-in-full) to "fact_order_lines". On-time records 1 for all timely deliveries but 0 for delayed deliveries. In-full records 1 for deliveries made in full and 0 for incomplete delivery per order. On-time-in-full records 0 for a delivery that is both on time and in full but records 0 when any of the two (on-time, in-full) is 0.
5. Created a VIEW from the cleaned "fact_order_lines" table and saved as "fact_order_lines_view".
6. Furthermore, another VIEW, "fact_orders_aggregate_view" was created from "fact_order_lines_view" to aggregate orders base on "order_id" and "customer_id" with the "order_placement_date" as an aedded feature to relate to the date (calendar) table. This view groups many order lines into a single entity. If one of the order lines is not fulfilled, the result is 0, while 1 means all line items are delivered. On-time is 1 only when all line items are delivered on time, otherwise, 0. In-full is 1 only when all line items are delivered in full, otherwise, 0. On-time-in-full is 1 only when both on-time and in-full are 1 each, otherwise, 0.
7. Four TABLES and two VIEWS were imported into Power BI for visualisation.

## Skills:
- SQL: schema design, data transformation & modelling, data querying, PostgreSQL
- Power BI: DAX measures, data visualization

## Insights & Recommendation:
### 1. The company failed to meet all service level targets....  context

### 2. "Lotus Mart" and "Acclaimed Stores" experienced the worst delays in delivery even though they are among the top five customers by "Order Quantity", while "Vijay Stores" with the highest Order Quatity suffered the worst shortage amongst the top five orders.

### 3. On-Time rates consistently remain around 59% without major fluctuations over six months. This suggest that is the actual performance of the company at best and for improvements in timely deliveries, the company might need to hire additional staff. In-Full and OTIF likewise, agree with this assumption.  
  
### 4. Dairy product category contributes the highest to shortage in delivery. CONFIRM IF a particular product or category cause more delivery delays....

### 5. 

___

### `Additional Materials`

#### `Supply Chain Service Level Tracking Report:`

#### `Model View:`

#### 


[Data set](https://codebasics.io/challenges/codebasics-resume-project-challenge/5)

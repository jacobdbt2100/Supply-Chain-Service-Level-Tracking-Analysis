# Supply Chain Service Level Tracking Analysis
___

## Executive Summary:
I analysed supply chain service level data and found that On-Time and In-Full service levels were consistently less than targets with at least 23% difference over a period of six months. "Delivered" quantity fall short of "Orders" by 400,000. Three customers out of the top 5 having over one million order quantity representing ___% of total order quantity were conspicuously underserved with On_Time delivery as down to 28%. Other customers had less than 800,000 order quantity.

Base on these findings, I recommend targeted product manufacturing schedules and real-time inventory tracking to boost operational efficiency.

## Business Problem:
For supply chain–driven organisations, service level performance directly affects customer satisfaction, retention, and contractual compliance. In this organisation, management observed recurring complaints from customers and inconsistent service level outcomes but lacked clear visibility into where and why performance was falling short. The objective was to analyse supply chain service level data by tracking On-Time (OT), In-Full (IF), and On-Time-In-Full (OTIF) deliveries against agreed targets, alongside Line Fill Rate and Volume Fill Rate across multiple customers.

This analysis aims to identify key gaps in service performance, highlight customers or order types most impacted, and provide actionable insights to improve delivery reliability and overall service levels.

## Methodology:
1. Created database, "SupplyChain_DB" alongside five tables (dim_customers, dim_date, dim_products, dim_targets_orders, fact_order_lines) in PostgreSQL.
2. Imported CSV files and populated all five tables.
3. Cleaned the three date columns in the "fact_order_lines" table by converting from text to proper text formats.
4. Added three binary features (on-time, in-full, on-time-in-full) to "fact_order_lines". On-time records 1 for all timely deliveries but 0 for delayed deliveries. In-full records 1 for deliveries made in full and 0 for incomplete delivery per order. On-time-in-full records 0 for a delivery that is both on time and in full but records 0 when any of the two (on-time, in-full) is 0.
5. Created a VIEW from the cleaned "fact_order_lines" table and saved as "fact_order_lines_view".
6. Furthermore, 

## Skills:
- 

## Insights & Recommendation:
### 1. 

### 2. 

### 3. 
  
### 4. 

### 5. 

___

### `Additional Notes`

#### `Supply Chain Service Level Tracking Report:`

#### `Model View:`

#### 


[Data set](https://mavenanalytics.io/data-playground/manufacturing-downtime)

# Shield Insurance – Dataset Overview

## 1. Introduction

The Shield Insurance Power BI project uses structured insurance data to examine business performance across customer demographics, policy information, premium records and settlement percentages.

This document describes the organization of the analytical model, identified fields and the reporting purpose of each table.

**Data confidentiality:** The original source dataset is not included in this repository because public redistribution is not permitted.

## 2. Dataset Architecture

The Power BI model contains six tables.

| Table | Classification | Analytical Purpose |
|---|---|---|
| `dim_customer` | Dimension | Customer attributes and demographic segmentation |
| `dim_date` | Dimension | Calendar context and time-based reporting |
| `dim_policies` | Dimension | Policy attributes and preference analysis |
| `fact_premiums` | Fact | Premium, revenue and sales-mode analysis |
| `fact_settlements` | Fact | Expected settlement analysis |
| `CALCULATED_MEASURES` | Measures table | Organization of DAX calculations |

## 3. Table-Level Documentation

### 3.1 Customer Dimension – `dim_customer`

This table supports customer-level analysis and demographic segmentation.

Age groups used in the dashboard:

- 18–24
- 25–30
- 31–40
- 41–50
- 51–65
- 65+

**Reporting applications:**
- Customer distribution by age group.
- Revenue contribution by age segment.
- Sales-mode distribution across customer segments.
- Policy preference analysis.

### 3.2 Date Dimension – `dim_date`

The date dimension provides calendar context for time-based reporting.

The project uses the `mmm_yy` month label with a numeric year-month sorting field to maintain chronological ordering.

**Reporting applications:**
- Monthly revenue analysis.
- Customer and policy trend comparisons.
- Month-over-month performance reporting.

### 3.3 Policy Dimension – `dim_policies`

This table supports policy-related analysis within the reporting model.

**Reporting applications:**
- Policy preference comparisons.
- Policy distribution across customer age segments.

The complete column inventory is not listed because every field has not been independently verified.

### 3.4 Premium Fact Table – `fact_premiums`

The premium fact table supports premium and sales-related reporting.

**Identified fields:**

| Field | Description |
|---|---|
| `policy_id` | Policy identifier |
| `sales_mode` | Sales channel or mode |
| `customer_code` | Customer identifier |
| `date` | Date associated with the premium record |

**Reporting applications:**
- Premium and revenue analysis.
- Sales-mode performance comparisons.
- Customer-related analysis.
- Date-based performance trends.

### 3.5 Settlement Fact Table – `fact_settlements`

This table supports expected settlement analysis across age values.

**Identified fields:**

| Field | Description |
|---|---|
| `age` | Age value used for settlement segmentation |
| `settlement %` | Settlement percentage |

**Reporting applications:**
- Expected settlement percentage comparison.
- Age-based settlement analysis.

**Important limitation:** A date or month field has not been identified in this table. Therefore, monthly settlement trends and month-over-month settlement calculations cannot be derived from this table.

### 3.6 Measures Table – `CALCULATED_MEASURES`

This table provides a dedicated location for organizing DAX measures.

Identified measures include:

- `TOTAL_CUSTOMERS`
- `TOTAL_POLICIES`
- `FINAL_PREMIUM_AMOUNT`
- `TOTAL_REVENUE`
- `DAILY_REVENUE_GROWTH`
- `DAILY_CUSTOMER_GROWTH`
- `POLICY_MOM_GROWTH`
- `CUSTOMERS_MOM_GROWTH`
- `REVENUE_MOM_GROWTH`
- `EXPECTED_SETTLEMENT`

These measures support KPI reporting, business comparisons and settlement analysis.

## 4. Data Preparation and Modelling

The project uses Power Query and Power BI modelling capabilities to prepare the data for analytical reporting.

The implementation includes:

- Preparing source tables using Power Query.
- Organizing fact and dimension tables.
- Establishing the date context for chronological reporting.
- Applying a numeric year-month sorting field.
- Developing DAX measures for KPIs and period comparisons.

## 5. Analytical Coverage

| Analysis | Relevant Tables |
|---|---|
| Customer demographics | `dim_customer` |
| Monthly performance | `dim_date`, `fact_premiums` |
| Policy preferences | `dim_policies` |
| Premium and revenue | `fact_premiums` |
| Sales-mode performance | `fact_premiums` |
| Expected settlement | `fact_settlements` |
| KPI calculations | `CALCULATED_MEASURES` |

## 6. Data Availability and Confidentiality

The original source dataset is intentionally excluded from this public repository because redistribution is not permitted.

This document provides the known structure and analytical purpose of the model without reproducing restricted source records or customer-level information.

## 7. Project Resources

- **GitHub Repository:** https://github.com/Sub02/Shield-Insurance-BI-Analytics
- **Live Power BI Dashboard:** https://app.powerbi.com/view?r=eyJrIjoiYjAzNGViZTctMDVlNS00NWZjLWI0ODUtYTQ1MTBlNGQ4OTA4IiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9
- **YouTube Walkthrough:** https://youtu.be/KuFA-KzAISQ

## Author

**Subhayan Kundu**

- LinkedIn: https://www.linkedin.com/in/subhayan-kundu/
- Portfolio: https://codebasics.io/portfolio/SUBHAYAN-KUNDU/

---

*This document describes the identified project model structure. Refer to the Power BI model for the complete schema and calculation definitions.*

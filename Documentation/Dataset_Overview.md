# Shield Insurance – Dataset Overview & Data Architecture

## 1. Introduction

The Shield Insurance project uses structured insurance data to develop an interactive business intelligence solution in Microsoft Power BI.

The analytical model brings together customer, policy, date, premium and settlement information to support business performance monitoring and customer-segment analysis.

This document provides a technical overview of the dataset organization, table classification, identified fields and their analytical applications within the Power BI report.

**Data Confidentiality Notice:** The original source dataset is not included in this repository because permission for public redistribution has not been granted. This documentation describes the data model without exposing restricted source records or customer-level information.

---

## 2. Data Model Architecture – Star Schema

The Shield Insurance Power BI solution follows a **Star Schema data modelling approach**.

The model separates measurable business information into fact tables and descriptive attributes into dimension tables. This organization provides a structured analytical foundation for examining insurance performance across different business dimensions.

### 2.1 Fact Tables

The model contains two fact tables:

| Table Name | Analytical Purpose |
|---|---|
| `fact_premiums` | Premium-related analysis, revenue reporting and sales-mode performance |
| `fact_settlements` | Expected settlement percentage analysis across age values |

### 2.2 Dimension Tables

The model contains three dimension tables:

| Table Name | Analytical Purpose |
|---|---|
| `dim_customer` | Customer attributes and demographic segmentation |
| `dim_date` | Calendar attributes and time-based analysis |
| `dim_policies` | Policy attributes and policy preference analysis |

### 2.3 Supporting Calculation Table

| Table Name | Purpose |
|---|---|
| `CALCULATED_MEASURES` | Dedicated organization of DAX measures used in the report |

The fact and dimension tables form the analytical data model. The supporting measures table provides a centralized location for organizing report calculations.

---

## 3. Detailed Table-Level Documentation

### 3.1 Customer Dimension – `dim_customer`

The customer dimension provides descriptive customer information for demographic analysis and segmentation.

The report uses the following age categories:

| Age Group |
|---|
| 18–24 |
| 25–30 |
| 31–40 |
| 41–50 |
| 51–65 |
| 65+ |

**Analytical Applications:**

- Customer distribution across age groups.
- Revenue contribution by age segment.
- Sales-mode distribution across demographic categories.
- Policy preference comparisons across age groups.

### 3.2 Date Dimension – `dim_date`

The date dimension provides the calendar context required for time-based analysis.

A month label, `mmm_yy`, is used for monthly reporting. A numeric year-month sorting field is applied to maintain chronological ordering in Power BI visuals.

**Analytical Applications:**

- Monthly revenue trend analysis.
- Customer and policy performance monitoring.
- Month-over-month business comparisons.
- Chronological reporting across reporting periods.

### 3.3 Policy Dimension – `dim_policies`

The policy dimension provides policy-related descriptive information used in the dashboard.

**Analytical Applications:**

- Policy preference analysis.
- Policy distribution across customer age segments.
- Comparison of policy-related business categories.

The complete column inventory is not listed here because the exact field-level schema has not been independently verified.

### 3.4 Premium Fact Table – `fact_premiums`

The premium fact table supports premium-related reporting and sales-channel analysis.

**Identified Fields:**

| Field Name | Description |
|---|---|
| `policy_id` | Identifier associated with a policy |
| `sales_mode` | Sales channel or mode associated with the record |
| `customer_code` | Identifier associated with a customer |
| `date` | Date associated with the premium record |

**Analytical Applications:**

- Premium and revenue analysis.
- Sales-mode performance comparisons.
- Customer-related premium analysis.
- Date-based performance trends.
- Monthly business reporting.

### 3.5 Settlement Fact Table – `fact_settlements`

The settlement fact table supports expected settlement analysis using age and settlement percentage information.

**Identified Fields:**

| Field Name | Description |
|---|---|
| `age` | Age value used for settlement segmentation |
| `settlement %` | Settlement percentage used in the analysis |

**Analytical Applications:**

- Expected settlement percentage analysis.
- Comparison of settlement percentages across age values.
- Age-based settlement segmentation.

**Important Data Limitation:**

The available settlement table does not contain a date or month field. Consequently, a true monthly settlement trend or month-over-month settlement calculation cannot be derived directly from this table.

### 3.6 Supporting Measures Table – `CALCULATED_MEASURES`

The `CALCULATED_MEASURES` table provides a dedicated location for organizing the DAX calculations used throughout the report.

**Identified Measures:**

| Measure Name | Analytical Purpose |
|---|---|
| `TOTAL_CUSTOMERS` | Customer count |
| `TOTAL_POLICIES` | Policy count |
| `FINAL_PREMIUM_AMOUNT` | Final premium amount |
| `TOTAL_REVENUE` | Revenue calculation |
| `DAILY_REVENUE_GROWTH` | Daily revenue growth analysis |
| `DAILY_CUSTOMER_GROWTH` | Daily customer growth analysis |
| `POLICY_MOM_GROWTH` | Month-over-month policy growth |
| `CUSTOMERS_MOM_GROWTH` | Month-over-month customer growth |
| `REVENUE_MOM_GROWTH` | Month-over-month revenue growth |
| `EXPECTED_SETTLEMENT` | Expected settlement analysis |

These measures support KPI reporting, business comparisons and the analytical calculations displayed in the dashboard.

---

## 4. Data Preparation & Transformation

Power Query is used within Microsoft Power BI to prepare and shape the source tables for analytical reporting.

The project preparation workflow includes:

- Preparing the available source tables for reporting.
- Organizing customer, date and policy dimensions.
- Structuring premium and settlement fact tables.
- Preparing calendar attributes for time-based analysis.
- Applying chronological sorting to monthly labels.
- Supporting the analytical model with DAX-based calculations.

The prepared tables are used by the Star Schema model to support the dashboard's business reporting requirements.

---

## 5. Star Schema – Analytical Organization

The data model separates the business data into two primary categories:

**Fact Tables**

- `fact_premiums`
- `fact_settlements`

These tables provide the information used in premium, revenue, sales-mode and settlement analysis.

**Dimension Tables**

- `dim_customer`
- `dim_date`
- `dim_policies`

These tables provide descriptive analytical context for examining business information across customer, time and policy perspectives.

**Supporting Calculation Table**

- `CALCULATED_MEASURES`

This table organizes the DAX measures used by the reporting layer.

The actual relationship configuration and cardinalities should be inspected in the Power BI Model View.

---

## 6. Analytical Coverage & Table Mapping

The following mapping summarizes how the model supports the dashboard's analytical areas.

| Analytical Area | Relevant Tables |
|---|---|
| Customer segmentation | `dim_customer` |
| Monthly business trends | `dim_date`, `fact_premiums` |
| Policy preference analysis | `dim_policies`, `dim_customer` |
| Premium and revenue analysis | `fact_premiums` |
| Sales-mode performance | `fact_premiums` |
| Expected settlement analysis | `fact_settlements` |
| KPI and growth calculations | `CALCULATED_MEASURES` |

This mapping describes the tables' analytical applications and is not a substitute for the actual model relationship diagram.

---

## 7. Data Availability & Confidentiality

The original source dataset is intentionally excluded from this public GitHub repository.

This restriction is maintained to respect the applicable source-data distribution permissions.

Instead, the repository provides technical documentation covering:

- Star Schema model organization.
- Fact and dimension table classification.
- Identified source fields.
- Analytical applications of individual tables.
- DAX measure names.
- Known data and reporting limitations.

No restricted source records or reconstructed customer-level data are included.

---

## 8. Project Resources

| Resource | Link |
|---|---|
| GitHub Repository | [Shield Insurance – Power BI Analytics](https://github.com/Sub02/Shield-Insurance-BI-Analytics) |
| Live Power BI Dashboard | [Explore Interactive Report](https://app.powerbi.com/view?r=eyJrIjoiYjAzNGViZTctMDVlNS00NWZjLWI0ODUtYTQ1MTBlNGQ4OTA4IiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9) |
| Project Walkthrough | [Watch on YouTube](https://youtu.be/KuFA-KzAISQ) |

---

## Author

**Subhayan Kundu**

Aspiring Data Analyst | Business Intelligence | Data Analytics

**Technical Skills:** Power BI | SQL | Advanced Excel | Python | Data Modelling

- **LinkedIn:** [Subhayan Kundu](https://www.linkedin.com/in/subhayan-kundu/)
- **Portfolio:** [Codebasics Portfolio](https://codebasics.io/portfolio/SUBHAYAN-KUNDU/)
- **GitHub:** [Sub02](https://github.com/Sub02)

---

*This document describes the identified data model structure and its analytical applications. The Power BI model remains the authoritative source for the complete schema, relationships and calculation definitions.*

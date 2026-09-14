# Walmart Customer & Sales Analytics Dashboard

## Power BI | DAX | Customer Analytics | Churn & Retention

An interactive **Walmart Customer & Sales Analytics Dashboard** developed using **Microsoft Power BI and DAX** to analyze customer behavior, churn, retention, purchasing patterns, promotional activity, loyalty programs, store performance, and Customer Lifetime Value (CLV).

The project transforms customer, transaction, loyalty, churn, and store data into an interactive analytical dashboard that can support business decision-making.

---

## Project Objective

The main objective of this project is to understand:

* Customer churn and retention
* Repeat purchasing behavior
* Customer segmentation based on purchase frequency
* Loyalty-tier performance
* Promotional transaction behavior
* Store and channel performance
* Product-category transaction patterns
* Customer Lifetime Value (CLV)
* Relationship between customer behavior and churn

---

## Tools & Technologies

* **Power BI Desktop**
* **DAX**
* **Power Query**
* **Data Modeling**
* **Data Visualization**
* **Customer Analytics**
* **Business Intelligence**

---

## Data Model

The project uses multiple related datasets/tables:

* `Customer_Demographics`
* `Customer_Transactions`
* `Loyalty_Program`
* `Churn_Labelled_Customers`
* `Store_Locations`

### Relationships

The Power BI data model contains:

```text
Customer_Demographics
        │
        ├──────────────► Customer_Transactions
        │
        ├──────────────► Loyalty_Program
        │
        └──────────────► Churn_Labelled_Customers

Customer_Transactions
        │
        └──────────────► Store_Locations
```

Relationships were established to enable cross-table analysis of customer behavior, transactions, loyalty, churn, and store performance.

---

# Key KPIs

| KPI                        |      Result |
| -------------------------- | ----------: |
| Total Customers            |     **300** |
| Churned Customers          |     **149** |
| Active Customers           |     **151** |
| Churn Rate                 |   **49.7%** |
| Repeat Customers           |     **251** |
| Average CLV                | **₹484.69** |
| Average Transaction Amount | **₹516.26** |
| Promo Transactions         |     **490** |
| Promo Transaction Rate     |  **49.00%** |
| Total Points Redeemed      |    **624K** |

---

# Dashboard Analysis

## 1. Customer Churn & Retention

The dashboard analyzes churn across multiple customer dimensions.

### Churn Rate by Region

| Region  | Churn Rate |
| ------- | ---------: |
| West    |  **58.3%** |
| Central |  **49.2%** |
| North   |  **43.1%** |
| East    |  **40.8%** |
| South   |  **40.0%** |

The **West region has the highest observed churn rate**, while the South has the lowest among the displayed regions.

### Churn by Loyalty Tier

Churn was analyzed across:

* Elite
* Plus
* Premium
* Basic

This helps identify whether customer loyalty level is associated with retention behavior.

### Churn by Other Dimensions

The dashboard also analyzes churn by:

* Income level
* Preferred channel
* Store type
* Opening year

---

# 2. Customer Segmentation

Customers were segmented according to their purchase frequency.

### Segmentation Logic

```text
0–3 purchases   → Low
4–8 purchases   → Mid
9+ purchases    → High
```

### Customer Distribution

| Segment | Customers |
| ------- | --------: |
| Low     |   **175** |
| Mid     |   **123** |
| High    |     **2** |

This segmentation helps identify customers with low purchasing frequency and potential opportunities for retention and engagement campaigns.

---

# 3. Purchase Behavior Analysis

The dashboard analyzes average purchases per customer across:

* Region
* Age group
* Loyalty tier

It also analyzes transaction volume across product categories.

### Transactions by Product Category

| Product Category | Transactions |
| ---------------- | -----------: |
| Groceries        |      **269** |
| Apparel          |      **251** |
| Electronics      |      **249** |
| Home & Living    |      **231** |

**Groceries recorded the highest number of transactions** among the displayed categories.

---

# 4. Promotion & Loyalty Analysis

The project analyzes customer transactions involving promotions.

### Promotional KPIs

* Promo Transactions: **490**
* Promotional Transaction Rate: **49.00%**
* Average purchase amount with promotion
* Average purchase amount without promotion

The dashboard also compares:

* Points earned
* Points redeemed
* Loyalty tier
* Promotion application

This provides insight into customer participation in promotional and loyalty programs.

---

# 5. Store & Channel Performance

The dashboard evaluates transaction performance by store type.

### Average Transaction Amount

| Store Type          | Avg. Transaction |
| ------------------- | ---------------: |
| Sam's Club          |         **₹534** |
| Neighborhood Market |         **₹531** |
| Online              |         **₹513** |
| Supercenter         |         **₹488** |

### Total Transactions by Store Type

| Store Type          | Transactions |
| ------------------- | -----------: |
| Online              |      **290** |
| Sam's Club          |      **289** |
| Supercenter         |      **247** |
| Neighborhood Market |      **174** |

The analysis also compares average transaction amount between **Store and Online preferred channels**.

---

# 6. Customer Lifetime Value (CLV)

Customer Lifetime Value was analyzed to understand the economic value of customers.

The dashboard evaluates:

* CLV segment
* Days since last purchase
* Total amount spent
* Average CLV
* Loyalty tier
* Region
* Churned customers

### CLV Calculation

The project calculates membership duration and total customer spending to derive CLV.

```text
CLV = Total Amount Spent / Membership Duration Years
```

The resulting overall **Average CLV is ₹484.69**.

---

# DAX Analysis

Several DAX functions and measures were used to create the analytical layer of the dashboard.

### Customer Metrics

```DAX
Total Customers =
DISTINCTCOUNT(Customer_Demographics[Customer_ID])
```

```DAX
Churned Customers =
CALCULATE(
    DISTINCTCOUNT(Customer_Demographics[Customer_ID]),
    Churn_Labelled_Customers[Churn_Flag] = 1
)
```

```DAX
Churn Rate =
DIVIDE(
    [Churned Customers],
    [Total Customers]
)
```

### Customer Segmentation

```DAX
Customer Segment =
SWITCH(
    TRUE(),
    [Purchase Count] <= 3, "Low (0–3)",
    [Purchase Count] <= 8, "Mid (4–8)",
    "High (9+)"
)
```

### Promotional Analysis

```DAX
% Promo Transactions =
DIVIDE(
    [Promo Transactions],
    [Total Transactions]
)
```

### CLV Analysis

```DAX
Membership Duration Years =
DATEDIFF(
    Membership_Since,
    TODAY(),
    DAY
) / 365
```

```DAX
Total Amount Spent =
SUM(Customer_Transactions[Amount])
```

```DAX
CLV =
DIVIDE(
    [Total Amount Spent],
    [Membership Duration Years]
)
```

### Repeat Rate

```DAX
Repeat Rate =
DIVIDE(
    [Repeat Customers],
    [Total Customers]
)
```

---

# DAX Functions Used

The project demonstrates practical use of:

```text
DATEDIFF()
TODAY()
YEAR()
FORMAT()
DISTINCTCOUNT()
CALCULATE()
DIVIDE()
FILTER()
COUNT()
SWITCH()
TRUE()
AVERAGE()
SUM()
```

These functions were used for date calculations, customer metrics, segmentation, aggregation, filtering, ratios, churn analysis, loyalty analysis, and CLV calculations.

---

# Power BI Visualizations

The dashboard contains visual analysis including:

* KPI cards
* Churn rate by region
* Churn rate by loyalty tier
* Churn rate by income level
* Churn rate by preferred channel
* Churn rate by store type
* Churn rate by opening year
* Customer segmentation
* Average purchases by region
* Average purchases by age group
* Average purchases by loyalty tier
* Product-category transaction analysis
* Promotion analysis
* Loyalty points analysis
* Store performance
* Channel performance
* CLV segmentation
* CLV by loyalty tier
* CLV by region
* Funnel analysis for customer stages

---

# Key Business Insights

Based on the dashboard analysis:

### 1. High churn requires attention

The overall churn rate is **49.7%**, meaning almost half of the analyzed customer base is classified as churned.

### 2. West region shows the highest churn

The West region records **58.3% churn**, making it the highest among the displayed regions.

### 3. Most customers fall into low-frequency segments

There are **175 Low-frequency customers**, compared with 123 Mid-frequency and only 2 High-frequency customers.

This indicates an opportunity to increase repeat purchases.

### 4. Groceries lead transaction volume

Groceries have **269 transactions**, the highest among the analyzed product categories.

### 5. Sam's Club has the highest average transaction value

Sam's Club records an average transaction value of approximately **₹534**.

### 6. Online has the highest transaction volume

Online transactions total **290**, slightly higher than Sam's Club at 289.

### 7. Loyalty and retention can be analyzed together

The dashboard provides churn and CLV analysis by loyalty tier, allowing customer value and retention behavior to be evaluated together.

---

# Project Structure

```text
Walmart-Sales-Analysis-PowerBI/
│
├── README.md
│
├── PowerBI/
│   └── Walmart_Analysis.pbix
│
├── Documentation/
│   └── DAX-Functions.docx
│
├── Report/
│   └── Walmart_Analysis.pdf
│
└── Screenshots/
    ├── dashboard-overview.png
    ├── churn-analysis.png
    ├── promotion-loyalty-analysis.png
    ├── store-channel-analysis.png
    └── customer-clv-analysis.png
```

---

# How to Use

1. Download or clone this repository.
2. Install **Power BI Desktop**.
3. Open:

```text
PowerBI/Walmart_Analysis.pbix
```

4. Explore the interactive dashboard.
5. Use the available filters/slicers to analyze customer, region, loyalty, store, and CLV metrics.

> Note: Power BI Desktop is required to open and interact with the `.pbix` file.

---

# Skills Demonstrated

Through this project, I demonstrated practical skills in:

* Power BI
* DAX
* Data Modeling
* Data Relationships
* KPI Development
* Customer Churn Analysis
* Customer Segmentation
* Retention Analysis
* Loyalty Program Analysis
* Promotional Analysis
* Store & Channel Analysis
* Customer Lifetime Value
* Business Intelligence
* Data Visualization
* Business Insights

---

# Future Improvements

Potential improvements include:

* Adding time-series sales analysis
* Creating a dedicated executive dashboard
* Building predictive churn modeling
* Adding customer-level drill-through pages
* Connecting the dashboard to a live data source
* Adding automated data refresh
* Integrating Python machine learning for churn prediction

---

# Author

**Naresh Bollepally**

B.Tech – Computer Science & Engineering

Aspiring Data Analyst / Data Scientist

### Skills

```text
Python | SQL | Power BI | DAX | Excel | Machine Learning
```

---

##  Project Category

**Data Analytics | Business Intelligence | Power BI | DAX | Customer Analytics**

---

⭐ If you find this project useful, consider giving the repository a star.

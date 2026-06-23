# 📊 Power BI Projects — DAX & Data Analytics Portfolio

A collection of Power BI dashboards built with advanced DAX, Time Intelligence, and dynamic analysis techniques. Each project tackles a real-world business dataset and delivers actionable insights.

---

## 🗂️ Projects

| Project | Dataset | Pages | Key Techniques |
|---------|---------|-------|----------------|
| [Superstore Sales Dashboard](#-1-superstore-sales-dashboard) | US Retail (9,994 orders) | 5 | Time Intelligence, Dynamic Measures, Top N |
| [TehraanData Sales Report](#-2-tehraandata-power-bi-report) | AdventureWorks | 5 | Dynamic Measures, TREATAS, Numeric Slicer |

---

## 🛒 1. Superstore Sales Dashboard

> Retail sales analysis across the United States (2014–2017)

### Overview
An interactive dashboard analyzing **9,994 orders** across 4 US regions, uncovering profitability issues related to discounting strategy and product category performance.

### Pages
| Page | Description |
|------|-------------|
| **Overview** | KPIs, regional sales distribution, category performance |
| **Detail Analysis** | Sub-category profitability, discount impact |
| **Storytelling** | Top customers, profit matrix, scatter analysis |
| **Time Analysis** | YoY growth, cumulative sales, YTD, margin trend |
| **Dynamic Analysis** | User-controlled measure & Top N ranking |

### Key Insights
- 📉 Discounts above 30% always result in **negative profit**
- 🪑 Furniture has only **2.5% profit margin** despite high revenue
- 🌍 **West region** leads in both sales and profit
- ⚠️ **Central region** has the worst sales-to-profit ratio
- 🏙️ **New York City** is the top-performing city by profit

### DAX Highlights
```dax
-- Year-over-Year Growth
YoY Growth % = 
DIVIDE([Total Sales] - [Sales LY], [Sales LY]) * 100

-- Running Total
Running Total Sales = 
CALCULATE(
    [Total Sales],
    FILTER(ALL(DateTable[Date]), DateTable[Date] <= MAX(DateTable[Date]))
)

-- Dynamic Measure
Dynamic Measure = 
SWITCH(
    SELECTEDVALUE('Measure Selector'[Measure Name]),
    "Sales", [Total Sales],
    "Profit", [Total Profit],
    "Quantity", [Total Quantity],
    [Total Sales]
)
```

### Tools
`Power BI Desktop` `DAX` `SQL Server Express` `SSMS`

📁 [View Project](./Superstore-Sales-Dashboard/)

---

## 🏢 2. TehraanData Power BI Report

> Sales performance, customer behaviour, and geographic analysis

### Overview
A comprehensive business intelligence report built on the **AdventureWorks** dataset, featuring dynamic measure selection, customer segmentation, and product-level analysis across multiple countries.

### Pages
| Page | Description |
|------|-------------|
| **KPI Cards** | Executive summary with key metrics and trends |
| **Customers** | Demographic and geographic customer breakdown |
| **Products** | Category and subcategory performance with YoY comparison |
| **Countries** | Dynamic measure analysis by geography |
| **Sales** | Granular product-level breakdown with numeric slicer |

### Key Features
- 🔄 **Dynamic Measure Selector** — switch between KPIs across all charts
- 📊 **Sales Last Year (SalesLY)** — side-by-side YoY comparison in product table
- 🏆 **Best Year calculation** — dynamically identifies top-performing year
- 🔢 **Numeric Slicer** — filter visuals by custom numeric range
- 👥 **Customer Segmentation** — by gender, age group, and status

### DAX Highlights
```dax
-- Dynamic Measure with TREATAS
FinalMeasure = 
SWITCH(TRUE(),
    [Sel3] = "TotalSale", [TotalSale],
    [Sel3] = "TotalOrders", [TotalOrders],
    [Sel3] = "TotalCustomers", [TotalCustomers]
)

-- Year Over Year Growth
YOYgrowth = DIVIDE([TotalSale] - [SalesLY], [SalesLY]) * 100

-- Sales Per Customer
SalesPerCustomer = DIVIDE([TotalSale], [TotalCustomers])
```

### Tools
`Power BI Desktop` `DAX` `Power BI Cloud`

📁 [View Project](./TehraanData-PowerBI/)

---

## 🧠 DAX Concepts Covered

| Concept | Used In |
|---------|---------|
| `CALCULATE` + `FILTER` | Both projects |
| `ALLEXCEPT` | Superstore |
| `SAMEPERIODLASTYEAR` | Both projects |
| `TOTALYTD` | Superstore |
| `SWITCH` + `SELECTEDVALUE` | Both projects |
| `TOPN` + `RANKX` | Superstore |
| `TREATAS` | TehraanData |
| `CROSSJOIN` + `ROW` + `UNION` | TehraanData |
| `DIVIDE` | Both projects |
| `VAR` / `RETURN` | Both projects |

---

## 🛠️ Tools & Technologies

- **Power BI Desktop** — Dashboard development
- **DAX** — All calculated measures and tables
- **SQL Server Express** — Data storage (Superstore)
- **SSMS** — Data management
- **Power BI Cloud** — Publishing and sharing

---

## 📬 Connect

Feel free to connect on [LinkedIn](#) or explore more of my work here on GitHub!

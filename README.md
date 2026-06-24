# 📊 Power BI Projects — DAX & Analytics Portfolio

A collection of Power BI dashboards built with advanced DAX, Time Intelligence, and dynamic analysis. Each project is based on a real-world dataset and delivers actionable business insights.

---

## 🗂️ Projects

| # | Project | Dataset | Revenue | Pages | Key Techniques |
|---|---------|---------|---------|-------|----------------|
| 1 | [TehraanData Report](#-1-tehraandata-power-bi-report) | AdventureWorks | $29.36M | 4 | Dynamic Measures, TREATAS, Top N Slicer |
| 2 | [Superstore Dashboard](#-2-superstore-sales-dashboard) | US Retail | $2.30M | 5 | Time Intelligence, Dynamic Measures, TOPN |

---

## 🚴 1. TehraanData Power BI Report

> Sales, customer, and product analysis across 6 countries (2010–2014)

### Overview
A comprehensive business intelligence report analyzing **$29.36M in revenue** from the AdventureWorks dataset, covering customer segmentation, product performance, and geographic distribution.

### Pages
| Page | Description |
|------|-------------|
| **KPI Cards** | Executive summary — 6 KPIs + 3 trend charts |
| **Customers** | Segmentation by country, gender, age, and status |
| **Products** | Category analysis with dynamic measure selector |
| **Sales** | Top N product ranking with numeric slicer |

### Key Insights
- 🚴 Bikes account for **87% of all revenue**
- 🌍 **US and Australia** are the dominant markets
- 👥 **86.58% of customers are Regular** — large VIP upgrade opportunity
- 📅 **December and November** are peak sales months
- 🏆 **Mountain-200** is the best-selling product line

### DAX Highlights
```dax
-- Dynamic Measure with SWITCH
FinalMeasure = 
SWITCH(
    SELECTEDVALUE(DynamicMeasures[Column1]),
    "TotalSale", [TotalSale],
    "TotalOrders", [TotalOrders],
    "TotalCustomers", [TotalCustomers],
    [TotalSale]
)

-- Sales Per Customer
SalesPerCustomer = DIVIDE([TotalSale], [TotalCustomers])

-- Year Over Year Growth
YOYgrowth = DIVIDE([TotalSale] - [SalesLY], [SalesLY]) * 100
```

📁 [View Project](./TehraanData-PowerBI/)

---

## 🛒 2. Superstore Sales Dashboard

> Retail sales analysis across the United States (2014–2017)

### Overview
An interactive dashboard analyzing **9,994 orders** across 4 US regions, uncovering profitability issues related to discounting strategy and product category performance.

### Pages
| Page | Description |
|------|-------------|
| **Overview** | KPIs, regional distribution, category performance |
| **Detail Analysis** | Sub-category profitability, discount impact |
| **Storytelling** | Top customers, profit matrix, scatter analysis |
| **Time Analysis** | YoY growth, cumulative sales, YTD, margin trend |
| **Dynamic Analysis** | User-controlled measure & Top N ranking |

### Key Insights
- 📉 Discounts above **30% always result in losses**
- 🪑 Furniture has only **2.5% profit margin** despite high revenue
- 🌍 **West region** leads in both sales and profit
- ⚠️ **Central region** has the worst sales-to-profit ratio
- 🏙️ **New York City** is the top city by profit

### DAX Highlights
```dax
-- Year-over-Year Growth
YoY Growth % = 
DIVIDE([Total Sales] - [Sales LY], [Sales LY]) * 100

-- Running Total
Running Total Sales = 
CALCULATE(
    [Total Sales],
    FILTER(
        ALL(DateTable[Date]),
        DateTable[Date] <= MAX(DateTable[Date])
    )
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

-- Top N with Dynamic Measure
Top N = 
VAR SelectedN = SELECTEDVALUE('TopN Table'[Value], 10)
RETURN
CALCULATE(
    [Dynamic Measure],
    TOPN(SelectedN, ALL(SalesNew[Customer_Name]), [Dynamic Measure])
)
```

📁 [View Project](./Superstore-Sales-Dashboard/)

---

## 🧠 DAX Concepts Covered

| Concept | TehraanData | Superstore |
|---------|-------------|------------|
| `CALCULATE` + `FILTER` | ✅ | ✅ |
| `SWITCH` + `SELECTEDVALUE` | ✅ | ✅ |
| `DIVIDE` | ✅ | ✅ |
| `VAR` / `RETURN` | ✅ | ✅ |
| `SAMEPERIODLASTYEAR` | ✅ | ✅ |
| `TOTALYTD` | ❌ | ✅ |
| `TOPN` + `RANKX` | ❌ | ✅ |
| `ALLEXCEPT` | ❌ | ✅ |
| `TREATAS` | ✅ | ❌ |
| `CROSSJOIN` + `ROW` + `UNION` | ✅ | ❌ |
| Running Total | ❌ | ✅ |
| Numeric Slicer (Helper Table) | ✅ | ✅ |

---

## 🛠️ Tools & Technologies

| Tool | Usage |
|------|-------|
| **Power BI Desktop** | Dashboard development |
| **DAX** | All measures and dynamic analysis |
| **SQL Server Express** | Data storage (Superstore) |
| **SSMS** | Data management and querying |
| **Power BI Cloud** | Publishing (TehraanData) |

---

## 📬 Connect

Feel free to connect on [LinkedIn](#) or explore more projects here on GitHub!

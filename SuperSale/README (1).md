# 🛒 Superstore Sales Dashboard — Power BI

An interactive, multi-page Power BI dashboard analyzing **9,994 retail orders** across the United States (2014–2017). Built to surface actionable business insights through advanced DAX measures, Time Intelligence, and dynamic user-driven analysis.

---

## 📊 Dashboard Pages

| Page | Description |
|------|-------------|
| **Overview** | KPIs, regional sales distribution, category performance |
| **Detail Analysis** | Sub-category profitability, discount impact on profit |
| **Storytelling** | Top customers, profit matrix, scatter analysis |
| **Time Analysis** | YoY growth, cumulative sales, YTD progress, margin trend |
| **Dynamic Analysis** | User-controlled dimension & measure selection, Top N ranking |

---

## 🔍 Key Business Insights

- 📉 **Discounts above 30% always result in losses** — confirmed across all categories
- 🪑 **Furniture has only 2.5% profit margin** despite being 2nd in revenue — a pricing problem
- 🌍 **West region dominates** with $725K in sales and $108K profit
- ⚠️ **Central region is underperforming** — highest revenue-to-profit gap
- 🖨️ **Copiers deliver the best ROI** — highest profit despite lower sales volume
- 🏙️ **New York City leads** in profit among all cities ($62K+)
- 📦 **Tables and Bookcases are loss-making** sub-categories despite significant sales volume

---

## 🧮 DAX Measures

### Core Measures
| Measure | Description |
|---------|-------------|
| `Total Sales` | SUM of all sales revenue |
| `Total Profit` | SUM of all profit |
| `Total Quantity` | SUM of all order quantities |
| `Profit Margin %` | Profit ÷ Sales × 100 |
| `Avg Discount` | Average discount rate per order |
| `Loss Flag` | Conditional color flag for negative profit |

### Time Intelligence
| Measure | Description |
|---------|-------------|
| `Sales LY` | Sales in the same period last year |
| `YoY Growth %` | Year-over-Year sales growth percentage |
| `Running Total Sales` | Cumulative sales from start to current date |
| `YTD Sales` | Year-to-date sales progress |
| `Profit Margin LY` | Profit margin in same period last year |
| `Profit Margin YoY` | Change in profit margin vs last year |

### Dynamic Measures
| Measure | Description |
|---------|-------------|
| `Dynamic Measure` | SWITCH-based measure selector (Sales/Profit/Quantity/Discount) |
| `Top N` | TOPN-based ranking with user-controlled N value |
| `Customer Rank` | RANKX-based customer ranking by selected measure |

---

## 🗄️ Data Model

```
DateTable (Date) ──────► SalesNew (Order_Date)
     │
     └── Year, Month, MonthName, Quarter

Measure Selector ──────► (Disconnected - used via SELECTEDVALUE)
TopN Table ────────────► (Disconnected - used via SELECTEDVALUE)
```

- **Fact Table:** SalesNew (9,994 rows)
- **Dimension Table:** DateTable (continuous calendar 2014–2017)
- **Relationship:** One-to-Many | Single direction filter
- **Dynamic Tables:** Measure Selector, TopN Table (disconnected slicers)

---

## 🛠️ Tools & Technologies

| Tool | Usage |
|------|-------|
| **Power BI Desktop** | Dashboard development & visualization |
| **DAX** | Calculated measures, Time Intelligence, dynamic analysis |
| **SQL Server Express** | Data storage and management |
| **SSMS** | Data import, transformation, and querying |

---

## 📁 Dataset

- **Source:** [Superstore Sales Dataset — Kaggle](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final)
- **Records:** 9,994 orders
- **Period:** January 2014 — December 2017
- **Geography:** United States (4 Regions, 49 States)
- **Categories:** Furniture, Technology, Office Supplies

---

## 🚀 How to Run

1. Clone this repository
2. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/)
3. Install [SQL Server Express](https://www.microsoft.com/sql-server/sql-server-downloads)
4. Import `SampleSuperstore.csv` into SQL Server as `SalesNew`
5. Open `SuperSale.pbix` in Power BI Desktop
6. Update data source to your local SQL Server instance
7. Click **Refresh** and explore!

---

## 💡 What I Learned

- Building a proper **Date Table** for Time Intelligence functions
- Writing advanced **DAX** including `CALCULATE`, `FILTER`, `ALLEXCEPT`, `TREATAS`
- Implementing **Time Intelligence** (YoY, Running Total, YTD)
- Creating **Dynamic Measures** using `SWITCH` + `SELECTEDVALUE`
- Building **Top N analysis** using `TOPN` and `RANKX`
- Designing **interactive dashboards** with Slicers, Sync, and Conditional Formatting
- Understanding **data model relationships** and filter direction

---

## 📸 Dashboard Preview

| Page | Preview |
|------|---------|
| Overview | ![Overview](screenshots/overview.png) |
| Detail Analysis | ![Detail](screenshots/detail.png) |
| Time Analysis | ![Time](screenshots/time.png) |
| Dynamic Analysis | ![Dynamic](screenshots/dynamic.png) |

---

## 📬 Connect

Feel free to connect on [LinkedIn](#) or explore my other projects on [GitHub](#)!

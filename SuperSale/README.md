# 🛒 Superstore Sales Dashboard

An interactive Power BI dashboard analyzing sales, profit, and customer behavior for a retail superstore — built to uncover actionable business insights from 9,994 orders across the United States.

---

## 📊 Dashboard Pages

| Page | Description |
|------|-------------|
| **Overview** | High-level KPIs, sales by region and category |
| **Detail Analysis** | Sub-category profitability and discount impact |
| **Storytelling** | Top customers, scatter analysis, profit matrix |
| **Time Analysis** | YoY growth, cumulative sales, profit margin trend |

---

## 🔍 Key Insights

- 📉 **Discounts above 30% result in negative profit** — every order with 30%+ discount lost money
- 🪑 **Furniture has the lowest profit margin (2.5%)** despite being the second-highest revenue category
- 🌍 **West region leads in both sales ($725K) and profit ($108K)**
- ⚠️ **Central region is underperforming** — highest sales-to-profit gap
- 🖨️ **Copiers generate the highest profit** despite lower sales volume

---

## 🧮 DAX Measures

| Measure | Description |
|---------|-------------|
| `Total Sales` | SUM of all sales |
| `Total Profit` | SUM of all profit |
| `Total Quantity` | SUM of all orders |
| `Profit Margin %` | Profit ÷ Sales × 100 |
| `Sales LY` | Sales in the same period last year |
| `YoY Growth %` | Year-over-Year sales growth percentage |
| `Running Total Sales` | Cumulative sales over time |
| `YTD Sales` | Year-to-date sales progress |
| `Profit Margin LY` | Profit margin in same period last year |
| `Profit Margin YoY` | Change in profit margin vs last year |
| `Avg Discount` | Average discount per order |
| `Loss Flag` | Flags categories/sub-categories with negative profit |

---

## 🗄️ Data Model

```
DateTable (Date) ──────► SalesNew (Order_Date)
     │
     └── Year, Month, MonthName, Quarter
```

- **Fact Table:** SalesNew (9,994 rows)
- **Dimension Table:** DateTable (continuous calendar)
- **Relationship:** One-to-Many | Single direction filter

---

## 🛠️ Tools & Technologies

- **Power BI Desktop** — Dashboard development
- **DAX** — Calculated measures and Time Intelligence
- **SQL Server Express** — Data storage
- **SSMS** — Data import and management

---

## 📁 Dataset

- **Source:** [Superstore Sales Dataset - Kaggle](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final)
- **Records:** 9,994 orders
- **Period:** 2014 - 2017
- **Region:** United States

---

## 🚀 How to Use

1. Clone this repository
2. Open `SuperSale.pbix` in Power BI Desktop
3. If needed, update the data source to your local SQL Server
4. Refresh the data and explore!

---

## 📸 Dashboard Preview

### Overview
![Overview](screenshots/overview.png)

### Time Analysis
![Time Analysis](screenshots/time_analysis.png)

---

## 💡 What I Learned

- Designing a **Date Table** for Time Intelligence functions
- Writing advanced **DAX measures** (YoY, Running Total, YTD)
- Using **CALCULATE**, **FILTER**, **ALLEXCEPT** for context manipulation
- Building **interactive dashboards** with Slicers and Sync
- Applying **Conditional Formatting** based on DAX measures

---

## 📬 Connect With Me

Feel free to connect on [LinkedIn](#) or check out my other projects on [GitHub](#)!

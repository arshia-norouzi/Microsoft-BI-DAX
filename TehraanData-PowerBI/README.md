# 🚴 TehraanData Power BI Report

An interactive Power BI dashboard analyzing **$29.36M in sales** across 6 countries, built on the AdventureWorks dataset. The report covers sales performance, customer behaviour, product trends, and geographic distribution across **4 analytical pages**.

---

## 📊 Dashboard Pages

### 1. KPI Cards — Executive Summary
High-level performance indicators with trend visuals.

| Visual | Description |
|--------|-------------|
| **Total Sale** | $29.36M aggregate revenue |
| **Total Orders** | 28K orders |
| **Average Order Value** | $1.1K per order |
| **Sales Per Customer** | $1.6K revenue per customer |
| **Order Per Customer** | 1.5 orders per customer |
| **Year Over Year Growth** | 2.2x YoY growth rate |
| **Sales by Month** | Line chart — seasonal trends |
| **Sales by Subcategory** | Top performing subcategories |
| **Sales by Country** | Geographic revenue distribution |

---

### 2. Customers — Demographic Analysis
Deep dive into customer segmentation and behaviour.

| Visual | Description |
|--------|-------------|
| **Customers by Country** | US leads with 8K+ customers |
| **Customer Status** | Regular (86.58%), Gold (10.13%), VIP (3.28%) |
| **Sales by Gender** | Nearly equal — Female 50.46%, Male 49.54% |
| **Sales by Age Group** | Middle-aged customers dominate revenue |

---

### 3. Products — Category & Subcategory Analysis
Product-level performance with year filtering.

| Visual | Description |
|--------|-------------|
| **Sales by Category** | Bikes 87.06%, Accessories 8.5%, Clothing 4.43% |
| **Year Slicer** | Filter by 2010–2014 |
| **Tax Amount by Subcategory** | Mountain Bikes lead in tax contribution |
| **Dynamic Measure Selector** | Switch between Freight, SalesAmount, OrderQuantity, TaxAmount |

---

### 4. Sales — Product-Level Breakdown
Granular analysis with numeric Top N slicer.

| Visual | Description |
|--------|-------------|
| **Top N Products** | User-controlled slicer (1–10) filters top products |
| **Sales by Product Name** | Mountain-200 and Road-150 dominate |
| **Sales by Subcategory** | Road Bikes ($15M) leads all subcategories |

---

## 🔍 Key Insights

- 🚴 **Bikes account for 87% of all revenue** — heavy product concentration risk
- 🌍 **US and Australia** are the top 2 markets by both sales and customers
- 👥 **86.58% of customers are Regular status** — large VIP upgrade opportunity
- ⚖️ **Gender split is nearly equal** (50.46% F vs 49.54% M) — balanced customer base
- 📅 **December and November** are peak sales months
- 🏆 **Mountain-200 and Road-150** are the top-selling product lines

---

## 🧮 Key DAX Measures

| Measure | Description |
|---------|-------------|
| `TotalSale` | SUM of total sales revenue |
| `TotalOrders` | COUNT of total orders |
| `TotalCustomers` | DISTINCTCOUNT of customers |
| `AverageOrderValue` | TotalSale ÷ TotalOrders |
| `SalesPerCustomer` | TotalSale ÷ TotalCustomers |
| `OrderPerCustomer` | TotalOrders ÷ TotalCustomers |
| `YOYgrowth` | Year-over-Year growth rate |
| `SalesLY` | Sales in prior year |
| `FinalMeasure` | Dynamic measure via SWITCH + SELECTEDVALUE |
| `IfSale` | Numeric slicer-based Top N filter for products |
| `IfSubCategory` | Numeric slicer-based Top N filter for subcategories |

---

## 🗄️ Data Model

| Table | Type | Description |
|-------|------|-------------|
| `DimCustomer` | Dimension | Customer details, gender, age group, status |
| `DimProduct` | Dimension | Product names and details |
| `DimProductCategory` | Dimension | Bikes, Accessories, Clothing |
| `DimProductSubcategory` | Dimension | Road Bikes, Mountain Bikes, etc. |
| `DimDate` | Dimension | Calendar years and month names |
| `DimGeography` | Dimension | Country and region data |
| `FactInternetSales` | Fact | Sales transactions |
| `Numbers` | Helper | Numeric slicer values for Top N |
| `DynamicMeasures` | Helper | Measure selector for dynamic charts |

---

## 🛠️ Tools & Technologies

| Tool | Usage |
|------|-------|
| **Power BI Desktop** | Dashboard development |
| **DAX** | All measures and dynamic analysis |
| **Power BI Cloud** | Publishing and sharing |

---

## 📁 Dataset

- **Source:** AdventureWorks (Microsoft sample database)
- **Total Revenue:** $29.36M
- **Total Orders:** 28K
- **Period:** 2010 – 2014
- **Geography:** US, Australia, UK, Germany, France, Canada

---

## 🚀 How to Run

1. Open `TehraanDataPowerBI.pbix` in Power BI Desktop
2. Refresh the data model if connected to a live source
3. Use the **Year Slicer** on the Products page to filter by year
4. Use the **Numeric Slicer** on the Sales page to control Top N products
5. Use the **Measure Selector** on the Products page to switch KPIs

---

## 💡 What I Learned

- Building **dynamic measures** with `SWITCH` + `SELECTEDVALUE`
- Using **TREATAS** to apply filters across disconnected tables
- Creating **numeric slicers** with helper tables for Top N analysis
- Designing **customer segmentation** visuals with demographic data
- Working with a **star schema** data model (AdventureWorks)

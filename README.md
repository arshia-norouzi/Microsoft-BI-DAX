# TehraanData Power BI Report

## Overview

This Power BI report provides a comprehensive analysis of sales performance, customer behaviour, product trends, and geographic distribution. Built in Power BI Desktop (version 2025.08, report format v1.28), the report is structured across **5 interactive pages**, each focused on a distinct analytical domain.

---

## File Information

| Property | Value |
|---|---|
| File | `TehraanDataPowerBI.pbix` |
| Power BI Version | 1.28 (2025.08) |
| Created From | Power BI Cloud |
| File Size | ~4.4 MB |

---

## Report Pages

### 1. KPI Cards
A high-level executive summary page featuring key performance indicators and trend visuals.

**Visuals:**
- **Total Sales** — Card showing aggregate sales revenue
- **Total Orders** — Card showing total number of orders
- **Average Order Value** — Card showing mean value per order
- **Sale Per Customer** — Card showing revenue per customer
- **Order Per Customer** — Card showing orders per customer ratio
- **Year Over Year Growth** — Card displaying YoY growth rate
- **Sales by Month** — Line chart of `TotalSale` by `EnglishMonthName`
- **Sales by Product Category** — Column chart of `TotalSale` by `EnglishProductCategoryName`
- **Sales by Country** — Column chart of `TotalSale` by `EnglishCountryRegionName`

---

### 2. Customers
Demographic and geographic breakdown of the customer base.

**Visuals:**
- **Sales by Gender** — Column chart of `TotalSale` by `Gender`
- **Sales by Age Group** — Bar chart of `TotalSale` by `AgeStatus`
- **Top Customers by Name** — Column chart ranking customers by `TotalSale`
- **Customers by Country** — Column chart of `TotalCustomers` by `EnglishCountryRegionName`
- **Customer Status** — Pie chart showing distribution of customer `Status` by `Share`

---

### 3. Products
Product-level performance analysis with year and subcategory filtering.

**Visuals:**
- **Sales by Category** — Donut chart of sales by `EnglishProductCategoryName`
- **Sales by Subcategory & Year** — Table showing `CalendarYear`, `EnglishProductSubcategoryName`, `TotalSale`, and `SalesLY` (Sales Last Year)
- **Year Slicer** — Filter by `CalendarYear`

---

### 4. Countries
Geographic analysis with dynamic measure selection.

**Visuals:**
- **Dynamic Measure by Country** — Column chart of `FinalMeasure` by `EnglishCountryRegionName`
- **Dynamic Measure by Subcategory** — Column chart of `FinalMeasure` by `EnglishProductSubcategoryName`
- **Best Year** — Card displaying the top-performing year (`TopYear`)
- **Measure Selector Slicer** — Dynamically switches the measure shown in charts

---

### 5. Sales
Granular product and subcategory sales breakdown with a numeric slicer.

**Visuals:**
- **TotalSale by Product Name** — Column chart of `IfSale` by `EnglishProductName`
- **TotalSale by Subcategory** — Column chart of `IfSubCategory` by `EnglishProductSubcategoryName`
- **Numeric Slicer** — Filters the above visuals by a numeric range

---

## Data Model

The report is powered by an in-memory VertiPaq data model containing the following tables:

| Table | Type | Description |
|---|---|---|
| `DimCustomer` | Dimension | Customer details including `FullName`, `Gender`, `AgeStatus` |
| `DimProduct` | Dimension | Product details including `EnglishProductName` |
| `DimProductCategory` | Dimension | Product categories (`EnglishProductCategoryName`) |
| `DimProductSubcategory` | Dimension | Product subcategories (`EnglishProductSubcategoryName`) |
| `DimDate` | Dimension | Date table with `CalendarYear`, `EnglishMonthName` |
| `DimGeography` | Dimension | Geographic data (`EnglishCountryRegionName`) |
| `Measure Pool (2)` | Measure table | Core calculated measures (see below) |
| `DynamicMeasures (2)` | Dynamic measure table | Switchable `FinalMeasure` and `Column1` selector |
| `CategorySale` | Aggregation | Pre-aggregated sales by category |
| `CustomersStatus` | Reference | Customer status labels and share percentages |
| `BestYear` | Calculation | Returns the best-performing year (`TopYear`) |
| `Numbers` | Helper | Numeric slicer values (`Column1`, `IfSale`, `IfSubCategory`) |

---

## Key Measures

The following measures are defined in `Measure Pool (2)`:

| Measure | Description |
|---|---|
| `TotalSale` | Sum of total sales revenue |
| `TotalOrders` | Count of total orders |
| `AverageOrderValue` | Average revenue per order |
| `SalesPerCustomer` | Total sales divided by number of customers |
| `OrderPerCustomer` | Total orders divided by number of customers |
| `YOYgrowth` | Year-over-year growth rate |
| `SalesLY` | Sales in the prior year (Last Year) |
| `TotalCustomers` | Count of distinct customers |

---

## Requirements

- **Power BI Desktop** 2025.08 or later (to open and edit the `.pbix` file)
- **Power BI Service** (to publish and share the report online)

---

## Usage

1. Open `TehraanDataPowerBI.pbix` in Power BI Desktop.
2. Refresh the data model if connected to a live data source.
3. Use the slicers on the **Products**, **Countries**, and **Sales** pages to filter visuals interactively.
4. The **Countries** page features a dynamic measure selector — use the slicer to switch between different KPIs across charts.
5. Publish to Power BI Service for sharing and scheduled refresh.

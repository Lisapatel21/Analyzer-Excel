[README (2).md](https://github.com/user-attachments/files/34217000/README.2.md)
# 📊 PR. 2 Analyzer: Business Intelligence & Spreadsheet Modeling

## 🌟 Project Overview
The **PR. 2 Analyzer** is an Excel-based analytics model that evaluates regional sales, product profitability, customer purchasing behavior, and the relationship between revenue and profit. It combines descriptive statistics, regression, What-If scenario planning, lookup formulas, conditional formatting, pivot tables, and a chart dashboard, turning 200 raw transactions into a business story.

**Business questions this workbook answers**
1. Which regions and product categories drive revenue and profit?
2. How much profit does each extra dollar of sales generate?
3. Which customers and orders are the highest value?
4. How sensitive is profit to discounting?

---

## 🔗 View Project Spreadsheet

[📁 Click Here to View the Excel Spreadsheet](https://docs.google.com/spreadsheets/d/18XqU8hnZn9KRKKIeYksB9oLFq1_ZwiE0/edit?usp=drive_link&ouid=105190136189399848271&rtpof=true&sd=true)

This link provides access to the project spreadsheet, allowing you to view and explore the work in full.

---

## 🎥 Project Video

[▶️ Click Here to Watch the Project Video](https://drive.google.com/file/d/1IIJ0IK338RZHmSmXgZJhS9YASs9c1PGB/view?usp=drive_link)

This link opens the project video on Google Drive, offering a visual look at the PR. 2 Analyzer project alongside the spreadsheet.

---

## 🛠️ Skills Demonstrated
| Area | What was done | Where |
|---|---|---|
| Descriptive statistics | Mean, median, mode, std. dev., variance, kurtosis, skewness, range, sum, count for Sales, Quantity, Discount, Order Date, Profit | `Dataset!P2:Y15` |
| Linear regression | Profit vs. Sales via the Data Analysis Toolpak (summary, ANOVA, coefficients) | `Dataset!AA2:AI19` |
| What-If analysis | `New_Profit_Scenario = Profit × (1 − Test_Discount)` | `Dataset!K:L` |
| Lookup & ranking | `INDEX` + `MATCH` + `LARGE` to return the customer behind the Nth-largest sale | `Dataset!M:N` |
| Timestamp | `=NOW()` column (volatile; updates on every recalculation) | `Dataset!J` |
| Custom number format | ▲ green / ▼ red arrows on scenario results | `Dataset!L` |
| Conditional formatting | Top 10 sales highlighted using `RANK` | `Dataset!A2:I201` |
| Pivot table | Sales by Region → Product Category, with grand total | `Pivote Table` |
| Dashboard | Bar, line, and pie charts | `Dashboard` |

---

## 📁 Workbook Architecture
1. **Project Instructions** – task list and deliverable guidelines.
2. **Dashboard** – three charts (bar, line, pie) summarizing the pivot data.
3. **Pivote Table** – Sum of Sales by Region (*Central, East, North, South, West*) and Category (*Books, Clothing, Electronics, Furniture, Office Supplies*). *(Sheet name keeps the original spelling.)*
4. **Dataset** – 200 transactions from **10 Apr 2024 to 7 Apr 2025**, plus the helper columns and Toolpak outputs listed above.

---

## 📈 Key Findings

### Headline numbers
| KPI | Value |
|---|---|
| Total sales | **$195,217.76** |
| Total profit | **$68,287.01** |
| Overall profit margin | **35.0%** |
| Transactions | 200 |
| Average sale | $976.09 (median $976.72, so the distribution is roughly symmetric) |
| Average profit per order | $341.44 |

### By region
| Region | Sales | Share | Profit | Margin |
|---|---:|---:|---:|---:|
| West | $44,083.58 | 22.6% | $14,985.83 | 34.0% |
| Central | $43,468.33 | 22.3% | $16,068.40 | **37.0%** |
| South | $40,248.79 | 20.6% | $13,691.91 | 34.0% |
| North | $34,975.42 | 17.9% | $11,902.28 | 34.0% |
| East | $32,441.64 | 16.6% | $11,638.59 | 35.9% |

West leads on revenue, but **Central is the most profitable region** and earns the best margin, which makes it the better model to copy.

### By product category
| Category | Sales | Share |
|---|---:|---:|
| Books | $47,002.46 | 24.1% |
| Clothing | $41,927.59 | 21.5% |
| Electronics | $41,044.00 | 21.0% |
| Furniture | $36,612.89 | 18.8% |
| Office Supplies | $28,630.82 | 14.7% |

**Books is the top category overall**, followed closely by Clothing and Electronics. Office Supplies is the weakest.

### Region × category hot spots
* Strongest cells: Central–Clothing ($12,200), South–Electronics ($11,989), East–Books ($11,389), West–Electronics ($11,372), Central–Books ($11,297).
* Weakest cells: South–Office Supplies ($2,295), East–Clothing ($2,401), East–Electronics ($2,870), which are the places to look for under-performance.

### Regression: Profit vs. Sales
| Metric | Value |
|---|---|
| Multiple R | 0.7734 |
| R² | 0.5982 |
| Adjusted R² | 0.5961 |
| Slope | 0.3509 (p < 0.001) |
| Intercept | −1.03 (p = 0.96, not significant) |
| Significance F | 4.6 × 10⁻⁴¹ |

**Reading it:** each extra $1 of sales is associated with about **$0.35 of additional profit**, and the relationship is highly significant. Sales explain roughly 60% of profit variation, so the correlation is strong but not complete; the other ~40% likely comes from discounts, product mix, and costs. The near-zero intercept means profit scales almost proportionally with sales.

### Descriptive-statistics notes
* Sales, Quantity, Discount, and Order Date all have **negative kurtosis** (Quantity −1.21, Discount −1.33), meaning flat, evenly spread distributions rather than peaked ones.
* Skewness is small for every variable (all below 0.6), so no heavy outliers.
* Discounts range from 0% to 20% (mean 9.7%).

---

## 🚀 How to Use
1. Open `_PR. 2 Analyzer.xlsx` in Microsoft Excel (Google Sheets will not reproduce the custom arrow format or Toolpak output exactly).
2. **Dataset** → review raw records, helper columns, and statistics.
3. **Pivote Table** → refresh after any data change (*Data → Refresh All*).
4. **Dashboard** → read the three charts.
5. For What-If testing, edit the discount values in `Dataset!K` (see note below).

---

## ⚠️ Known Limitations & Recommended Improvements
These came up while checking the workbook against this README. They are worth fixing before presenting the model.

| # | Issue | Why it matters | Suggested fix |
|---|---|---|---|
| 1 | **What-If discounts are not realistic.** `K2 = (ROW()-1)*0.2` produces 20%, 40% … up to 4000%, so most scenario profits are negative. | The scenario results are not meaningful, and the values are formulas, not editable inputs. | Replace with a single input cell (e.g. a 0–30% discount) or a Data Table / Scenario Manager with 0%, 5%, 10%, 15%, 20%, 25%. |
| 2 | **Customer IDs and names don't match.** Each of the 30 Customer_IDs is linked to 2–9 different names (e.g. CUST014 appears as both Emma Davis and David Thomas). | Customer-level totals and "top customer" lookups are unreliable by name. | Standardize a Customer_ID → Name master list. |
| 3 | **Top-10 highlighting ranks single orders, not customer totals.** The rule is `RANK($E2, …) <= 10` on the Sales column. | The project brief asks for top customers by *total purchase*. | Add a customer-total column (`SUMIF` on Customer_ID) and rank that instead. By ID, the top customers are CUST015 ($11,611), CUST028 ($10,294), CUST007 ($9,942), CUST008 ($9,761), CUST026 ($9,372). |
| 4 | **The INDEX/MATCH ranking returns the buyer of each Nth-largest single sale.** | Ties in Sales would return the same name twice. | Add a tiebreaker, or build the lookup off a de-duplicated customer summary. |
| 5 | **Arrows are applied to scenario profit, not monthly sales growth.** | The brief asks for arrows on monthly growth. | Add a monthly sales table with MoM % change and apply the ▲/▼ format there. |
| 6 | **Mode shows `#N/A`** for Sales and Profit. | Every value is unique, so no mode exists. | Expected result; note it in the sheet or hide the cell with `IFERROR`. |
| 7 | **The Dashboard has charts but no KPI cards.** | An executive view should lead with headline numbers. | Add cells for total sales, profit, margin, top region, and top category linked to the pivot. |

---

## 🔭 Ideas for Future Versions
* **Monthly trend sheet** with MoM growth and a rolling 3-month average.
* **Multiple regression** (Profit ~ Sales + Discount + Quantity) to test whether discounts erode profit.
* **Profit-margin chart by region and category**, not just sales.
* **Slicers** on the pivot (Region, Category, Year-Month) to make the Dashboard interactive.
* **Customer segmentation** (high / mid / low value) using total purchase quartiles.
* **Histogram** of Sales (listed in the project topics, not yet built).
* **Data validation dropdowns** for Region and Category to keep new rows clean.

---
*Author: **Lisa Patel**.*

⭐ *"Thank you for exploring this project! May your spreadsheets always balance, your data stories inspire, and your analytics journey be filled with continuous discovery."*

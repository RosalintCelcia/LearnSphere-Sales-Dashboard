# 📊 LearnSphere Sales Performance Dashboard (Power BI)

An interactive Power BI report that tracks revenue, leads, conversion, order value and customer-acquisition cost for **LearnSphere**, a fictional ed-tech company selling online courses through YouTube and paid ads.

> ⚠️ All data in this project is **synthetic (dummy) data** created for portfolio purposes. LearnSphere is not a real company.

![Overview dashboard](images/01_overview.png)

---

## 🎯 Business problem

The sales and marketing teams kept their numbers in separate monthly Excel sheets. Nobody could answer simple questions quickly:

- Is revenue growing, and is the growth coming from more customers or higher prices?
- Which channel (YouTube or paid ads) brings in revenue more efficiently?
- Which course programs give the best return on marketing spend?

This dashboard puts 3+ years of data (Apr 2023 – Jun 2026) on 3 interactive pages.

## 🗂️ Dashboard pages

| Page | What it answers |
|---|---|
| **1. Overview** | Revenue, units, leads, AOV and conversion vs last year, plus monthly trend, YoY growth and seasonality |
| **2. Source Performance** | YouTube vs Ads: leads, units, conversion %, ARPU and acquisition cost % |
| **3. Program Performance** | 7 programs (DA, DS, BA, DM, Gen AI, CS, AI/ML): revenue, conversion, AOV, CAC and marketing spend |

<p float="left">
  <img src="images/02_source.png" width="49%" />
  <img src="images/03_program.png" width="49%" />
</p>

## 💡 Key insights

1. **Revenue grew 27.8% in FY26** to ₹709 L (from ₹555 L in FY25 and ₹438 L in FY24).
2. **The growth is price-led.** Average order value rose 32% (₹12.9K → ₹16.2K) from FY24 to FY26, while lead-to-sale conversion stayed flat at 6.6–7.3%.
3. **Strong seasonality.** Jan–Mar brings in ~38% of the year's revenue every year, and revenue drops ~65% from March to April.
4. **Ads overtook YouTube** in revenue for the first time in FY26 (₹364 L vs ₹345 L).
5. **AI/ML has the highest conversion (11.1%)** with the lowest marketing spend, which makes it a scale-up opportunity.
6. **Growth is slowing.** YoY growth fell from ~29% (Mar-26) to 19% (Jun-26).

## 🛠️ Tools & skills

- **Power BI Desktop**: data modeling, DAX, bookmarks, page navigation, custom theme
- **Power Query**: cleaning and reshaping monthly Excel/CSV files
- **DAX**: KPIs, YoY %, MoM %, dynamic CAC %, conversion %
- **Excel**: source data preparation

## 🧱 Data model

![Data model](images/04_data_model.png)

- `Date Table`: a shared calendar table, related to all fact tables
- Fact tables: monthly revenue, source-wise leads and units, program-wise performance, CAC/cost
- Slicer tables for Source and Program

## 🧮 Sample DAX measures

```DAX
Total Revenue = SUM ( 'Revenue'[Realized Revenue] )

Revenue PY =
CALCULATE ( [Total Revenue], SAMEPERIODLASTYEAR ( 'Date Table'[Date] ) )

Revenue YoY % =
DIVIDE ( [Total Revenue] - [Revenue PY], [Revenue PY] )

Conversion % =
DIVIDE ( SUM ( 'Leads'[Units] ), SUM ( 'Leads'[Leads] ) )

Acquisition Cost % =
DIVIDE ( [Marketing Spend] + [Sales Cost], [Total Revenue] )
```
*(Replace these with your own measures from the report.)*

## 📁 Repository structure

```
├── LearnSphere_Sales_Dashboard.pbix
├── data/
│   ├── Historical_Data.xlsx
│   ├── LearnSphere_Marketing_Cost.xlsx
│   └── LearnSphere_Payment_Sheet.csv
├── theme/
│   └── theme_LearnSphere_Dark.json
├── images/
│   ├── 01_overview.png
│   ├── 02_source.png
│   ├── 03_program.png
│   └── 04_data_model.png
└── README.md
```

## ▶️ How to use

1. Download or clone this repo.
2. Open `LearnSphere_Sales_Dashboard.pbix` in **Power BI Desktop** (free).
3. If prompted, point the data source to the files in the `data/` folder (*Transform data → Data source settings*).

## 👩‍💻 About me

**Rosalint Celciaa**, Data Analyst (Excel · SQL · Python · Power BI)
📧 rosalint.celciaa@gmail.com · 🔗 [LinkedIn](https://www.linkedin.com/in/YOUR-PROFILE)

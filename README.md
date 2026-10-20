# Financial Sales Dashboard (Power BI)

An interactive Power BI dashboard analysing sales, profit, discounts and product performance across 5 customer segments, 5 countries and 6 products.

## Preview

![Executive Overview](screenshots/page1_overview.png)
![Product and Segment Analysis](screenshots/page2_analysis.png)

## Dataset

Microsoft's public **Financial Sample** dataset (`data/Financial_Sample.xlsx`).

- 700 rows, 16 columns
- Period: Sep 2013 to Dec 2014 (2013 covers only 4 months)
- Fields: Segment, Country, Product, Discount Band, Units Sold, Manufacturing Price, Sale Price, Gross Sales, Discounts, Sales, COGS, Profit, Date
- This is sample data and the currency is not specified in the file

## Tools

Power BI Desktop, Power Query, DAX

## Data Preparation

- Renamed the ` Sales` column (it had a leading space)
- Replaced blank Discount Band values with `None` (these rows have zero discount)
- Set correct data types for dates, prices and numeric columns
- Created a `DateTable` in DAX, marked it as the date table and related it to the sales table
- Kept all measures in a separate `_Measures` table

## Key Measures

Total Sales, Total Profit, Total Units Sold, Total Discounts, Profit Margin %, Discount %, Loss Making Orders, Sales YoY %, Sales YTD and more. Full code is in [`dax/measures.txt`](dax/measures.txt).

## Dashboard Pages

**1. Executive Overview**
KPI cards, monthly sales and profit trend, sales and profit by segment, sales by product, sales by country, and slicers for Year, Segment, Country, Product and Discount Band.

**2. Product and Segment Analysis**
Profit heatmap (Product x Segment), sales vs profit margin by product, profit margin by discount band, and loss-making orders by product.

## Key Insights

- Total sales of about 118.7M with a profit of about 16.9M, a margin of about 14.2%
- Government is the largest segment, with about 52.5M in sales
- Enterprise is loss-making (about -0.61M profit), and all 58 loss-making orders belong to this segment
- Higher discounts go with lower margins: None about 21.9%, Low about 17.9%, Medium about 14.4%, High about 9.1%
- Paseo is the top product by sales, at about 33M

## Notes

- 2013 has data only for Sep to Dec, so year-over-year comparison is meaningful only for those months
- Price columns (Sale Price, Manufacturing Price) are per-unit values and are not summed

## Repository Structure

```
Financial-Sales-Dashboard/
├── README.md
├── data/Financial_Sample.xlsx
├── dashboard/Financial_Sales_Dashboard.pbix
├── screenshots/
│   ├── page1_overview.png
│   └── page2_analysis.png
└── dax/measures.txt
```

## How to Use

1. Download `dashboard/Financial_Sales_Dashboard.pbix`
2. Open it in Power BI Desktop (free)
3. If prompted, point the data source to `data/Financial_Sample.xlsx`

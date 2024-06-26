## Temp


# Sales Analysis Dashboard


## Problem Statement

This Dashboard is a powerful tool designed to provide users with comprehensive insights into sales performance across various dimensions. With sections dedicated to home, period, segment, product, country, help, and export, users can easily navigate through different aspects of sales analysis. The dashboard features dynamic tooltips that provide contextual information when hovering over data points or visualizations, enhancing the user experience. With its customizable and interactive nature, the dashboard enables users to gain valuable insights into sales trends, customer behavior, product performance, and regional sales patterns. It is designed to be user-friendly and intuitive, making it easy for users to explore and analyze sales data effectively.



## Sections of dashboard

### Home
The Home page serves as the main hub for the dashboard, providing a high-level summary of key sales metrics such as total units sold, net sales, profit, and cost of goods. Users can quickly assess overall performance and identify areas that require further analysis.

<img width="618" alt="Home_SA" src="https://github.com/gouravjain77/PowerBI/assets/152005778/52c32f44-d5b8-42ed-a660-2ff29357ee90">

### Period
The Period page allows users to analyze sales performance over units sold, net sales, profit, COGs over different periods. Users can track sales trends, identify seasonality patterns, and compare performance across different periods.


<img width="616" alt="Period_SA" src="https://github.com/gouravjain77/PowerBI/assets/152005778/36adeb82-50ac-474e-8170-6faeac46ff2e">


### Segment
The Segment page categorizes sales data based on customer segments, over units sold, net sales, profit, and COGs. Users can analyze customer behavior, identify segment-specific trends, and tailor marketing strategies accordingly.


<img width="617" alt="Segment_SA" src="https://github.com/gouravjain77/PowerBI/assets/152005778/07f5e967-7406-4f90-9353-d070393c6da4">

### Country
The Country page allows users to analyze sales performance across different countries over units sold, net sales, profit, and COGs. Users can compare sales metrics, identify top-performing countries, and target international markets effectively.

<img width="617" alt="Country_SA" src="https://github.com/gouravjain77/PowerBI/assets/152005778/634c4964-601f-4a7d-bce2-333cc090f343">


### Product
The Product page provides insights into product performance, including top-selling products, product revenue, and profitability. Users can identify best-selling products, analyze product margins, and optimize product offerings.

<img width="617" alt="Product_SA" src="https://github.com/gouravjain77/PowerBI/assets/152005778/58906b2f-75f7-4eb4-9769-af6391af1226">

### Help
The Help page provides user-friendly guidance on how to navigate and utilize the dashboard effectively. Users can access tutorials, FAQs, and troubleshooting tips to enhance their experience.

<img width="617" alt="Help_SA" src="https://github.com/gouravjain77/PowerBI/assets/152005778/0ec60710-7c03-45ff-bfbd-39cc21818f26">

### Export
The Export page allows users to export sales data and reports as Excel Table. Users can customize the export settings and choose specific data to export, enabling seamless integration with other systems or tools.

<img width="496" alt="Export_SA" src="https://github.com/gouravjain77/PowerBI/assets/152005778/b4d06562-15eb-437a-ae40-33b131aa6cb9">

### Dynamic Tooltip
The dashboard features a dynamic tooltip that provides contextual information and insights when hovering over data points or visualizations, enhancing the user experience and making it easier to interpret the data. 

<img width="272" alt="Tooltip_SA" src="https://github.com/gouravjain77/PowerBI/assets/152005778/a3c38b7c-ab94-4849-9ac8-0b3f2edab23a">

### Drill Down Pages
The Drill Down pages allow users to drill down into specific data points or categories to get a more detailed view of sales performance. This helps in identifying underlying factors contributing to sales trends and making informed decisions.

<img width="500" alt="Drilldown_SA" src="https://github.com/gouravjain77/PowerBI/assets/152005778/37e65dd6-0d85-4427-aa36-4ba831d0ad4e">

### Measures Created :
- Date Selection = FORMAT(MIN(DIM_DATE[Reporting Period]),"MMM/YY")&" - "& FORMAT(MAX(DIM_DATE[Reporting Period]),"MMM/YY")
- Date/Time Last Refreshed = "Last Refreshed: "&FORMAT(VALUES(LAST_REFRESHED[Date Last Refreshed]),"mm.dd.yy")
- Units Sold = SUM(FACT_SALES[Units Sold])
- Units Sold CY = CALCULATE(SUM(FACT_SALES[Units Sold]),DIM_DATE[Year Rank]="1")
- Units Sold PY = CALCULATE([Units Sold],DIM_DATE[Year Rank]="2")
- Gross Sales = SUM(FACT_SALES[Gross Sales])
- Discounts = SUM(FACT_SALES[Discounts])
- Net Sales = SUM(FACT_SALES[Sales])
- Cost Of Goods = SUM(FACT_SALES[COGs])
- Profit = [Net Sales]-[Cost Of Goods]
- Profit CY = CALCULATE([Profit],DIM_DATE[Year Rank]="1")
- Profit PY = CALCULATE([Profit],DIM_DATE[Year Rank]="2")
- Profit YOY% = IFERROR(CALCULATE(([Profit CY]-([Profit PY])) / ABS([Profit PY]),ALL(DIM_DATE[Year])),1)
- Profit YOY% Formatted = "YOY: "&FORMAT([Profit YOY%],"00%")
- Profit Margin = IFERROR([Profit] / [Net Sales],0)
- Profit Margin Formatted = IF([Profit Margin]>0,"+"&FORMAT([Profit Margin],"0%"),FORMAT([Profit Margin],"0%"))
- 100% Minus Profit Margin = 1-[Profit Margin]
- Transparent = "RGBA(255,255,255,0)"
- All of Distinct Countries = DISTINCTCOUNT(FACT_SALES[Country])
- All of Distinct Segments = DISTINCTCOUNT(FACT_SALES[Segment])
- User Greeting = "Welcome " &SELECTEDVALUE(DIM_MANAGERS[First Name])&"!"
- Welcome_All = VAR Selected_User = SELECTEDVALUE(DIM_MANAGERS[Manager ID])RETURN IF(ISBLANK(Selected_User),"#fff","RGBA(255,255,255,0)")
- Discount Band Colors = VAR High = IF(SELECTEDVALUE('FACT_SALES'[Discount Band])="High",True,False)VAR Medium = IF(SELECTEDVALUE('FACT_SALES'[Discount Band])="Medium",True,False)VAR Low = IF(SELECTEDVALUE('FACT_SALES'[Discount Band])="Low",True,False)VAR None = IF(SELECTEDVALUE('FACT_SALES'[Discount Band])="None",True,False)RETURN SWITCH(TRUE(),High,"#e92f42",Medium,"#ffbe0b",Low,"#049570",None,"#808080","#07345F")



### Benefits
- Comprehensive Analysis: The dashboard offers a comprehensive view of sales performance across multiple dimensions, enabling users to gain a deeper understanding of their business.
- Actionable Insights: Users can identify trends, patterns, and opportunities for improvement, allowing them to make informed decisions and drive business growth.
- Customization: The dashboard is highly customizable, allowing users to tailor it to their specific needs and preferences.
- Ease of Use: The dashboard is user-friendly and intuitive, with interactive visuals and dynamic tooltips that make data exploration easy and efficient.
- Data Export: Users can export sales data and reports for further analysis or sharing with stakeholders, facilitating collaboration and data-driven decision-making.

### Conclusion
The Sales Analysis Dashboard is a powerful tool that provides actionable insights into sales performance, customer behavior, and product trends. It empowers managers and stakeholders to make informed decisions, optimize strategies, and drive business success.

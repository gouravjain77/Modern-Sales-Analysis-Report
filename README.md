# Sales Analysis Dashboard

### Dashboard Link : https://app.powerbi.com/groups/me/reports/384d017e-e935-44dc-9e7d-1626c1a36de1/ReportSection

## Problem Statement

This Dashboard is a powerful tool designed to provide users with comprehensive insights into sales performance across various dimensions. With sections dedicated to home, period, segment, product, country, help, and export, users can easily navigate through different aspects of sales analysis. The dashboard features dynamic tooltips that provide contextual information when hovering over data points or visualizations, enhancing the user experience. With its customizable and interactive nature, the dashboard enables users to gain valuable insights into sales trends, customer behavior, product performance, and regional sales patterns. It is designed to be user-friendly and intuitive, making it easy for users to explore and analyze sales data effectively.



## Sections of dashboard

### Home
The Home page serves as the main hub for the dashboard, providing a high-level summary of key sales metrics such as total units sold, net sales, profit, and cost of goods. Users can quickly assess overall performance and identify areas that require further analysis.

<img width="618" alt="Home_SA" src="https://github.com/gouravjain77/PowerBI/assets/152005778/52c32f44-d5b8-42ed-a660-2ff29357ee90">

### Period
The Period page allows users to analyze sales performance over different time periods, such as monthly, quarterly, or yearly. Users can track sales trends, identify seasonality patterns, and compare performance across different periods.

### Segment
The Segment page categorizes sales data based on customer segments, such as new customers, repeat customers, or high-value customers. Users can analyze customer behavior, identify segment-specific trends, and tailor marketing strategies accordingly.

### Country
The Country page allows users to analyze sales performance across different countries or regions. Users can compare sales metrics, identify top-performing countries, and target international markets effectively.

### Product
The Product page provides insights into product performance, including top-selling products, product revenue, and profitability. Users can identify best-selling products, analyze product margins, and optimize product offerings.

### Help
The Help page provides user-friendly guidance on how to navigate and utilize the dashboard effectively. Users can access tutorials, FAQs, and troubleshooting tips to enhance their experience.

### Export
The Export page allows users to export sales data and reports as Excel Table. Users can customize the export settings and choose specific data to export, enabling seamless integration with other systems or tools.

### Dynamic Tooltip
The dashboard features a dynamic tooltip that provides contextual information and insights when hovering over data points or visualizations, enhancing the user experience and making it easier to interpret the data. 

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

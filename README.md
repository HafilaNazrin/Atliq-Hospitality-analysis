# Atliq-Hospitality-analysis
Created a report in the Hospitality Domain using Key Metrics such as Revenue, RevPar, ADR, and Occupany%. A Table representing the key metrics of the Property including Realisation, Cancellation, and Average rating. Charts regarding the Online Platform.
Welcome to my blog on Developing reports with Power BI! Power BI is a powerful business intelligence tool by Microsoft that transforms data into visually appealing and insightful reports and dashboards. Whether you’re a business professional, data analyst, or someone curious about data visualization, this guide will help you take your first steps into the world of Power BI and unleash its full potential.

![Dashboard](https://github.com/user-attachments/assets/2c9ac6b2-bcc4-41c4-9569-924b8b947247)

Data analysis is a game-changer for optimizing business operations, empowering informed decisions and strategic planning. Recently, I worked on a project where I analyzed Hospitality data from Atliq Grand, designed an interactive dashboard, and visualized the insights using Power BI. In this article, I’ll walk you through my approach, from collecting the data to crafting the interactive dashboard.

## Objective
AtliQ Grands owns multiple five-star hotels across India and has been in the hospitality industry for the past twenty years. However, due to strategic moves from other competitors and ineffective management decision-making, AtliQ Grands is losing market share and revenue in the luxury/business hotels category. As a strategic move, the managing director of AtliQ Grands wanted to incorporate “Business and Data Intelligence” to regain their market share and revenue.

1. Create the metrics according to the metric list.
2. Create a dashboard according to the mock-up provided by stakeholders.
3. Create relevant insights not provided in the metric list/mock-up dashboard.

![mock up dashboard_atliq grands](https://github.com/user-attachments/assets/946dfb3b-baf8-44ef-89ee-1165ce5c9db9)

## Data Source
To get the Source data: Dataset

## Cleaning Data
The day type was created using the Calculated Column.

Day_Type = 
VAR _Weekday = WEEKDAY(dim_date[date])
RETURN IF(_Weekday> 5, "Weekend", "Weekday")

## DAX Calculation
Using Dax, Revenue, Total Bookings, Total Capacity and many more requested Metrics were calculated.

Revenue = SUM(fact_bookings[revenue_realized])

Week Over Week Change(WOW) was calculated using the formula,

Revenue WoW change % = 
var selv = IF(HASONEFILTER(dim_date[Week Num]),SELECTEDVALUE(dim_date[Week Num]),MAX(dim_date[Week Num]))
var revcw = CALCULATE([Revenue],dim_date[Week Num]=selv)
var revpw = CALCULATE([Revenue],FILTER(ALL(dim_date),dim_date[Week Num]=selv-1))

RETURN DIVIDE(revcw,revpw,0)-1

## Creating Dashboard
Created a Table to represent the Key Metrics and to indicate Revenue and Rating in each Area it was highlighted using Conditional Bars. Filter for Room Type, City and Months with Week were created.

![Property key metrics](https://github.com/user-attachments/assets/2877f64d-7b6c-4990-9a9c-7fd088a932bc)

Play cards stating the values of Revenue, RevPAR, Occupancy, ADR, DSRN and Realisation.

![Key Metrics](https://github.com/user-attachments/assets/cb8fe218-961a-4726-a2ad-ac9a979d3d87)

A tooltip with the trend line chart was added for the Play cards,

![Tooltip](https://github.com/user-attachments/assets/175a7677-ad3e-42a1-aad2-a7b3f389e986)

Line chart indicating the ADR, Occupancy, RevPAR and Bar Chart indicating Platform and Booking,

![Line Chart](https://github.com/user-attachments/assets/d6b875a4-4b67-43d7-a2ed-7cfb442900db)

Conclusion
1. Recommendation of Dynamic pricing regarding weekend and weekday

2. Bookings on other online platforms are more than our Website, to engage our customers in our Website we can make an offer on booking prices or provide extra vouchers.

3. Atliq Exortica in Hyderabad and Atliq Bay in Mumbai have low reviews where Level 2 and Level 3 Analysation can be done.

You can check my Dashboard, which I made using Power BI.

Thanks for reading, see my profile for more Data Analysis projects!

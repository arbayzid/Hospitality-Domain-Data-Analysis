# Hospitality-Domain-Data-Analysis
A data analysis project on hospitality domain using Power BI

![two-professionals-review-notes-laptop-creating-buisness-meeting-lounge-area-luxury-hotel-international-representatives-attend-important-conference-share-experiences](https://github.com/arbayzid/Hospitality-Domain-Data-Analysis/assets/146184500/476e066a-4f9d-4b27-829d-af78d250fe55)
📊𝐋𝐢𝐯𝐞 𝐃𝐚𝐬𝐡𝐛𝐨𝐚𝐫𝐝: [Hospitality Analysis](https://www.novypro.com/project/hospitality-analysis-power-bi-5)

## Project Title:
Provide Insights to the Revenue Team in the Hospitality Domain
## Project Overview:
This project aimed to conduct a comprehensive analysis of business performance for AtliQ Grands over the past 3 months, with the aim of identifying trends, and factors influencing revenue generation. By analyzing various aspects of Atliq Grands's operations, including revenue generation, occupancy trends, customer booking behavior, and service quality, the project sought to provide actionable insights to drive strategic decision-making on revenue management for the company.
## Business Problem:
AtliQ Grands, a leading hospitality company, owns multiple five-star hotels across India. They have been in the hospitality industry for the past 20 years. Due to strategic moves from other competitors and ineffective decision-making in management, AtliQ Grands are losing its market share and revenue in the luxury/business hotels category.

## Project Objective:
The primary objective of this data analysis project is to help AtliQ Grands regain its market share and revenue in the luxury/business hotels category by incorporating business and data intelligence into their revenue management strategies. This involves analyzing historical data and providing actionable insights to the revenue team.
## Project Scope:
- Gather historical data on relevant metrics.
- Analysis of historical data related to revenue, occupancy rates, booking patterns.
- Development of key performance metrics aligned with revenue management objectives.
- Creation of a user-friendly dashboard that visualizes important metrics and provides a comprehensive overview of the revenue management performance.
-	Generation of actionable insights and recommendations to the revenue team based on data analysis findings.
-	Documentation of the data analysis process, findings, and recommendations.
## Data Collection:
The dataset, sourced from codebasics.io, consists of five CSV files, each containing a separate table.
-	dim_date: Provides meta-information regarding dates, including month, week number, and day type (e.g., weekday or weekend).
-	dim_hotels: Contains essential metadata about hotel properties, such as property ID, property name, category (e.g., Luxury, Business), and city.
-	dim_rooms: Information about room types, including room ID and class. 
-	fact_aggregated_bookings: Aggregated booking data, including property ID, check-in date, room category, successful bookings, and capacity.
-	fact_bookings: Detailed booking data, including booking ID, property ID, booking date, check-in/out dates, number of guests, room category, booking platform, ratings given, booking status, revenue generated, and revenue realized.
## Data Preparation and Modeling:
All data was loaded into Power BI and extensively inspected to ensure quality and integrity. This inspection included checks for missing values, significant outliers, correct data types, and proper formatting. Subsequently, relationships between the tables were established for effective data modeling.
![Screenshot 2024-03-01 153457](https://github.com/arbayzid/Hospitality-Domain-Data-Analysis/assets/146184500/665d041e-afc3-488e-ab45-7ea11996e5c5)
## Data Analysis:
Some of the key measures created for in depth analysis has been listed below:  \
**Total Revenue:**
```
Revenue = SUM(fact_bookings[revenue_realized])
```
**Revenue Current Week:**
```
Revenue CW = 
VAR WeekNumber =
    IF (
        HASONEFILTER ( dim_date[wn] ),
        SELECTEDVALUE ( dim_date[wn] ),
        MAX ( dim_date[wn] )
    )
RETURN
    CALCULATE ( [Revenue], dim_date[wn] = WeekNumber )
```
**Revenue Previous Week:**
```
Revenue PW = 
VAR WeekNumber =
    IF (
        HASONEFILTER ( dim_date[wn] ),
        SELECTEDVALUE ( dim_date[wn] ),
        MAX ( dim_date[wn] )
    )
RETURN
    CALCULATE (
        [Revenue],
        FILTER ( ALL ( dim_date ), dim_date[wn] = WeekNumber - 1 )
    )
```
**Revenue Week-on-Week growth:**
```
Revenue WoW Growth = 
DIVIDE ( [Revenue CW] - [Revenue PW], [Revenue PW], 0 )
```
**Dynamic Color for Revenue Week-on-Week growth:**
```
Color Revenue Wow Growth = 
    IF([Revenue WoW Growth] > 0, "green",
        IF([Revenue WoW Growth] < 0, "red", "gray"))
```
**Occupancy Rate:**
```
Occupancy Rate = DIVIDE([Checked Out Bookings], [Total Capacity],0)
```
**Realisation Rate:**
```
Realisation Rate = DIVIDE([Checked Out Bookings], [Bookings],0)
```
**Revenue Per Available Room:**
```
RevPAR = DIVIDE([Revenue], [Total Capacity], 0)
```
**Average Daily Rate:**
```
ADR = DIVIDE([Revenue], [Bookings], 0)
```

## Dashboard Design and Development:
Design and mock-up of a user-friendly dashboard have been developed using Figma to incorporate relevant metrics and visualizations, providing a comprehensive overview of revenue management performance.

**Dashboard Mock-up:**
![Screenshot 2024-03-01 160410](https://github.com/arbayzid/Hospitality-Domain-Data-Analysis/assets/146184500/8f3e5a3c-de70-4d77-87e7-0304e6070a00)

The dashboard comprises the following components:

**Key Performance Indicators (KPI):**\
The dashboard showcases crucial KPIs such as Total Revenue, Occupancy Rate, Average Rating, Realisation Rate, RevPAR, ADR, Total Bookings, and ALOS for the specified time period, as well as for the last week. Additionally, it displays the week-on-week growth of these top level KPIs.

**Charts:**
- City and Room Analytics: Three dynamic bar charts have been incorporated to show revenue, occupancy rate, and average rating by city. Similarly, for room analytics, three dynamic bar charts have been included to show revenue, occupancy rate, and average rating by room class.
- Competitive Analysis: Weekday and weekend comparisons have been included to show Revenue, Ratings, Bookings, Occupancy Rate, and Realization Rate.
- Booking Platforms: A column chart showing total bookings and cancelled bookings using various booking platforms has been developed.
- Weekly Trends: A line and clustered column chart has been created to illustrate weekly trends of KPIs such as RevPAR, ADR, and Occupancy Rate.
- Weekday and Weekend Trends: Three separate line charts have been developed to show weekday and weekend trends of RevPAR, ADR, and Occupancy Rate.

**Filters:**\
Some user-friendly filters have been added, enabling customization based on City, Category, Room Class, Property, Booking Platform, Month, and Week, as well as allowing stakeholders to focus on specific segments of interest. These filters enhance the dashboard’s usability and facilitate tailored insights. Additionally, a button has been incorporated to conveniently clear all filters.

📊𝐋𝐢𝐯𝐞 𝐃𝐚𝐬𝐡𝐛𝐨𝐚𝐫𝐝: [Hospitality Analysis](https://www.novypro.com/project/hospitality-analysis-power-bi-5)

## Key Insights:
Here are some important insights from the Dashboard:

- KPIs - Total Revenue, Occupancy Rate, Average Rating, Realization Rate, RevPAR, ADR, Total Bookings, and ALOS provide a snapshot of the business’s overall performance.
-	Mumbai is the top-performing city in terms of revenue, followed by Bangalore, Hyderabad, and Delhi.
-	Bangalore is the second-highest revenue-generating city, despite having the lowest occupancy rate and rating.
-	Delhi tops both in occupancy and rating, followed by Hyderabad, Mumbai, and Bangalore.
-	The room class "Elite" generates the highest revenue, followed by "Premium," "Presidential," and "Standard."
-	"Premium" room class ranks 2nd in revenue generation, although it has the lowest occupancy rate and low rating.
-	The weekday occupancy rate is significantly lower (35.9%) compared to weekends (51.9%). Notably, rating and realization rate remain quite similar across both weekdays and weekends.
-	While RevPAR and ADR remain consistent across weeks, the occupancy rate fluctuates considerably.
-	Occupancy rate and RevPAR follow similar trends on weekdays and weekends, while ADR shows no consistent pattern.
-	"Make your trip" and "log trip" are the top two booking platforms.


## Recommendations:
Based on the insights gained from the analysis, the following recommendations are proposed:
-	Prioritize the city of Mumbai and the "Elite" room class due to their significant impact on revenue generation.
-	Take initiatives and implement strategies to increase the average rating and, thus, the occupancy rate for the city Bangalore and the "Premium" room class.
- Implement a dynamic pricing strategy by increasing room rates for shorter stays and offering attractive deals for longer stays to optimize revenue based on length of stay variations.
- Invest in marketing and promotional campaigns to maximize revenue during high-demand periods.
- Implement targeted marketing strategies to attract guests during weekdays and off-peak seasons, aiming to improve occupancy rates during these periods.
- Optimize pricing strategies based on demand fluctuations and competitor analysis to maximize revenue generation.
- Prioritize enhancing customer experience and satisfaction at properties with lower average ratings. Address any underlying issues impacting guest satisfaction.
- Strengthen relationships with MakeMyTrip and LogTrip platforms, while also diversifying distribution channels and establishing partnerships with additional platforms. This will reduce reliance on specific booking platforms and increase reach to a wider audience.

## Conclusion:
By leveraging data analysis and business intelligence, AtliQ Grands aims to enhance its revenue management capabilities, drive revenue growth, and regain market share in the competitive hospitality industry. This project will empower the revenue team with actionable insights and strategic recommendations, enabling informed decision-making and sustainable business success.

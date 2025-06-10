# 🏨 Hotel Booking Analysis Dashboard – Elevate Resort

Elevate resorts is a leading global hospitality brand, renowned for its wide range of accommodations and unparalleled guest experience.\
Elevate resorts has noticed a stagnation in its revenue growth over the past couple of years. The elevate resorts is new to the world of extracting insights of the data, but they have taken their first step by collecting booking data for the last couple of years across their properties.\
The management wants us to analyze the data to find some insights which can help them in coming out with strategies to improve the growth in revenue.


## 🧾 Dataset Overview

The datasets provided by management contains detailed records of hotel bookings and geographical data including:

- **Booking info:** Dates, length of stay, adults/children, cancellation status
- **Financial:** ADR (average daily rate), deposit type
- **Customer segments:** Market segment, customer type, assigned room, agent
- **Special requests**, **Country info** and many more data points.

You can view the full data dictionary


## 📌 Problem Statements

Elevate Resort’s management team has posed several key questions:

1. **When do we receive the most bookings, and how do cancellations trend over time?**
2. **Which countries are driving the highest number of bookings?**
3. **What is the revenue breakdown across different market segments and customer types?**
4. **How do lead time and payment modes affect cancellation patterns?**
5. **What are our overall KPIs — total bookings, cancellations, revenue, and revenue lost?**





## 📊 Power BI Dashboard Features

The dashboard includes:

- **KPI Cards** showing:
  - Total bookings
  - Total cancellations
  - Total revenue
  - Total revenue lost
- **Trend Line Chart** for monthly bookings and cancellations
- **Top 10 Country Analysis** by total bookings
- **Revenue Analysis**:
  - By Market Segment
  - By Customer Type
- **Cancellation Analysis**:
  - By Lead Time (Scatter plot)
  - By Deposit Type (Clustered bar chart)

All visuals are dynamic and respond to:
- Date range slicers  
- Country filters

---

## 💡 Key Insights

- **August** was the month with the highest bookings.
- **Portugal** and **United Kingdom** were the top contributors to bookings.
- **Online TA (Travel Agencies)** brought in the highest revenue among market segments.
- **Transient customers** contributed the majority share of total revenue.
- Bookings with longer lead times showed a higher tendency to cancel.
- Most cancellations came from bookings with **No Deposit**, implying a potential revenue leak.

---

## 🛠 DAX Measures Used

Some key DAX formulas created:

```DAX
-- Total Real Revenue
Real_Revenue = 
IF(
    OR(hotel_bookings[deposit_type] = "Non Refund", hotel_bookings[is_cancelled] = 0),
    hotel_bookings[adr] * (hotel_bookings[stays_in_week_nights] + hotel_bookings[stays_in_weekend_nights]),
    0
)

-- Revenue Lost from Cancellations
Revenue_Lost = 
IF(
    AND(hotel_bookings[deposit_type] <> "Non Refund", hotel_bookings[is_cancelled] = 1),
    hotel_bookings[adr] * (hotel_bookings[stays_in_week_nights] + hotel_bookings[stays_in_weekend_nights]) * -1,
    BLANK()
)
```
## 🧠 Tools Used
- Power BI for data modeling, visualization, and interactivity

- DAX for custom calculations

- Excel (for initial dataset understanding & eyeballing)

I designed this data and dashboard to simulate a real-world business scenario and solve practical problems using data. I aimed to balance performance metrics, storytelling, and visual clarity.

Feel free to explore, give feedbacks, or suggest improvements!

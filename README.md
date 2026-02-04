# 🏨 Hotel Booking Data Analysis

So earlier this month, I bought another Udemy course 'Data Analysis Real world use-cases- Hands on Python' by Shan Singh. After completing it and learning some insigthul analyses, I had some ideas of how to get some more interesting insights from this dataset. So, I did a couple of extra analyses, which is what this repository is about. For the sake of completness, I included the analyses of origin of customers as part of the exploratory analysis.

This project explores hotel booking data to uncover insights about **guest origins,room allocation, market segments and room types, guest origins, and seasonality** in order to answer key business questions relevant to the hospitality industry.

---

## 📂 Dataset

* **Dataset:** Hotel Booking Dataset (CSV) with ~119,000 bookings
* **Features:** Booking dates, room types, guests, market segments, cancellations, country of origin, pricing, and more.
* **Hotels:** Resort Hotel & City Hotel (analyzed together)
  
---

## 🛠️ Python Tools & Libraries

* **pandas** 
* **matplotlib** 
* **seaborn**
* **plotly (for interactive plots!)**
* **Jupyter Notebook**

---

## 🧹 Data Cleaning Steps

* Removed invalid rows where number of adults, children, and babies guests were all zero
* Removed duplicate records
* Concatenated fields to create new arrival date column with style YYYY-MM-DD
* Cleaned market segment labels for readability (e.g. 'Offline Travel Agent / Tour Operator' instead of 'Offline TA/TO')

Note: I have decided to include the cancelled bookings as I am interested in intention of guests making a booking in the hotel, regardless of whether they cancelled the booking due to various personal reasons.

---

## 📊 Analyses & Insights

### 1️⃣ Guest Origin Spatial Analysis 🌍

One analysis from the Udemy course that I have decided to keep for this repository is the guest origin heatmap, as I could not think of a better way to visualise the guest number from each country than using a world heatmap!

Here are the simple steps:
* Aggregated guests by country, remember to use `.reset_index()` to create an extra index column!
<img width="291" height="418" alt="Screenshot 2026-02-04 at 12 02 55 PM" src="https://github.com/user-attachments/assets/002b6a23-3666-4212-b078-62a44390ea75" />

* Displayed results on an **interactive world choropleth map**

<img width="1165" height="311" alt="Screenshot 2026-02-02 at 2 05 50 PM" src="https://github.com/user-attachments/assets/8709c2a0-8410-457f-9ef4-7238d0c55865" />

### Inference: Portugal, the UK, France, Spain, and Germany are the top guest origin countries. Seem that our hotel is very appealing to European holiday maker!

### 2️⃣ Room Type booking and Allocation

Since there are a number of room types in the hotels, I am interested in the preference of guests for each room type, as well as how likely it is for them to get what they reserved.

The key for this analysis is to create a new column to show, for each room type,  how many bookings were assigned the same room as the reserevd one. 

<img width="440" height="348" alt="Screenshot 2026-02-04 at 12 06 50 PM" src="https://github.com/user-attachments/assets/3ca569a3-8ee4-4edb-b146-9904d515f920" />

Then visualise:

<img width="1253" height="368" alt="Screenshot 2026-02-02 at 3 01 23 PM" src="https://github.com/user-attachments/assets/24d465a5-42b1-414a-bb44-4557de090d80" />

📌 *Inference: Most guests were assigned the same room type they booked, though some room types show higher reassignment rates. Room type A has a lower assignment rate among other room type (except room type L for the low booking number), probably due to the very high number of booking it received*

Note: I think we would have a better picture if we have the total number of available rooms for each room type, as it could really influence the assignment rate!

---

### 3️⃣ Seasonality in Guest Arrivals. 

Usually, people like to make holiday during summer time, let's see if it shows in our data too!

Since we do not have a column that contain full arrival date information (we only have 'arrival_date_year', 'arrival_date_month', 'arrival_date_week_number' and 'arrival_date_day_of_month'). We have to construct it ourselves.

First, we convert the month information from it english name form to arabic number form using a dictionary, and use it as a new column 'arrival_date_month_index':

`dict_month = {'July':7, 'August':8, 'September':9, 'October':10, 'November':11, 'December':12,
       'January':1, 'February':2, 'March':3, 'April':4, 'May':5, 'June':6}`

Then, we concatenate relevant columns to get a date column in form of YYYY-MM-DD

<img width="761" height="113" alt="Screenshot 2026-02-04 at 2 06 19 PM" src="https://github.com/user-attachments/assets/1f0b28e0-dab3-4ea0-b78c-fb814adf7f0a" />

In the Udemy course, seasonality of all room types combined was analysed. Some seasonality was observed with higher arrivals in summer time compared to winter time. Can we see the same sesonality at the level of room type? I repeated the same analysis but only focusing on the most popular room tyoe, i.e. roomm type A and D.

<img width="1054" height="391" alt="Screenshot 2026-02-02 at 4 25 42 PM" src="https://github.com/user-attachments/assets/4ae1ce1e-4957-400d-b2d2-9a91edf719f2" />

📆 *Inference: Clear seasonality observed in room type D between 2016-2017: higher guest numbers in summer, lower in winter—especially noticeable between 2016–2017.*

---

### 4️⃣ Market Segment Distribution: Who Were Booking Our Hotel?

For a change, I have decided to visualise the booking proportions across market segments using treemap instead of the traditional pie chart.

<img width="924" height="293" alt="Screenshot 2026-02-04 at 2 13 25 PM" src="https://github.com/user-attachments/assets/ef09ac51-3bb7-4680-bcaa-0f278a2a5584" />


(Visualized using an interactive **Plotly pie chart**.)

📈 *Inference: Online Travel Agencies dominate hotel bookings.*

---

### Market segment and Reserved Room Type 

My next queestion would be, since we have a couple of room types and market segments, does certain market segment tend to reserve certain room type? We can look at the data from two different perspectives:

1) Given a reserved room type, what is the booking proportion across different market segment?

<img width="1098" height="650" alt="Screenshot 2026-02-04 at 2 23 02 PM" src="https://github.com/user-attachments/assets/33c0a308-74d8-489b-a282-a7afd9bcfe47" />

2) Given a market segment, what is the boooking proportion across room types?

<img width="1030" height="597" alt="Screenshot 2026-02-04 at 2 34 08 PM" src="https://github.com/user-attachments/assets/9addc2ec-bb98-41fb-9089-798e9b9d3a70" />

Both of looked informative. However, I am interested in the intention/peference of the market segment, at the end day it is the market who choose the room, not the other way round! **I would choose the second figure.**

📈 *Inference: Based on the second figure, all known market segments tend to reserve room type A, which explains the highest room type A reservation among all room types.*

---

### Revenue hotspot : Which combination of reserved room type and market segment generates the most revenue per booking?

To answer this question, I computed the average daily rate (ADR) in combinations of reserved room type and market segment, and put them in form of a pivot table.

<img width="646" height="442" alt="Screenshot 2026-02-04 at 2 56 39 PM" src="https://github.com/user-attachments/assets/9f3e9ee2-8e07-47e5-9dfc-92b2a60ad4f9" />

Then, visualise this pivot table as a heatmap.

<img width="1017" height="640" alt="Screenshot 2026-02-04 at 2 58 25 PM" src="https://github.com/user-attachments/assets/6a978afa-bc6c-4056-a7e0-806a99c6d38a" />

📈 *Inference: According to the heatmap, the hotspots of revenue mainly come from Room G, H with market segment Direct booking, Offline Travel Agent/Tour Operator and Online Travel Agent, as well as room F with Online Travel Agent.*

---

## 💡 Key Takeaways

* Room reassignment exists but is relatively limited
* Online channels are the primary booking source
* Guest arrivals show strong geographic concentration
* Seasonal patterns are significant and consistent

---

## ✨ Future Improvements

* Separate analysis by hotel type (Resort vs City)
* Excluding cancelled booking for comparison
* Weekly / monthly aggregation for smoother seasonality trends


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

📌 *Most guests were assigned the same room type they booked, though some room types show higher reassignment rates. Room type A has a lower assignment rate among other room type (except room type L for the low booking number), probably due to the very high number of booking it received*

Note: I think we would have a better picture if we have the total number of available rooms for each room type, as it could really influence the assignment rate!

---

###  Market Segment Distribution

Analyzed booking proportions across market segments:

* Online Travel Agencies
* Offline Travel Agents / Tour Operators
* Direct bookings
* Corporate & Group bookings

📈 *Online Travel Agencies dominate hotel bookings.*
<img width="1187" height="352" alt="Screenshot 2026-02-02 at 2 05 31 PM" src="https://github.com/user-attachments/assets/74e974e4-a1b8-429e-abd2-edca6b9534d1" />

(Visualized using an interactive **Plotly pie chart**.)

3️⃣
---


---

### 4️⃣ Seasonality in Guest Arrivals

* Constructed a full arrival date from year, month, and day
* Analyzed total guests over time
* Overall observation as well as selected analyses on most popular room types (e.g., A & D)

<img width="1128" height="648" alt="Screenshot 2026-02-03 at 7 08 23 PM" src="https://github.com/user-attachments/assets/b4df1007-b679-4b1a-b780-929bf94bc41f" />

<img width="1054" height="391" alt="Screenshot 2026-02-02 at 4 25 42 PM" src="https://github.com/user-attachments/assets/4ae1ce1e-4957-400d-b2d2-9a91edf719f2" />

📆 *Clear seasonality observed in room type D between 2016-2017: higher guest numbers in summer, lower in winter—especially noticeable between 2016–2017.*

---

## 📁 Repository Structure

```text
├── hotel_bookings_analysis.ipynb
├── hotel_bookings.csv
└── README.md
```

---

## ▶️ How to Run the Notebook

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/hotel-booking-analysis.git
   ```
2. Install dependencies:

   ```bash
   pip install pandas matplotlib seaborn plotly chart-studio
   ```
3. Open the notebook:

   ```bash
   jupyter notebook
   ```

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


# 🏨 Hotel Booking Data Analysis

## 📌 Project Overview

This project explores hotel booking data to uncover insights about **room allocation, market segments, guest origins, and seasonality**.
Using Python and popular data analysis libraries, the notebook performs data cleaning, exploratory data analysis (EDA), and visualization to answer key business questions relevant to the hospitality industry.

---

## 📂 Dataset

* **Source:** Hotel Booking Dataset (CSV)
* **File:** `hotel_bookings.csv`
* **Records:** ~119,000 bookings
* **Hotels:** Resort Hotel & City Hotel (analyzed together)
* **Features:** Booking dates, room types, guests, market segments, cancellations, country of origin, pricing, and more.

---

## 🛠️ Tools & Libraries

* **Python**
* **pandas** – data cleaning & manipulation
* **matplotlib / seaborn** – static visualizations
* **plotly** – interactive charts & maps
* **Jupyter Notebook**

---

## 🧹 Data Cleaning Steps

* Removed invalid rows where adults, children, and babies were all zero

* Removed duplicate records

* Created engineered features:

  * same_room → whether assigned room matches reserved room

  * Total_guests → adults + children + babies

  * arrival_date → combined date field

* Cleaned market segment labels for readability

---

## 📊 Key Analyses & Insights

### 1️⃣ Room Type Booking & Allocation

* Counted bookings by **reserved room type**
* Compared **reserved vs assigned rooms**
* Visualized:

  * Total bookings per room type
  * Percentage of guests assigned the same room vs reassigned
<img width="1253" height="368" alt="Screenshot 2026-02-02 at 3 01 23 PM" src="https://github.com/user-attachments/assets/24d465a5-42b1-414a-bb44-4557de090d80" />

📌 *Most guests were assigned the same room type they booked, though some room types show higher reassignment rates.*


---

### 2️⃣ Market Segment Distribution

Analyzed booking proportions across market segments:

* Online Travel Agencies
* Offline Travel Agents / Tour Operators
* Direct bookings
* Corporate & Group bookings

📈 *Online Travel Agencies dominate hotel bookings.*
<img width="1187" height="352" alt="Screenshot 2026-02-02 at 2 05 31 PM" src="https://github.com/user-attachments/assets/74e974e4-a1b8-429e-abd2-edca6b9534d1" />

(Visualized using an interactive **Plotly pie chart**.)

---

### 3️⃣ Spatial Analysis: Guest Origins

* Analyzed **non-cancelled bookings only**
* Aggregated guests by country
* Displayed results on an **interactive world choropleth map**

🌍 *Portugal, the UK, France, Spain, and Germany are the top guest origin countries.*
<img width="1165" height="311" alt="Screenshot 2026-02-02 at 2 05 50 PM" src="https://github.com/user-attachments/assets/8709c2a0-8410-457f-9ef4-7238d0c55865" />

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
* Cancellation prediction modeling
* Revenue and ADR trend analysis
* Weekly / monthly aggregation for smoother seasonality trends


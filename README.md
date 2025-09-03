# Hotel Booking Cancellation – Data Preprocessing Project

This project prepares a raw **hotel bookings dataset** for machine learning.  
The business goal is to help the revenue team reduce losses from last-minute cancellations by ensuring the dataset is clean and model-ready.  
The focus here is **data preprocessing and data cleaning **, not final model training.

---
 📂 Repository Contents
- `hotel_booking_preprocessing.ipynb` → google Colab notebook with all preprocessing steps.
- `hotel_bookings.csv` → the dataset which is used .
- `README.md` → Project documentation (this file).

---

Preprocessing Steps
1. **Data Exploration**
   - Loaded dataset, generated summary statistics (`.info()`, `.describe()`,others which describe the data ).
   - Visualized missing values using heatmaps and missingno.

2. **Data Cleaning**
   - Missing values:
     - `agent`, `company` → filled with 0.
     - `country` → imputed with mode.
     - `children` → imputed with median.
   - Dropped duplicate rows.
   - Outliers:
     - Capped `adr` values above 1000 to 1000.
   - Fixed data types (dates formatted correctly).

3. **Feature Engineering**
   - `total_guests = adults + children + babies`
   - `total_nights = stays_in_weekend_nights + stays_in_week_nights`
   - `is_family = 1 if (children + babies > 0) else 0`

4. **Encoding**
   - One-hot encoding for low-cardinality features (`meal`, `market_segment`).
   - Frequency encoding for `country` (high-cardinality).
   - Dropped leakage columns (`reservation_status`, `reservation_status_date`).

5. **Final Step**
   - Split into training (80%) and testing (20%) sets.

---

Key Findings
- `agent` and `company` had heavy missingness (mostly zero in real-world).
- `adr` had extreme outliers (>5000) that could distort models.
- Several duplicate rows were found and removed.
- After cleaning, the dataset is balanced and ML-ready.

---

🚀 Next Steps
- Apply classification models (Logistic Regression, Random Forest, XGBoost).
- Compare performance on the cleaned dataset.

---

🛠️ Tools used in the notebook & Libraries
- Python (Pandas, NumPy, Matplotlib, Seaborn, Missingno, Scikit-learn)
- Google Colab

# Hotel Booking Cancellations – Data Preprocessing Project

## 📌 Project Objective

The goal of this project is to build a **robust data preprocessing pipeline** for hotel booking cancellation prediction.  
Last-minute cancellations significantly impact hotel revenue, and the quality of preprocessing will determine the future model’s success.

This project **focuses only on data preparation and cleaning**, not on building the final ML model.

---

## 📂 Dataset

- Source: `hotel_bookings.csv` (from the hotel’s PMS system)
- Size: ~119k rows, 32 columns
- Target Variable: `is_canceled`

---

## 🔎 Phase 1: Exploratory Data Analysis (EDA)

- Generated summary statistics with `.describe()` and `.info()`
- Checked missing values (`df.isna().sum()`)
- Visualized missing data (using `missingno` / seaborn heatmap)
- Detected outliers in numerical columns using IQR method and Visualize Box plot , Histograme plot
- Key Data Quality Issues:
  - Missing values in `company`, `agent`, `children`, `country`
  - Outliers in many columns
  - Duplicate rows

---

## 🛠 Phase 2: Data Cleaning

1. **Missing Values**
   - `company` & `agent` → filled with `0`
   - `country` → filled with mode (most frequent country)
   - `children` → imputed with median
2. **Duplicates**
   - Removed exact duplicate rows
3. **Outliers**
   - Applied capping (values which are less than lower bound repalce it with lower_bound value , values are greater than upper bound replace it with upper_bound value)
4. **Data Types**
   - Converted date columns into proper `datetime` format , `is_canceled` to int type
5. **Feature Engineering**
   - `total_guests = adults + children + babies`
   - `total_nights = stays_in_weekend_nights + stays_in_week_nights`
   - `is_family` = 1 if children or babies > 0, else 0
6. **Encoding**
   - One-Hot Encoding for categorical low-cardinality(less than or equal 12) variables (`meal`, `market_segment`) , showing count plot visualization 
   - Frequency Encoding for high-cardinality (`country`)
7. **Splitting Data**
   - split Data to X , Y(target `is_canceled`)
   - split X, y to x_train , x_test , y_train ,y_test

---

## 📊 Tools & Libraries

- Python 3.x
- Pandas, NumPy
- Matplotlib, Seaborn, Missingno
- Scikit-learn (for preprocessing ,splitting data)

---


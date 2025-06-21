# internship-at-skillytixs
# 🧼 Marketing Campaign Data Cleaning

This repository contains the cleaned version of the raw marketing campaign dataset, along with a Jupyter Notebook demonstrating the full data cleaning process using **Pandas** in **Python**.

---

## 📂 Files Included

- `marketing_campaign.csv` – Raw dataset (tab-separated)
- `cleaned_marketing_campaign.csv` – Final cleaned dataset
- `data_cleaning.ipynb` – Jupyter Notebook with all cleaning steps
- `README.md` – Documentation of the cleaning process

---

## 🧠 Objective

The goal was to **clean and prepare** the dataset by:
- Handling missing values
- Removing duplicate records
- Standardizing inconsistent data formats (e.g., dates, categories)
- Preparing the data for further analysis or modeling

---

## 🔧 Data Cleaning Process (Step-by-Step)

### 1. **Load Dataset**
Loaded the dataset using `pandas.read_csv()` with `sep='\t'` since it was tab-separated.

---

### 2. **Initial Data Inspection**
- Checked data types, null counts, and column names using `df.info()` and `df.head()`.
- Observed missing values in the `Income` column and string-format dates in `Dt_Customer`.

---

### 3. **Remove Duplicates**
- Checked using `df.duplicated().sum()` → No duplicates found.
- Still used `df.drop_duplicates()` to ensure cleanliness.

---

### 4. **Handle Missing Values**
- **Column affected**: `Income`
- Filled missing values using the **median** (₹51,381.5) to avoid distortion from outliers:
  ```python
  df['Income'] = df['Income'].fillna(df['Income'].median())

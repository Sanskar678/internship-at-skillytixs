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
  
### 5. **Standardize Date Format**
Converted Dt_Customer from string to datetime object:

python
Copy
Edit
df['Dt_Customer'] = pd.to_datetime(df['Dt_Customer'], format='%d-%m-%Y')

### 6. **Clean Categorical Variables**
Standardized text format (removed spaces, fixed capitalization) in:

Education

Marital_Status

python
Copy
Edit
df['Education'] = df['Education'].str.strip().str.title()
df['Marital_Status'] = df['Marital_Status'].str.strip().str.title()

### 7. **Export Cleaned Dataset**
Saved the cleaned DataFrame to a CSV file:

python
Copy
Edit
df.to_csv("cleaned_marketing_campaign.csv", index=False)

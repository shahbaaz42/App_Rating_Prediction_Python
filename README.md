# App_Rating_Prediction_Python
App Rating Prediction using Linear Regression  

Course-end Project 1  

## 📌 Problem Statement  
The Google Play Store team is about to launch a new feature wherein certain promising apps will be boosted in visibility. This boost will manifest in multiple ways, including higher priority in recommendations sections (“Similar apps”, “You might also like”, “New and updated games”), and higher ranking in search results.  

This feature will help bring more attention to newer apps that have the potential to succeed.  

**Objective:**  
The task is to predict app ratings based on available features so that Google can identify which apps are good candidates for promotion.  

---

## 📊 Dataset  
**File Used:** `googleplaystore.csv`  

**Fields in the data:**  
- **App**: Application name  
- **Category**: Category to which the app belongs  
- **Rating**: Overall user rating of the app  
- **Reviews**: Number of user reviews for the app  
- **Size**: Size of the app  
- **Installs**: Number of user downloads/installs for the app  
- **Type**: Paid or Free  
- **Price**: Price of the app  
- **Content Rating**: Age group the app is targeted at - Children / Mature 21+ / Adult  
- **Genres**: An app can belong to multiple genres (apart from its main category).  
- **Last Updated**: Date when the app was last updated on Play Store  
- **Current Ver**: Current version of the app available on Play Store  
- **Android Ver**: Minimum required Android version  

---

## 📝 Steps to Perform  

### Step 1: Load the Data  
- Load the dataset `googleplaystore.csv` using pandas.  

### Step 2: Check for Null Values  
- Identify missing values.  
- Count null values per column.  
- Drop rows with missing data.  

### Step 3: Data Type Fixes & Cleaning  
- Convert `Size` into numeric (Kb → Mb conversion).  
- Convert `Reviews` to numeric.  
- Clean `Installs` (remove `+` and `,`) and convert to integer.  
- Clean `Price` (remove `$`) and convert to numeric.  

### Step 4: Sanity Checks  
- Keep ratings only between **1 and 5**.  
- Ensure reviews ≤ installs.  
- For free apps (`Type = Free`), price must be `0`.  

### Step 5: Univariate Analysis  
- Boxplot for **Price** → Detect high outliers.  
- Boxplot for **Reviews** → Check extremely high counts.  
- Histogram for **Rating** → See rating distribution.  
- Histogram for **Size** → Distribution of app sizes.  

### Step 6: Outlier Treatment  
- Remove apps with suspiciously high prices.  
- Drop apps with more than **2M reviews**.  
- Handle outliers in **Installs** using percentile thresholds.  

### Step 7: Bivariate Analysis  
- Scatter plots: Rating vs Price, Size, Reviews.  
- Boxplots: Rating vs Content Rating, Rating vs Category.  
- Interpret relationships and patterns.  

### Step 8: Data Preprocessing  
- Apply log transformation (`np.log1p`) to `Reviews` & `Installs`.  
- Drop unused columns: `App`, `Last Updated`, `Current Ver`, `Android Ver`.  
- Convert categorical variables (`Category`, `Genres`, `Content Rating`, `Type`) into dummy variables.  

### Step 9: Train-Test Split  
- Perform 70-30 split into `df_train` and `df_test`.  

### Step 10: Feature & Target Separation  
- Create `X_train`, `y_train`, `X_test`, and `y_test`.  

### Step 11: Model Building  
- Train **Linear Regression** model.  
- Report **R² score** on the training set.  

### Step 12: Model Evaluation  
- Make predictions on the **test set**.  
- Report **R² score** on test data.  
- Interpret results.  

---

## 📈 Results  
- **R² on Training Set**: ~0.1662  
- **R² on Test Set**: ~0.1295  

The model explains only a small portion of the variance in ratings, showing that additional features or advanced models may be required for better prediction.  

---

## 🚀 Conclusion  
- Data cleaning and preprocessing are essential before modeling.  
- Linear regression provides baseline performance but may not be sufficient for complex patterns.  
- This project demonstrates end-to-end **data preprocessing, visualization, and regression modeling** on real-world app store data.  

---

## 📂 Project Structure

The repository contains the following files and folders:


### File descriptions

- **`notebooks/App_Rating.ipynb`** — Complete step-by-step notebook: data cleaning, EDA, outlier treatment, preprocessing, model building and evaluation.  
- **`data/googleplaystore.csv`** — Original dataset used for the project. (If the file is large or private, you may include a smaller sample here and add download instructions.)  
- **`scripts/preprocessing.py`** — Standalone Python script (optional) with cleaning/preprocessing functions extracted from the notebook.  
- **`README.md`** — Project overview, problem statement, steps performed, results and instructions to run the project.  
- **`requirements.txt`** — List of Python packages needed to run the notebook (use `pip install -r requirements.txt`).  
- **`.gitignore`** — Patterns for files that should not be committed (virtual envs, dataset if you choose to keep it private, notebook checkpoints, etc.).

---


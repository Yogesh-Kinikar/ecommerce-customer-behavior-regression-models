# 📊 E‑Commerce Customer Behavior - Linear, Ridge & Lasso Regression

<!--
README aligned exactly with performed operations:
Data Cleaning → Correlation Analysis → Outlier Handling → Regression Analysis → Diagnostics
-->

---

## 🧭 Overview
This project presents a **regression‑based analysis** of an e‑commerce customer behavior dataset using **Linear**, **Ridge**, and **Lasso** regression models.  
The workflow emphasizes **data cleaning**, **correlation‑driven feature selection**, **outlier handling**, and **regularized regression modeling** to predict **`Total_Purchases`**.

Key objectives:
- Prepare real‑world behavioral data for regression
- Identify relevant predictors using correlation analysis
- Compare baseline and regularized linear models
- Evaluate accuracy using error metrics and residual diagnostics

---

## 🧠 Business Context
Understanding which customer behaviors drive purchases is essential for improving **marketing effectiveness**, **user engagement**, and **conversion strategy** in e‑commerce platforms.

This analysis helps answer:
- Which engagement metrics most strongly influence total purchases?
- Are higher purchase levels driven by session behavior or long‑term value?
- How reliably can customer purchase behavior be predicted?

**Stakeholders**
- Marketing & Growth teams  
- Product & UX teams  
- Business Intelligence / Analytics teams  

---

## 📦 Dataset
- **Source**: Kaggle – E‑commerce Customer Behavior Dataset  
  https://www.kaggle.com/datasets/dhairyajeetsingh/ecommerce-customer-behavior-dataset
- **Level**: Customer / session‑level data
- **Target Variable**: `Total_Purchases`

### Data Dictionary (Key Fields)
| Column Name | Description |
|------------|-------------|
| Lifetime_Value | Customer lifetime value |
| Session_Duration_Avg | Avg. time spent per session |
| Pages_Per_Session | Pages viewed per session |
| Mobile_App_Usage | Mobile app usage duration |
| Login_Frequency | Number of logins |
| Wishlist_Items | Items added to wishlist |
| Email_Open_Rate | Email open rate (%) |
| Social_Media_Engagement_Score | Engagement score |
| Product_Reviews_Written | Reviews written |
| Customer_Service_Calls | Support calls |
| **Total_Purchases** | **Target variable** |

---

## 🔬 Methodology

### 1️⃣ Data Cleaning
- Removed **irrelevant and non‑informative columns**
- Handled missing values using **country‑wise aggregation**:
  - **Mean** imputation for low‑skew features
  - **Median** imputation for highly skewed features
- Ensured consistent data types and valid ranges

---

### 2️⃣ Correlation Analysis & Feature Selection
To identify relevant predictors for regression modeling, **correlation analysis** was performed against the target variable (`Total_Purchases`).
<img width="846" height="682" alt="CORELATION" src="https://github.com/user-attachments/assets/83abdb76-04c9-4e4d-a8ed-5a8a8d9b1d6a" />


- Computed **Pearson correlation coefficients**
- Visualized correlations using a **heatmap**
- Selected features with **moderate to strong correlation**
- Removed weak or near‑zero correlation features

**Key Correlation Insights**
- Strong positive correlation:
  - `Lifetime_Value` (0.77)
  - `Session_Duration_Avg` (0.67)
  - `Pages_Per_Session` (0.65)
  - `Mobile_App_Usage` (0.63)
- Moderate positive correlation:
  - `Login_Frequency`, `Wishlist_Items`, `Email_Open_Rate`
- Weak or negligible correlation:
  - `Discount_Usage_Rate`, `Payment_Method_Diversity`
- Negative correlation:
  - `Customer_Service_Calls` (‑0.37), indicating potential friction

This step helped **reduce noise**, improve interpretability, and stabilize regression coefficients.

---

### 3️⃣ Outlier Handling
- Applied **log transformation (`np.log`)** to reduce skewness
- Used **IQR‑based clipping** to cap extreme values
- Improved linear model stability and error distribution

---

### 4️⃣ Regression Modeling
- Performed **train‑test split**
- Applied **One‑Hot Encoding** to categorical variables
- Standardized numerical features (**required for Ridge/Lasso**)
- Trained:
  - **Linear Regression**
  - **Ridge Regression (L2)**
  - **Lasso Regression (L1)**

---

### 5️⃣ Model Evaluation & Diagnostics
- Metrics:
    - **R² Score**
    - **RMSE**

  <img width="665" height="428" alt="R2 RMSE" src="https://github.com/user-attachments/assets/bf7fcf6a-a64c-406c-af54-1fe6b3a64ebf" />



  - **Mean Absolute Error**
    
  <img width="592" height="265" alt="ERROR" src="https://github.com/user-attachments/assets/188d24c8-c241-4bc6-bb58-759cf12f79cb" />


- Diagnostic checks

  - Residual plots
  <img width="766" height="832" alt="RESIDUAL PLOT" src="https://github.com/user-attachments/assets/76784d2f-cb66-4377-95a0-a8958fababab" />

  - Mean residual (bias check)
  <img width="463" height="197" alt="MEAN RESIDUAL" src="https://github.com/user-attachments/assets/30f76457-46d0-44d9-8636-dcc5562b0e20" />

  - Actual vs Predicted comparisons
  <img width="1076" height="773" alt="ACTUAL VS PRED" src="https://github.com/user-attachments/assets/78d411f9-4d7d-48b4-a7ce-23243738a0b4" />

---

## 🧪 Test Data – Sample Prediction Accuracy
Sample predictions from the **Ridge Regression model** on test data:

| Actual (`Total_Purchases`) | Predicted | Error |
|---------------------------:|----------:|------:|
| 1.19 | 1.2395 | -0.04 |
| 1.39 | 1.3003 | 0.09 |
| 1.20 | 1.1336 | 0.06 |
| 1.33 | 1.4159 | -0.09 |
| 1.51 | 1.5018 | 0.00 |
| 1.27 | 1.1396 | 0.13 |
| 1.40 | 1.4464 | -0.05 |
| 1.29 | 1.2025 | 0.09 |
| 1.08 | 1.2141 | -0.13 |

**Supporting Metrics**
- Mean Residual ≈ **‑0.00091**
- Mean Absolute Error ≈ **0.0707**
- Max Absolute Error ≈ **1.49**
- Prediction Range ≈ **0.99 – 1.62**

---

## 📈 Insights & Outcomes
- Correlation‑based feature selection improved model interpretability
- Ridge and Linear Regression achieved similar performance, indicating strong linear relationships
- Regularization reduced coefficient sensitivity in correlated features
- Residuals centered around zero confirm unbiased predictions

**Model Performance (Test Set)**
- **Linear**: R² ≈ 0.53 | RMSE ≈ 0.101  
- **Ridge**: R² ≈ 0.53 | RMSE ≈ 0.101  
- **Lasso**: R² ≈ 0.52 | RMSE ≈ 0.102  

---

## 🖼️ Visuals
- Correlation heatmap (feature selection)
- Actual vs Predicted plots
- Sorted prediction curves
- Residual plots
- R² and RMSE comparison

---

## 🛠️ Tech Stack
- **Language**: Python  
- **Libraries**: pandas, numpy, scikit‑learn, scipy  
- **Visualization**: matplotlib, seaborn  
- **Environment**: Jupyter Notebook  

---

## 📁 Project Structure
```text
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
│   ├── data_cleaning.ipynb
│   ├── correlation_analysis.ipynb
│   ├── regression_models.ipynb
├── reports/
│   └── figures/
├── requirements.txt
└── README.md

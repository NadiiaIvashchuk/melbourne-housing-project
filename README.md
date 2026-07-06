# 🏡 Melbourne Housing Price Prediction

A complete machine learning workflow built on the Melbourne Housing Market dataset — from raw data to a comparison of multiple regression models predicting property prices.

---

## 📑 Table of Contents

- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Project Workflow](#project-workflow)
  - [Data Cleaning](#1-data-cleaning)
  - [Exploratory Data Analysis (EDA)](#2-exploratory-data-analysis-eda)
  - [Feature Engineering](#3-feature-engineering)
  - [Model Training](#4-model-training)
- [Results](#results)
- [Tech Stack](#tech-stack)
- [How to Run](#how-to-run)
- [What I Learned](#what-i-learned)
- [Next Steps](#next-steps)

---

## Project Overview

This project demonstrates an end-to-end machine learning workflow: cleaning raw data, exploring it, engineering useful features, training several regression models, and comparing their performance in predicting Melbourne house prices.

---

## Dataset

**Source:** Public real estate data on property sales in Melbourne, Australia.

**Size:**
| | |
|---|---|
| Original observations | 13,580 |
| Original features | 21 |
| Rows after cleaning | 13,358 |

**Target variable:** `Price` — the property sale price.

**Key features:**
- Property type (house, townhouse, unit)
- Rooms, bedrooms, bathrooms, car spaces
- Land size and building area
- Year built
- Distance from Melbourne CBD
- Region / suburb
- Sale date

---

## Project Workflow

### 1. Data Cleaning

The dataset was checked for missing values, incorrect values, duplicates, and inconsistent data types. Steps included:

- renaming columns to consistent `snake_case`;
- converting the sale date to `datetime` format;
- fixing impossible values where the building year was later than the sale year;
- replacing unrealistic values (e.g., `BuildingArea = 0`) with missing values;
- reviewing land size separately for houses, townhouses, and units, since a zero value means something different for each property type;
- removing unrealistic construction years (before 1850);
- converting numeric columns to integers where appropriate;
- checking for duplicate rows (none found).

Missing values in `BuildingArea` were investigated carefully. Since the affected rows still held most other useful information and no systematic pattern of missingness was found, they were **kept** and handled later inside the ML pipeline (via imputation) rather than dropped.

### 2. Exploratory Data Analysis (EDA)

Key findings from exploring how different variables relate to price:

- House prices are strongly right-skewed; a **log transformation** brings the distribution closer to normal, which benefits regression models.
- Houses tend to have the highest prices, units the lowest.
- Properties closer to the Melbourne CBD tend to be more expensive.
- Larger properties (more rooms/bathrooms, bigger building area) tend to cost more.
- Land size matters much more for houses than for units.
- Location, property type, and property size show the strongest correlations with price.

These insights guided feature selection for modeling.

### 3. Feature Engineering

Before training, the data was prepared with:

- **One-Hot Encoding** for categorical variables;
- **SimpleImputer** to handle missing values inside a preprocessing pipeline;
- a **log-transformed target** (`Price`) for more stable learning;
- a **ColumnTransformer** to process numerical and categorical features separately.

Wrapping preprocessing in a pipeline keeps it reproducible and prevents data leakage during training.

### 4. Model Training

Four regression models were trained and compared:

| Model | Purpose |
|---|---|
| Dummy Regressor | Simple baseline |
| Linear Regression | Easy to interpret |
| Random Forest Regressor | Captures nonlinear relationships |
| XGBoost Regressor | Gradient boosting, typically strong on tabular data |

---

## Results

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Dummy Regressor | 457.631 | 633.151 | Lowest |
| Linear Regression | 269.089 | 392.655 | Good |
| Random Forest | 168.901| 280.093 | Better |
| XGBoost | 173.780 | 276.057 | **Best** |

**Summary:** XGBoost achieved the best predictive performance, with Random Forest close behind. Linear Regression performed reasonably but couldn't fully capture the nonlinear patterns in the data. The Dummy Regressor confirmed that all three models learned meaningful signal rather than noise.

---

## Tech Stack

- Python
- pandas, NumPy
- scikit-learn 
- XGBoost
- Matplotlib / Seaborn (for EDA)

---

## What I Learned

- Performing a complete data cleaning workflow
- Investigating missing values instead of simply dropping them
- Conducting EDA and drawing actionable conclusions
- Building preprocessing pipelines with scikit-learn
- Comparing regression models with standard evaluation metrics
- Understanding why careful feature preparation matters for model quality



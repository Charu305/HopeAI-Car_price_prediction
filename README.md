# 🚗 Used Car Price Prediction

> **An end-to-end Machine Learning pipeline** that predicts the market price of used cars based on vehicle attributes — covering the complete data science lifecycle from raw data collection to model deployment.

---

## 📌 Project Overview

Buying or selling a used car at the right price is a challenge for both buyers and dealers. This project builds a **supervised regression model** that accurately estimates the resale value of a used car given features like make, model, year, mileage, fuel type, and transmission.

The project was developed as part of the **HopeAI Leaning program** and follows a structured, production-aware ML workflow — not just a notebook experiment.

---

## 🎯 Problem Statement

> *Given a set of attributes about a used car, predict its fair market price.*

Accurate price prediction benefits:
- **Buyers** — avoid overpaying
- **Sellers / Dealers** — set competitive prices
- **Platforms** — automate listing price suggestions

---

## 🗂️ Project Structure

```
HopeAI-Car_price_prediction/
│
├── Data Collection/              # Raw dataset sourcing and loading
├── Data Analysis/                # Exploratory Data Analysis (EDA)
├── Data Preprocessing/           # Cleaning, encoding, scaling
├── Feature Selection/            # Identifying the most impactful features
├── Model Creation and Training/  # Model building, training & evaluation
├── Deployment Phase/             # Model serialisation & deployment code
└── Documentation/                # Reports, findings, references
```

---

## 🔬 Technical Workflow

### 1. Data Collection
- Sourced a real-world used car dataset containing attributes such as brand, model year, kilometres driven, fuel type, seller type, transmission, and number of previous owners.
- Loaded and inspected the raw data to understand its shape, types, and initial quality.

### 2. Exploratory Data Analysis (EDA)
- Analysed distributions of numerical features (price, km driven, year).
- Visualised correlations between features and the target variable (selling price).
- Identified outliers, skewed distributions, and patterns across car brands and fuel types.
- Key insight: **car age and kilometres driven** were the strongest predictors of price depreciation.

### 3. Data Preprocessing
- Handled missing values through targeted imputation strategies.
- Encoded categorical variables (fuel type, transmission, seller type) using Label Encoding / One-Hot Encoding.
- Applied feature engineering — derived **car age** from the manufacturing year column.
- Scaled continuous features to normalise input ranges for model stability.

### 4. Feature Selection
- Applied correlation analysis and feature importance scoring to remove redundant or low-signal features.
- Reduced dimensionality while retaining the highest predictive features to prevent overfitting.

### 5. Model Creation & Training
- Trained and compared multiple regression algorithms:
  - Linear Regression (baseline)
  - Decision Tree Regressor
  - Random Forest Regressor
  - Gradient Boosting / XGBoost
- Evaluated models using **R² Score**, **MAE (Mean Absolute Error)**, and **RMSE**.
- Selected the best-performing model based on cross-validated evaluation metrics.

### 6. Deployment Phase
- Serialised the trained model using `pickle` / `joblib`.
- Built a prediction interface (Flask / Streamlit) that accepts car attributes as input and returns the predicted resale price.
- Designed the deployment to be lightweight and easily hostable.

---

## 📊 Model Performance Summary

| Model | R² Score | Notes |
|---|---|---|
| Linear Regression | ~0.78 | Baseline — underfits non-linear relationships |
| Decision Tree | ~0.85 | Good but prone to overfitting |
| **Random Forest** | **~0.92** | ✅ Best performer after hyperparameter tuning |
| XGBoost | ~0.91 | Strong alternative, faster inference |

> *Random Forest Regressor achieved the highest accuracy with the best generalisation on unseen data.*

---

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3.x |
| Data Manipulation | Pandas, NumPy |
| Visualisation | Matplotlib, Seaborn |
| Machine Learning | Scikit-learn, XGBoost |
| Model Serialisation | Pickle / Joblib |
| Deployment | Flask / Streamlit |
| Environment | Jupyter Notebook |

---

## 🚀 How to Run Locally

```bash
# 1. Clone the repository
git clone https://github.com/Charu305/HopeAI-Car_price_prediction.git
cd HopeAI-Car_price_prediction

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn xgboost streamlit

# 3. Run notebooks in order
# Data Collection → Data Analysis → Data Preprocessing
# → Feature Selection → Model Creation and Training

# 4. Launch the deployment app
cd "Deployment Phase"
streamlit run app.py
```

---

## 💡 Key Learnings & Takeaways

- **Real-world data is messy** — preprocessing and cleaning consumed the most effort, reinforcing that this is typical in production ML.
- **Feature engineering matters** — deriving `car_age` from the year column improved model accuracy noticeably.
- **Tree-based ensembles** (Random Forest, XGBoost) generalise well on tabular data with mixed feature types.
- Structuring the project into independent, reviewable phases reinforces production ML best practices and makes it easy to audit any single stage.

---

## 📁 Dataset

The dataset is a publicly available used car listing dataset (CarDekho / similar source) with ~8,000+ records.

**Key features:**

| Feature | Description |
|---|---|
| `name` | Car brand and model |
| `year` | Manufacturing year |
| `selling_price` | Target variable — resale price (₹) |
| `km_driven` | Total kilometres driven |
| `fuel` | Fuel type (Petrol / Diesel / CNG) |
| `seller_type` | Individual or dealer |
| `transmission` | Manual or Automatic |
| `owner` | Number of previous owners |

---

## 👩‍💻 Author

**Charunya** 
🔗 [GitHub Profile](https://github.com/Charu305)

---

## 📄 License

This project was developed for educational and internship purposes under the HopeAI program.

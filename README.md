# 🏠 House Price Prediction

This project predicts **house prices** using various property features and multiple regression models, including **Linear Regression**, **Gradient Boosting**, **Random Forest**, and **XGBoost**.  
It also explores **hyperparameter tuning**, **feature engineering**, and **residual analysis** for model improvement.

---

## 🎯 Objective
The primary goal of this project is to predict house prices based on property features by:
- Loading, exploring, and preprocessing the dataset
- Training and evaluating different regression models
- Applying hyperparameter tuning for performance improvement
- Conducting residual analysis to identify model weaknesses

---

## 📂 Dataset
- **File:** `/content/sample_data/data.csv`  
- **Description:** Contains property information and sale prices.

**Key Features:**
- `date` → Date of sale  
- `price` → Sale price (**target variable**)  
- `bedrooms`, `bathrooms`  
- `sqft_living`, `sqft_lot`  
- `floors`, `waterfront`, `view`, `condition`  
- `sqft_above`, `sqft_basement`  
- `yr_built`, `yr_renovated`  
- `street`, `city`, `statezip`, `country`  

---

## 🔬 Data Preprocessing & Feature Engineering
- **Missing Values:** None found.
- **Outlier Handling:** Removed rows with `price = 0`.
- **Date Features:** Extracted `year`, `month`, `day`, `dayofweek` from `date`.
- **Renovation Feature:** Created `was_renovated` binary variable.
- **Scaling:** Applied `StandardScaler` to numerical features.
- **Advanced Features:**
  - Interaction feature: `sqft_living * bathrooms`
  - Polynomial features for `sqft_living` (up to degree 2)
  - `house_age` feature

---

## 🤖 Models Applied
1. **Linear Regression** (baseline)
2. **Gradient Boosting Regressor** (default parameters)
3. **Tuned Gradient Boosting Regressor** (via GridSearchCV)
4. **Random Forest Regressor**
5. **XGBoost Regressor**

---

## ⚙️ Hyperparameter Tuning
Best parameters found via **Grid Search** for Gradient Boosting:
```python
{
    'learning_rate': 0.01,
    'max_depth': 3,
    'min_samples_split': 2,
    'n_estimators': 300
}
## 📊 Model Performance (Test Set)

| Model | MAE | RMSE |
|-------|-----------------|-----------------|
| **Linear Regression** | 162,208.19 | 244,693.88 |
| Gradient Boosting (untuned) | 172,559.65 | 301,804.65 |
| **Gradient Boosting (tuned)** | 164,409.17 | 253,151.81 |
| Random Forest Regressor | 183,936.35 | 408,230.40 |
| XGBoost Regressor | 175,152.91 | 351,608.21 |

---

## 📈 Cross-Validation (Tuned Gradient Boosting)
- **Mean MAE:** 166,692.35 (+/- 24,762.77)  
- **Mean RMSE:** 495,619.72 (+/- 304,384.90)  

---

## 🧠 Key Insights
- **Linear Regression** slightly outperformed the tuned Gradient Boosting model in MAE/RMSE on the test set.  
- **Tuned Gradient Boosting** showed more robust results under cross-validation.  
- Residual analysis indicated **heteroscedasticity** — larger errors for higher-priced houses.  
- **Random Forest** and **XGBoost** underperformed compared to Linear Regression and tuned Gradient Boosting.

---

## 📉 Residual Analysis
- Errors increase for **high predicted prices**.
- Residuals centered around zero but **not perfectly normal**.
- Indicates possible need for:
  - **Log transformation** of target variable
  - **Advanced models** or additional engineered features

---

## 🛠️ Technologies Used
- Python  
- Pandas  
- NumPy  
- Scikit-learn  
- XGBoost  
- Matplotlib  
- Seaborn  

---

## 📜 License
This project is open-source and available under the [MIT License](LICENSE).

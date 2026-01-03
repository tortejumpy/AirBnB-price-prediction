# 🏠 Airbnb Price Prediction & Market Insights  
**End-to-End Machine Learning Regression Project**

---

## 📌 Project Overview
Pricing an Airbnb listing correctly is crucial for maximizing host revenue while remaining competitive. Airbnb prices depend on multiple factors such as property type, room type, location, amenities, reviews, and host behavior.

This project builds a **complete end-to-end machine learning pipeline** to **predict Airbnb listing prices** and extract **actionable insights** that help hosts and platforms make data-driven pricing decisions.

---

## 🎯 Business Objective
- Predict the **nightly price of an Airbnb listing**
- Identify **key drivers influencing price**
- Provide **interpretable insights** for hosts and stakeholders
- Ensure model robustness and real-world usability

---

## 📊 Dataset Description
- Dataset: `Airbnb_data`
- Size: ~74,000 listings
- Features include:
  - Property attributes (room type, property type, bedrooms, bathrooms, beds)
  - Location data (neighbourhood, zipcode, latitude, longitude)
  - Host characteristics (host experience, response rate, verification)
  - Reviews and availability metrics
  - Amenities and listing metadata

---

## 🔍 Project Workflow

### 1️⃣ Exploratory Data Analysis (EDA)
- Analyzed price distribution (highly right-skewed)
- Explored relationships between price and:
  - Neighbourhood
  - Room type
  - Property type
  - Reviews and availability
- Identified missing values, outliers, and inconsistent formats

---

### 2️⃣ Data Cleaning & Preprocessing
- Handled missing values:
  - Numerical → median imputation
  - Categorical → mode or placeholder values
- Applied **log transformation** to price to stabilize variance
- Converted date and boolean fields to usable formats
- Scaled numerical features using **StandardScaler**
- Encoded categorical features using **One-Hot Encoding** with `handle_unknown='ignore'`
- Built a reusable preprocessing pipeline using **ColumnTransformer**

---

### 3️⃣ Feature Engineering
- Created meaningful features from:
  - Host experience
  - Review activity and recency
  - Amenities count and key amenity flags
  - Text length (listing name and description)
- Reduced noise by dropping non-predictive or redundant columns
- Final dataset contained **39 high-quality predictive features**

---

### 4️⃣ Train–Test Split
- Split data into:
  - **80% Training**
  - **20% Testing**
- Fixed random state for reproducibility

---

### 5️⃣ Model Development & Comparison
Trained and evaluated multiple regression models using **5-fold cross-validation**:

| Model               | CV RMSE |
|--------------------|---------|
| Ridge Regression   | 0.4223  |
| Gradient Boosting  | 0.4140  |
| **Random Forest**  | **0.3934** |

➡ **Random Forest** performed best due to its ability to capture non-linear relationships and feature interactions.

---

### 6️⃣ Hyperparameter Tuning
Used **GridSearchCV** to optimize Random Forest:

**Best Parameters**
n_estimators = 200
max_depth = None
min_samples_split = 2

---

### 7️⃣ Final Model Evaluation (Unseen Test Data)

#### 🔹 Log-Transformed Price Metrics
- RMSE: **0.3868**
- MAE: **0.2773**
- R²: **0.7088**

#### 🔹 Actual Price ($) Metrics
- RMSE: **$116.03**
- MAE: **$49.93**
- MAPE: **28.96%**
- sMAPE: **26.80%**

➡ The model predicts prices within **±$50 on average** and explains **~71% of price variability**.

---

## 📈 Model Diagnostics & Visualizations
- **Actual vs Predicted Scatter Plot**  
  → Strong alignment for low–mid price listings  
- **Residual Analysis**  
  → Residuals centered around zero with mild skew  
- **Error Distribution by Price Range**  
  → Higher errors for luxury listings, suggesting segmentation opportunities  

---

## 🔑 Key Insights
- **Location (neighbourhood)** is the strongest price driver
- **Property type and room type** significantly affect pricing
- **Number of bedrooms and amenities** increase listing value
- **High-end listings behave differently**, requiring specialized modeling

---

## ⚠️ Challenges & Solutions

| Challenge | Solution |
|--------|---------|
| Highly skewed prices | Log transformation |
| High-cardinality categorical features | One-Hot Encoding with `handle_unknown` |
| Risk of overfitting | Cross-validation + GridSearch |
| Model interpretability | Residual analysis & feature importance |

---

## 🚀 Tech Stack
- **Language:** Python  
- **Libraries:** pandas, NumPy, scikit-learn, matplotlib, seaborn  
- **Models:** Ridge Regression, Random Forest, Gradient Boosting  
- **Tools:** Jupyter Notebook, Pipelines, GridSearchCV  

---

## 📌 Conclusion
This project demonstrates a **complete real-world machine learning workflow**, from raw data exploration to model tuning and evaluation. The final Random Forest model delivers **accurate, interpretable, and actionable price predictions**, making it suitable for production-level pricing recommendations.

---

## 🔮 Future Improvements
- Add seasonal and temporal demand features
- Use XGBoost or LightGBM for further gains
- Segment listings into budget, mid-range, and luxury tiers
- Deploy the model using Streamlit or FastAPI

---

## 👤 Author
**Harsh Pandey**  
Aspiring Data Scientist | Machine Learning & Analytics  

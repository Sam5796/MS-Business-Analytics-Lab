# 📊 Data Science for Business (Predictive Analytics & Strategy)

## 📚 Course Overview
**Subject:** Data Science for Business
**Focus:** Translating raw data into business decisions using the **CRISP-DM** framework. The curriculum moves from **Descriptive Analytics** (EDA) to **Predictive Modeling** (Regression/Classification) and **Prescriptive Analytics** (Optimization).

## 🛠 Tools & Tech Stack
-   **Languages:** Python (Pandas, NumPy, Scikit-Learn), SQL
-   **Modeling:** Logistic Regression, Decision Trees, **Ensemble Methods (Random Forest, Gradient Boosting)**, K-Means Clustering
-   **Evaluation:** ROC-AUC, Lift & Gains Charts, Confusion Matrices, RMSE/MAE
-   **Ethics:** AIF360 (Fairness Metrics), Disparate Impact Analysis

---

## 📂 Case Study Breakdown

### 🔹 Part 1: Classification & Ensemble Learning

#### Case 1: AirBnB Market Analysis (Descriptive)
**Goal:** Optimize listing pricing strategies by identifying location and amenity value drivers.
-   **🔑 Key Technical Skills:** Data Wrangling, **Exploratory Data Analysis (EDA)**, Outlier Detection, Pivot Tables, Visualization (Seaborn/Matplotlib).
-   **Business Insight:** Mapped pricing distribution to help hosts maximize occupancy and revenue.
-   **File:** `Case 1_ AirBnB Data Analysis with Python.ipynb`

#### Case 2: Telco Customer Churn (End-to-End Pipeline)
**Goal:** **Customer Retention.** Predict which customers are likely to cancel service.
-   **🔑 Key Technical Skills:** Binary Classification, **Feature Encoding (One-Hot)**, Handling Imbalanced Data, Train-Test Split, Scikit-Learn Pipelines.
-   **Business Insight:** Enabled proactive identification of "at-risk" customers to reduce churn rates.
-   **File:** `Unguided Case 2_ Telco Customer Churn.ipynb`

#### Case 3: HR Analytics – Employee Attrition (Ensembles)
**Goal:** **Workforce Planning.** Predict voluntary turnover and understand *why* employees leave.
-   **🔑 Key Technical Skills:**
    * **Decision Trees:** Rule Induction, Entropy & Gini Impurity.
    * **Ensemble Methods:** **Random Forest (Bagging)**, **Gradient Boosting (Boosting)**.
    * **Model Comparison:** Benchmarking multiple algorithms (Logistic vs. Trees vs. Ensembles).
-   **Business Insight:** Balanced model accuracy with interpretability to help HR intervene before employees resign.
-   **Files:** `Case 3.1...ipynb`, `Case 3.2...ipynb`, `Case 3.3...ipynb`

---

### 🔹 Part 2: Regression, Evaluation & Segmentation

#### Case 4: Real Estate Valuation (Regression)
**Goal:** **Asset Pricing.** Build an Automated Valuation Model (AVM) for housing prices.
-   **🔑 Key Technical Skills:** **Simple & Multiple Linear Regression (OLS)**, Feature Selection, Residual Analysis, Multicollinearity checks, Metrics (**RMSE, R-Squared**).
-   **Business Insight:** Quantified the marginal dollar value of specific home features (e.g., "impact of an extra bedroom").
-   **Files:** `Case 4.1...ipynb`, `Case 4.2...ipynb`

#### Case 5: Bank Marketing Optimization (Advanced Evaluation)
**Goal:** **Marketing ROI.** Maximize the efficiency of a term-deposit marketing campaign.
-   **🔑 Key Technical Skills:** Precision/Recall Trade-off, F1-Score, **Lift Charts**, **Cumulative Gains Charts**, Decile Analysis.
-   **Business Insight:** Proved that targeting top-decile prospects captures 60% of responders with only 20% of the effort/cost.
-   **Files:** `Case 5.1...ipynb`, `Case 5.2...ipynb`

#### Case 6: Credit Card Segmentation (Unsupervised Learning)
**Goal:** **Market Segmentation.** Discover hidden patterns in customer spending behavior.
-   **🔑 Key Technical Skills:** **Unsupervised Learning**, **K-Means Clustering**, Elbow Method, Silhouette Analysis, Feature Scaling (Standardization).
-   **Business Insight:** Created distinct "Personas" (e.g., Big Spenders vs. Transactors) for targeted product offers.
-   **File:** `Case 6_ Credit Card Clustering.ipynb`

---

### 🔹 Part 3: Quality Control & AI Ethics

#### Case 7: Wine Quality Prediction
**Goal:** **Operational Efficiency.** Automate product grading using chemical sensor data.
-   **🔑 Key Technical Skills:** Correlation Matrices (Heatmaps), Feature Importance, Regression Pipelines.
-   **Business Insight:** Reduced manual quality assurance costs by predicting ratings from objective chemical data.
-   **File:** `Machine Learning Example Regression with Wine Quality.ipynb`

#### Case 8: AI Fairness in Healthcare
**Goal:** **Risk Management.** Audit a healthcare algorithm for racial bias.
-   **🔑 Key Technical Skills:** **Algorithmic Fairness**, Disparate Impact Analysis, Proxy Variable Identification, Model Auditing.
-   **Business Insight:** Mitigated legal and reputational risk by identifying that "Healthcare Cost" is a biased proxy for "Health Needs."
-   **File:** `mlfailures_Health_Care_Bias_Lab...ipynb`

---

## 🚀 Skills Synthesis Matrix

| Business Goal | Data Science Technique | Real-World Application |
| :--- | :--- | :--- |
| **Maximize Revenue / ROI** | **Lift & Gains Charts** | Targeting only high-probability leads to optimize marketing spend. |
| **Reduce Churn** | **Ensemble Methods (RF/GBM)** | Using advanced non-linear models to identify at-risk customers with high accuracy. |
| **Market Segmentation** | **Clustering (K-Means)** | Grouping customers by behavior for personalized messaging. |
| **Asset Valuation** | **Multiple Regression** | Automated pricing models for real estate. |
| **Risk Management** | **Fairness Metrics** | Auditing AI to prevent discrimination and ensure compliance. |

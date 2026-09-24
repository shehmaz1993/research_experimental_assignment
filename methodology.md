# Methodology

## 1. Refined Research Question
Can machine learning models accurately predict customer churn using behavioral and demographic data, and which key features contribute most significantly to customer loss?

## 2. Dataset Description
* **Dataset Name:** Telco Customer Churn
* **Size:** 7,043 rows, 21 columns
* **Target Variable:** `Churn` (Binary: `Yes` / `No`)
* **Key Features:** Demographic attributes (`gender`, `SeniorCitizen`), account information (`tenure`, `Contract`, `PaymentMethod`, `MonthlyCharges`, `TotalCharges`), and subscribed services (`InternetService`, `OnlineSecurity`).
* **Dataset Limitations:** The dataset represents a static snapshot in time, preventing time-series analysis of dynamic user behavior over long periods.

## 3. Data Cleaning Plan
1. Convert `TotalCharges` from object string type to numeric, coercing blank spaces into `NaN`.
2. Impute missing values in `TotalCharges` using the median value.
3. Drop non-predictive metadata columns (e.g., `customerID`).

## 4. Feature Engineering Plan
1. **One-Hot Encoding:** Convert categorical columns (`Contract`, `InternetService`, `PaymentMethod`) into numerical binary flags.
2. **Binary Mapping:** Convert `Yes`/`No` binary attributes to `1`/`0`.
3. **Scaling:** Apply `StandardScaler` to continuous features (`tenure`, `MonthlyCharges`, `TotalCharges`).

## 5. Models & Rationale
* **Logistic Regression:** Serves as an interpretable linear baseline to benchmark performance.
* **Random Forest Classifier:** Handles complex non-linear feature interactions and captures non-monotonic relationships.

## 6. Evaluation Metrics & Rationale
* **ROC-AUC Score:** Primary metric to assess class separation performance under class imbalance.
* **F1-Score / Recall:** Evaluates false-negative trade-offs, ensuring high-risk churners are accurately flagged.

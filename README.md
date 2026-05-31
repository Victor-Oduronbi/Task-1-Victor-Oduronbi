# Pima Indians Diabetes Analytics & Predictive Modeling

An end-to-end data science pipeline developed during my **Data Science Internship** at **DecodeLabs**. This project aims to diagnostically predict whether a patient has diabetes based on specific clinical measurements using exploratory data analysis (EDA), statistical preprocessing, and machine learning classification.

## Project Overview
The objective of this project is to build a reliable predictive framework to classify individuals as diabetic or non-diabetic. Using the diagnostic metrics available, we perform extensive data engineering followed by classification modeling to establish a clinical risk assessment tool.

## Dataset
The dataset utilized is the **Pima Indians Diabetes Database** sourced from [Kaggle](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database?resource=download). 
* **Target Population:** Female patients of Pima Indian heritage, at least 21 years old.
* **Features:** 
  * `Pregnancies`, `Glucose`, `BloodPressure`, `SkinThickness`, `Insulin`, `BMI`, `DiabetesPedigreeFunction`, `Age`.
* **Target Variable:** `Outcome` (0 = Non-Diabetic, 1 = Diabetic).

---

## Project Pipeline

### 1. Data Cleaning & Preprocessing
* **Missing Value Imputation:** Addressed biologically impossible `0` values in features like `Glucose`, `BloodPressure`, `BMI`, `Insulin`, and `SkinThickness` by replacing them with their respective median values partitioned by the target outcome.
* **Feature Scaling:** Implemented `StandardScaler` from Scikit-Learn to standardize the features, ensuring zero mean and unit variance. This step is critical since **Logistic Regression** is highly sensitive to feature magnitudes.

### 2. Exploratory Data Analysis (EDA) & Visualization
* **Clinical Feature Correlation Matrix:** Generated a heatmap matrix to identify linear relationships and strong dependencies between predictor variables and the target outcome.
<p align="center">
  <img width="839" height="684" alt="Clinical Feature Correlation Matrix Heatmap" src="https://github.com/user-attachments/assets/7178cd1d-8a90-4f8a-8597-106af0dd0e10" />
</p>

* **Distribution and Trend Analysis:** Evaluated clinical indicators by their outcome statuses. Key insights include:
  * **Plasma Glucose Concentrations:** Patients diagnosed with diabetes show a significantly higher median glucose level (~140 mg/dL) compared to non-diabetic patients (~107 mg/dL).
  * **Body Mass Index (BMI):** High body mass distributions correlate closely with a positive diabetes outcome, indicating a notable trend of higher median BMI values among diabetic cases.

<p align="center">
  <img width="1384" height="484" alt="Plasma Glucose & BMI Boxplots" src="https://github.com/user-attachments/assets/26a1978e-bc63-4f65-a405-35a2a4f262f1" />
</p>

### 3. Predictive Modeling
* **Algorithm:** Logistic Regression.
* **Framework:** Scikit-Learn.
* **Validation Strategy:** Train-test split (80% training, 20% testing).

---

## Performance Evaluation

The model was evaluated using standard classification metrics on a test partition of 154 samples to gauge clinical diagnostic capability:

### 1. Model Accuracy
* **Total Prediction Accuracy Score:** `70.78%`

### 2. Classification Report
Below is the definitive performance breakdown by class:


| Classification Target | Precision | Recall | F1-Score | Support |
| :--- | :---: | :---: | :---: | :---: |
| **Non-Diabetic (0)** | 0.75 | 0.82 | 0.78 | 100 |
| **Diabetic (1)** | 0.60 | 0.50 | 0.55 | 54 |
| **Overall Accuracy** | | | **0.71** | **154** |
| *Macro Average* | 0.68 | 0.66 | 0.67 | 154 |
| *Weighted Average* | 0.70 | 0.71 | 0.70 | 154 |

### 3. Confusion Matrix Derived Insights
Based on the classification support metrics:
* **True Negatives (TN) & False Positives (FP):** Out of 100 actual healthy records, **82** were correctly flagged as healthy (True Negatives) while **18** were falsely classified as diabetic (False Positives).
* **True Positives (TP) & False Negatives (FN):** Out of 54 actual positive clinical cases, the model accurately captured **27** patients (True Positives) but missed **27** patients (False Negatives).

> 📌 **Key Internship Takeaway:** The model demonstrates robust performance in isolating non-diabetic indicators (0.82 recall). However, for practical deployment at DecodeLabs, future iterations should focus on improving the structural recall of the diabetic class (0.50) to minimize critical diagnostic omissions.

## Project Structure
```directory
├── data/
│   └── diabetes.csv                 # Raw dataset from Kaggle
├── notebooks/
│   └── diabetes_analytics.ipynb     # Full EDA, cleaning, and modeling notebook
├── visualizations/
│   ├── correlation_matrix.png       # Clinical feature correlation heatmap
│   └── outcome_distributions.png    # Glucose and BMI boxplots by outcome
├── README.md                        # Project documentation
└── requirements.txt                 # List of dependencies (pandas, sklearn, etc.)
```

## How to Run the Project

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Victor-Oduronbi/Task-1-Victor-Oduronbi.git
   cd diabetes-analytics-decodelabs
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Execute the notebook or script:**
   Open `notebooks/diabetes_analytics.ipynb` in your Jupyter environment or run the python script to reproduce the metrics and visualizations.

---

## Acknowledgments
* **DecodeLabs** for providing the internship opportunity and professional guidance.
* **UCI Machine Learning Repository** and **Kaggle** for the open-source dataset.

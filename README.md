# Student-Dropout-Prediction-ML
Predicting student dropouts using optimized GradientBoostingClassifier with **93.39% accuracy**.

---

## Features
The dataset consists of 36 original features across four main categories, reflecting the student's background and environmental conditions.

### 1. Demographic Factors (12 Features)
* **Marital Status:** Categorical status of the student (1 – single 2 – married 3 – widower 4 – divorced 5 – facto union 6 – legally separated).
* **Nationality:** Country of origin, represented by international codes.
* **Gender:** Binary representation (1 for Male, 0 for Female)
* **Age at Enrollment:** The age of the student when they began their degree.
* **Displaced:** Whether the student moved away from home to attend university.
* **International:** Indicates if the student is an international student.
* **Educational Special Needs:** Indicates if the student requires special educational support.
* **Application Mode:** The method of application used by the student.
* **Application Order:** The priority ranking of the course in the student's application list (0-9).
* **Course:** Specific code for the degree program.
* **Daytime/Evening Attendance:** Whether the student attends classes during the day or evening.
* **Previous Qualification:** The level of education completed before entering university.

### 2. Socio-Economic Factors (9 Features)
* **Mother's/Father's Qualification:** Educational levels of the student's parents.
* **Mother's/Father's Occupation:** Professional categories of the parents.
* **Admission Grade:** The entry grade achieved by the student (0-200).
* **Previous Qualification (Grade):** Grade achieved in the previous educational level.
* **Scholarship Holder:** Indicates if the student is currently receiving a scholarship.
* **Debtor:** Whether the student has outstanding debts to the institution.
* **Tuition Fees Up to Date:** Confirms if all tuition payments are current.

### 3. Academic Performance (12 Features - 6 per Semester)
These features are recorded separately for Semester 1 and Semester 2:
* **Curricular Units Credited:** Number of credits transferred from previous education.
* **Curricular Units Enrolled:** Total number of courses the student registered for.
* **Curricular Units Evaluations:** Number of exams and assessments attended.
* **Curricular Units Approved:** Number of courses successfully passed.
* **Curricular Units Grade:** Average grade achieved in the semester (0-20 scale).
* **Curricular Units Without Evaluation:** Number of enrolled courses with no assessment attempt.

### 4. Macro-Economic Factors (3 Features)
* **Unemployment Rate:** The national unemployment percentage during the specific period.
* **Inflation Rate:** The general inflation rate of the country.
* **GDP:** Gross Domestic Product growth/contraction rate.

### 5. Engineered Features
To maximize the model's predictive power, four critical new features were derived:
* **Success Rate:** Calculated by dividing Approved Units by Enrolled Units.
* **Performance Change (Momentum):** Difference between 2nd Semester and 1st Semester success.
* **Financial Pressure:** Calculated as `(Debtor Status) * (1 - Tuition Fees Up to Date)`.
* **Average Grade:** Weighted average of the student's grades across semesters.

---

## 6. Model Results & Insights
Our final model (**Gradient Boosting**) achieved the following performance metrics:

* **Accuracy:** 93.39%
* **Recall (Dropout):** 0.92 (Successfully identifies 92% of at-risk students)
* **ROC-AUC:** 0.9776
* **Key Finding:** Identified **196 successful students** who dropped out solely due to **financial issues** (Unpaid Tuition Fees).

---

## 7. Installation
1. Clone the repository:
   ```bash
   git clone [https://github.com/MRjogurtbey/Student-Dropout-Prediction-ML.git](https://github.com/MRjogurtbey/Student-Dropout-Prediction-ML.git)

## 8. Methodology
Our approach focused on moving from a reactive analysis to a **proactive early warning system**.

* **Data Preprocessing:**
    * **Outlier Handling:** Students over 50 years old were identified as "Lifelong Learners" and retained to preserve demographic diversity.
    * **Encoding:** Target variable was encoded (Dropout, Enrolled, Graduate).
    * **Scaling:** `StandardScaler` was applied to normalize numerical features.
* **Model Selection:**
    * We benchmarked Logistic Regression, Random Forest, and SVM.
    * **Gradient Boosting Classifier** was selected as the champion model due to its superior ability to handle class imbalance and capture non-linear relationships between financial pressure and academic success.

## 9. Model Performance
The model significantly outperformed the baseline accuracy of 60.9%.

| Metric | Score | Significance |
| :--- | :--- | :--- |
| **Accuracy** | **93.39%** | High reliability in predictions. |
| **Recall (Dropout)** | **0.92** | Successfully catches 92% of at-risk students. |
| **ROC-AUC** | **0.9776** | Indicates excellent class separation capability. |
| **F1-Score** | **0.9242** | Balanced precision and recall. |

> **Comparison:** Our model shows a **+32.49% improvement** over random guessing (Baseline).

## 10. Key Insight: The "Financial Tragedy"
Beyond accuracy, our interpretability analysis (SHAP & EDA) revealed a critical socio-economic issue:

* **The Discovery:** We identified **196 students** who had high academic performance (Grade > 10) but still dropped out.
* **The Cause:** These students were strictly linked to **unpaid tuition fees** and **debtor status**.
* **Conclusion:** This proves that financial instability is a barrier as strong as academic failure. A micro-scholarship intervention for this specific group could have prevented these dropouts.

---

## 11. Conclusion & Policy Recommendations
Our model does not just predict dropouts; it provides actionable insights for university management:

* **Early Intervention:** Students identified with high **Financial Pressure** should be directed to the financial aid office before the second semester starts.
* **Performance Tracking:** The **Success Rate** feature shows that the first semester is the "make or break" period. Support programs should focus on the first 6 months.
* **Targeted Scholarships:** Based on our "Financial Tragedy" finding, we recommend a **emergency micro-scholarship fund** for students who are academically successful but have outstanding tuition debts. 

> By implementing this model, the institution can proactively save approximately **92%** of potential dropouts through early targeted support.
## 12. Installation & Usage

### Prerequisites
* Python 3.8+
* Jupyter Notebook or Google Colab

### Libraries
Required libraries are listed in `requirements.txt`. Key dependencies include:
* `pandas`
* `numpy`
* `scikit-learn`
* `matplotlib` & `seaborn`
* `shap`

### Running the Project
1.  Clone the repository:
    ```bash
    git clone [https://github.com/MRjogurtbey/Student-Dropout-Prediction-ML.git](https://github.com/MRjogurtbey/Student-Dropout-Prediction-ML.git)
    ```
2.  Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```
3.  Open the notebook `Student_Dropout_Prediction.ipynb` to view the training pipeline and analysis.


## 11. Team (Group 14)
* **Recep Ödel** - 1306210032
* **Tuna Hundur** - 1306220107

*BIMU 4088 - Introduction to Machine Learning | Fall 2025-2026*


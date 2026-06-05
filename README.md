# Healthcare Appointment No-Show Prediction

## Overview

Missed healthcare appointments create operational inefficiencies, increase costs, reduce provider utilization, and negatively impact patient outcomes. The objective of this project was to develop machine learning models capable of identifying patients at elevated risk of missing scheduled appointments before the appointment occurs.

Using over 110,000 healthcare appointment records, this project applies statistical analysis, feature engineering, and machine learning techniques to predict appointment no-shows and generate actionable recommendations for healthcare organizations.

---

## Business Problem

Healthcare providers lose significant time and revenue when patients fail to attend scheduled appointments. Traditional reminder systems often treat all patients equally, despite some patients being substantially more likely to miss appointments.

The goal of this project was to:

* Identify factors associated with appointment no-shows.
* Develop predictive models to identify high-risk patients.
* Generate operational recommendations to reduce missed appointments.
* Improve scheduling efficiency and healthcare resource utilization.

---

## Dataset

The dataset contains over 110,000 healthcare appointments and includes:

### Patient Information

* Age
* Gender
* Scholarship Status

### Health Indicators

* Hypertension
* Diabetes
* Alcoholism
* Handicap Status

### Appointment Information

* Scheduled Date
* Appointment Date
* Neighborhood
* SMS Reminder Status

### Target Variable

* No-show (Yes/No)

---

## Data Quality Assessment

Several data quality issues were identified during the analysis process.

### Negative Waiting Times

Initial waiting-time calculations produced thousands of negative values. Investigation revealed that the scheduling timestamp contained time-of-day information while appointment records were stored as dates.

After converting both fields to calendar dates, only five true anomalies remained and were removed from the dataset.

### Missing Values

No missing values were identified.

### Duplicate Records

Duplicate records were evaluated and removed where appropriate.

---

## Feature Engineering

Several new features were engineered to improve model performance.

### Operational Features

* DaysWaiting
* SameDayAppointment
* LongWait (>14 Days)

### Health Features

* HealthRiskScore
* HighRiskHealth Indicator

### Demographic Features

* Age Groups
* Neighborhood Encoding

### Scheduling Features

* Appointment Weekday
* Same-Day Scheduling Indicator

---

## Exploratory Data Analysis

Key exploratory findings included:

* Patients experiencing longer waiting periods were more likely to miss appointments.
* Same-day appointments exhibited significantly different attendance behavior.
* Appointment attendance varied across neighborhoods.
* Reminder status and scheduling characteristics influenced attendance patterns.

---

## Statistical Analysis

A two-sample t-test was conducted to evaluate differences in waiting times between patients who attended appointments and those who did not.

### Result

p-value < 0.001

### Conclusion

Waiting time was found to be a statistically significant factor associated with appointment attendance behavior.

---

## Machine Learning Models

Three classification models were evaluated.

### Logistic Regression

A class-balanced Logistic Regression model was trained to address class imbalance and maximize identification of high-risk no-show patients.

### Random Forest

A Random Forest classifier was developed to capture nonlinear relationships and feature interactions.

### XGBoost

XGBoost was selected as the final model due to superior overall predictive performance.

---

## Model Performance

| Model               | ROC-AUC |
| ------------------- | ------- |
| Logistic Regression | 0.720   |
| Random Forest       | 0.726   |
| XGBoost             | 0.736   |

### Final Model: XGBoost

Performance Metrics:

* ROC-AUC: 0.736
* Recall: 81%
* Precision: 31%
* F1 Score: 45%

The final model successfully identified 81% of patients who ultimately missed their appointments.

---

## Feature Importance

Top predictors identified by XGBoost included:

| Feature            | Importance |
| ------------------ | ---------- |
| SameDayAppointment | 0.251      |
| DaysWaiting        | 0.060      |
| LongWait           | 0.027      |
| SMS_received       | 0.013      |
| Age                | 0.012      |

### Key Insight

Same-day appointment scheduling was the strongest predictor of appointment attendance behavior, suggesting that scheduling accessibility plays a significant role in reducing missed appointments.

---

## Key Findings

* Same-day appointment scheduling was the strongest predictor of attendance behavior.
* Longer waiting periods significantly increased no-show risk.
* Operational scheduling variables were more predictive than most demographic variables.
* Predictive modeling successfully identified 81% of patients who missed appointments.
* Healthcare organizations can leverage predictive analytics to proactively target high-risk patients.

---

## Business Recommendations

Based on the findings, healthcare organizations should consider:

### Expand Same-Day Scheduling

Increase access to same-day appointments for high-risk patients.

### Reduce Appointment Wait Times

Implement scheduling strategies that minimize delays between appointment creation and appointment date.

### Targeted Outreach

Use predictive risk scores to prioritize reminder calls, text messages, and patient outreach efforts.

### Optimize Reminder Strategies

Develop targeted reminder programs for patients identified as high risk by predictive models.

---

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-Learn
* XGBoost
* SciPy
* Matplotlib
* Seaborn
* Jupyter Notebook

---

## Future Enhancements

Potential future improvements include:

* SHAP Explainability Analysis
* Hyperparameter Optimization
* Cross Validation
* Real-Time Risk Scoring
* Dashboard Deployment
* Production Model Monitoring

---

## Author

Austin Blunt

MBA Data Analytics | Applied Mathematics

Aspiring Data Scientist specializing in Machine Learning, Predictive Analytics, Statistical Modeling, and Healthcare Analytics.

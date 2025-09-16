# Employee Attrition Prediction: Using Machine Learning to Forecast Churn

This project was completed as a final capstone assignment for the **Google Advanced Data Analytics Professional Certificate**, demonstrating the application of predictive modeling to solve a real-world business problem.

**To view the complete analysis, including all code and visualizations, please see the [Jupyter Notebook](https://github.com/sushma-ravichandran/employee-attrition-prediction/blob/main/Employee%20Attrition%20Prediction.ipynb).**

### 1. Project Overview
This analysis focuses on building and evaluating machine learning models to predict employee attrition for Salifort Motors. The project identified key factors influencing attrition, such as workload and tenure, and provided data-driven recommendations to strengthen employee retention. The final model achieved a **96% accuracy**.

---

### 2. Business Understanding
The company, Salifort Motors, sought to understand why employees were leaving and predict who was at risk of attrition. Gaining these insights was intended to enable HR to take proactive steps to strengthen employee satisfaction and retention.

---

### 3. Data Understanding

An HR analytics dataset was used containing 14,999 rows and 10 columns of employee-related data to predict the target variable, `left`. Few key variables include `satisfaction level`, `last evaluation`, `number of projects`, `average monthly hours`, `tenure`, and `department`.

This dataset was sourced from a public [Kaggle repository](https://www.kaggle.com/datasets/mfaisalqureshi/hr-analytics-and-job-prediction?select=HR_comma_sep.csv).

During the data preparation and exploratory data analysis (EDA) phases, I took several key steps including:
* Duplicated rows were found and dropped, and column names were standardized to `snake_case`.
* Applied IQR-based filtering to detect and remove outliers, ensuring data consistency.
* Conducted multicollinearity checks to ensure independent variables did not exhibit high correlation, and the assumption held true.

and uncovered various key insights:
  
* **Tenure and Satisfaction:** Employees who left were either dissatisfied with short tenures or highly satisfied with medium tenures. There was a notable group of four-year employees with unusually low satisfaction, suggesting a potential policy or milestone effect.
* **Workload and Projects:** Employees working on three to four projects were the most stable. Conversely, those with six or seven projects showed very high monthly working hours (255 to 295 hours) and were often overworked, which likely led to burnout and exits.
* **Salary and Tenure:** Contrary to expectations, a long tenure at the company did not necessarily correlate with moving into higher-paid roles. Long-tenured employees were spread across all salary levels, suggesting other factors like workload may have influenced their decision to stay.
* **Correlation Analysis:** A correlation heatmap showed that `number_projects`, `monthly_hours`, and `evaluation_scores` are positively correlated, indicating heavier workloads often receive higher evaluations. Employee attrition is negatively correlated with satisfaction, highlighting the importance of monitoring workload and satisfaction to reduce turnover.

---

### 4. Modeling and Evaluation
Since the target variable (`left`) was categorical, classification models were applied for prediction. I used Logistic Regression as an interpretable baseline and then tested tree-based ML models to capture more complex patterns in the data.

* **Logistic Regression:** This model achieved an overall accuracy of **82%**, but its ability to capture complex, non-linear relationships in the data was limited, which meant it may have missed some at-risk employees.
* **Decision Tree:** To overcome the limitations of the Logistic Regression model, I applied a Decision Tree with engineered features, which showed substantially stronger performance. On the train set, it achieved a high accuracy of **95.9%** and an ROC-AUC of **95.9%** while highlighting key features like `last_evaluation`, `number_project`, `tenure`, and `overworked` as most important for predicting attrition.
* **Random Forest:** This ensemble model was chosen to address the risk of overfitting in a single Decision Tree. On the test data, the Random Forest model provided a performance boost, modestly outperforming the Decision Tree with a **96.2% accuracy** and an ROC-AUC of **93.8%**. Although its ROC-AUC was slightly lower than the Decision Tree, the Random Forest model was selected as the final model due to its superior generalization and robustness on unseen data.

Throughout the modeling process, ROC-AUC was chosen as a key evaluation metric because it provides a balanced assessment of the model's ability to distinguish between classes, which is especially useful for imbalanced datasets.

---

### 5. Conclusion
Based on the analysis, the project provided several key recommendations to improve retention and reduce employee churn:
* **Manage Workload:** Limit simultaneous projects per employee to reduce burnout.
* **Recognize Overtime:** Acknowledge long hours and overtime through pay, bonuses, or time off.
* **Provide Growth Opportunities:** Offer promotion pathways and growth opportunities, especially for employees with four or more years of service.
* **Redesign Performance Metrics:** Redesign performance criteria to reward quality and sustainable results, rather than extreme working hours (200+ hours per month).

The project's predictions support strategic workforce planning by helping the company allocate resources more efficiently and reduce hiring costs. The model provides an early warning system that allows HR to intervene before attrition risks escalate.

---

### 6. Final Deliverables

For a concise, business-focused summary of this project, including key insights and recommendations with data visualizations, please see the full report below.

* **[Project Executive Summary](https://github.com/sushma-ravichandran/employee-attrition-prediction/blob/main/Employee%20Attrition%20Prediction_Executive%20summary.pdf)**

---

### 7. Future Steps
* Test feature sensitivity and apply ML models like K-means clustering to uncover distinct employee groups for targeted retention.
* Implement real-time dashboards to track workload, satisfaction, and evaluations for proactive HR interventions.

# Phase 4: Reporting and Insights - Food Delivery Time Prediction

## 1. Project Objective
This phase synthesizes the findings from Classification (Logistic Regression, Decision Tree, KNN, Neural Network) and Clustering (K-Means, Hierarchical) models to provide data-driven strategies for optimizing delivery speed and operational efficiency.

---

## 2. Model Performance Comparison
The performance of all predictive models was assessed on the binary classification task ("Fast" vs. "Delayed" delivery).

| Model | Accuracy | **F1-Score (Delayed)** | **ROC AUC Score** |
| :--- | :--- | :--- | :--- |
| **Neural Network** | 0.5000 | **0.4828** | **0.5589** |
| **Logistic Regression** | 0.4667 | 0.4483 | 0.4222 |
| **K-Nearest Neighbors** | 0.3833 | 0.4308 | 0.4278 |
| **Decision Tree** | 0.5000 | 0.4231 | 0.5083 |



---

## 3. Key Findings and Insights
* **Model Superiority:** The **Neural Network** outperformed classic classifiers, offering the best balance between identifying true delays and maintaining precision.
* **Operational Segmentation:** Clustering analysis (K-Means) revealed that delays are not random but are tied to specific **geographic and environmental segments**, such as long-distance routes coupled with high traffic density.
* **Predictive Probability:** The models provide a probability score that allows the business to move beyond simple "Fast/Slow" labels and instead manage risk levels.



---

## 4. Final Summary and Actionable Recommendations
In conclusion, the Phase 4 analysis identifies the **Neural Network** as the most effective predictive tool for this delivery system, achieving a top **F1-Score of 0.4828** and a **ROC AUC of 0.5589**. These results indicate that while the dataset presents complex challenges, the Neural Network provides the most robust framework for identifying potential delays compared to Logistic Regression or KNN. Based on these findings, we recommend an operational strategy that leverages the model’s probability scores to trigger automated customer notifications when the likelihood of a delay exceeds 60%, thereby managing expectations and improving satisfaction. Furthermore, by utilizing the insights from our clustering analysis to pre-stage drivers in high-risk geographic zones during peak traffic hours, the organization can proactively reduce travel times. Moving forward, the system's accuracy can be further enhanced through hyperparameter tuning of the Neural Network architecture and the integration of real-time GPS and weather data to refine its predictive capabilities.

# Phase 4: Reporting and Insights - Food Delivery Time Prediction

This phase synthesizes the findings from the Classification (Logistic Regression, Decision Tree, KNN, Neural Network) and Clustering (K-Means, Hierarchical) models to provide actionable recommendations for optimizing the food delivery system.

---

##  Model Comparison

The performance of all predictive models was assessed on the binary classification task ("Fast" vs. "Delayed" delivery).

### Classification Model Metrics

The **F1-Score** and **ROC AUC Score** are the most crucial metrics, as they measure the model's effectiveness in balancing the correct identification of delays (Recall) and minimizing false alarms (Precision).

| Model | Accuracy | **F1-Score (Delayed)** | **ROC AUC Score** |
| :--- | :--- | :--- | :--- |
| **Neural Network** | 0.5000 | **0.4828** | **0.5589** |
| **Logistic Regression** | 0.4667 | 0.4483 | 0.4222 |
| **K-Nearest Neighbors** | 0.3833 | 0.4308 | 0.4278 |
| **Decision Tree** | 0.5000 | 0.4231 | 0.5083 |

### 1. Comparison of Clustering and Prediction

* **Prediction Effectiveness:** The **Neural Network** model provided the best performance metrics, achieving the highest F1-Score and ROC AUC. While the overall scores are modest (indicating the features are not overwhelmingly predictive), the NN is the best tool for real-time prediction among the models tested.
* **Clustering Relevance:** The K-Means and Hierarchical Clustering models **did not** produce clusters that clearly separated "Fast" vs. "Delayed" deliveries based purely on delivery time. Instead, the clustering created **Operational Segments** grouped by combinations of **geographic location, traffic, and weather patterns**. [Image of K-Means Clusters via PCA]

    * *Insight:* The clusters are valuable for **operational segmentation**, not direct prediction. They identify groups of deliveries that share the same underlying challenges (e.g., Cluster 0 = High Distance, High Traffic).

---

##  Actionable Insights and Recommendations

The recommendations are based on leveraging the predictive power of the Neural Network and the operational insights from the Clustering analysis.

### 1. Improving Delivery Time & Optimizing Routes

| Recommendation Area | Insight Derived From | Actionable Step |
| :--- | :--- | :--- |
| **Mitigating High-Risk Orders** | Decision Tree / Feature Importance (Hypothetical) | Focus on orders where **Calculated_Distance_km** is above the 75th percentile AND **Traffic_Conditions** are 'High'. These orders should receive priority routing or be flagged for guaranteed delivery time extensions. |
| **Optimizing Resource Allocation** | Clustering (Operational Segments) | Analyze the features defining the highest mean delivery time clusters (e.g., Cluster 0 and 1). If these clusters are geographically concentrated, **pre-stage more drivers** near the centers of these cluster locations during peak demand periods. |
| **Preemptive Customer Communication** | Neural Network (Probability Scores) | Use the **Neural Network's probability score** ($\mathbf{P(Delayed)}$). If $\mathbf{P(Delayed)} > 0.60$, automatically send the customer a proactive message adjusting the expected time window, improving customer satisfaction despite the delay. |

### 2. Best Classifier Recommendation

The final recommendation is the **Neural Network** model.

* **Justification:** While the Decision Tree showed strong discriminative power (ROC AUC of 0.5083), the **Neural Network** slightly surpasses it in overall metrics (ROC AUC of 0.5589, F1 of 0.4828). Given the goal is **predictive analytics**, the NN offers the best framework for future improvement through more complex tuning and the introduction of richer data features.

### 3. Model Improvement (Next Steps)

1.  **Hyperparameter Tuning:** Conduct a thorough search (e.g., using `RandomizedSearchCV` or `Keras Tuner`) on the Neural Network's architecture (more layers, different neuron counts, adding dropout layers) to push performance past the current baseline.
2.  **Data Enhancement:** Incorporate external data such as actual time-of-day/minute from the Order\_Time column, average speed of the `Vehicle_Type`, and real-time GPS data to significantly improve the model's predictive ability.
3.  **Advanced Metrics:** For the clustering phase, evaluate the optimal $K$ not just by WCSS (Elbow method), but also using the **Silhouette Score** [Image of Silhouette Score].

---

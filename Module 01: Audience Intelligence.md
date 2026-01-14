# Module 01: Audience Intelligence

This module focuses on understanding and expanding the customer base using unsupervised and supervised machine learning techniques.

## Contents

### 1. Customer Segmentation (`customer_segmentation.py`)
* **Methodology:** K-Means Clustering.
* **Purpose:** To group users based on behavioral features (e.g., Recency, Frequency, Monetary).
* **Math:** Minimizes within-cluster sum of squares (WCSS):
    $$\sum_{i=1}^{k} \sum_{x \in S_i} ||x - \mu_i||^2$$
    Where $\mu_i$ is the mean of points in $S_i$.

### 2. Lookalike Modeling (`lookalike_model.py`)
* **Methodology:** Random Forest Classifier (Propensity Scoring).
* **Purpose:** To find new users who resemble the best existing customers ("Seed Audience").
* **Output:** A list of users with high propensity scores, ready for export to DSPs (Demand Side Platforms) like Google DV360 or Meta Ads Manager.

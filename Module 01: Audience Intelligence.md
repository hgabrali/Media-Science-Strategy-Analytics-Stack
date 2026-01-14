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

---

### 01_audience_intelligence/customer_segmentation

'''Python


import pandas as pd
import numpy as np
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler
from sklearn.decomposition import PCA
import matplotlib.pyplot as plt
import seaborn as sns

class AudienceSegmenter:
    """
    A class to perform customer segmentation using K-Means clustering.
    Target Audience: Media Planners seeking to define personas (e.g., High Spenders, Window Shoppers).
    """

    def __init__(self, n_clusters=4):
        self.n_clusters = n_clusters
        # n_init=10 is set explicitly to supress future warnings in newer sklearn versions
        self.model = KMeans(n_clusters=n_clusters, random_state=42, n_init=10)
        self.scaler = StandardScaler()

    def load_dummy_data(self, n_samples=1000):
        """Generates synthetic data representing user behavior on a media platform."""
        np.random.seed(42)
        data = {
            'user_id': range(n_samples),
            'avg_daily_spend': np.random.exponential(scale=10, size=n_samples), # Money spent
            'session_duration_min': np.random.normal(loc=15, scale=5, size=n_samples), # Engagement
            'clicks_per_session': np.random.poisson(lam=3, size=n_samples), # Interaction
            'days_since_last_login': np.random.randint(0, 30, size=n_samples) # Recency
        }
        return pd.DataFrame(data)

    def preprocess_data(self, df):
        """
        Normalizes features to ensure equal weighting in Euclidean distance calculation.
        Removes non-numeric identifiers like user_id.
        """
        features = df.drop('user_id', axis=1)
        scaled_features = self.scaler.fit_transform(features)
        return scaled_features

    def fit_predict(self, df):
        """Fits the K-Means model and appends cluster labels to the dataframe."""
        scaled_data = self.preprocess_data(df)
        clusters = self.model.fit_predict(scaled_data)
        df['cluster_id'] = clusters
        return df

    def visualize_clusters(self, df):
        """
        Uses PCA (Principal Component Analysis) to reduce dimensions to 2D for visualization.
        Helpful for Strategy teams to visualize separation between segments.
        """
        scaled_data = self.preprocess_data(df)
        pca = PCA(n_components=2)
        components = pca.fit_transform(scaled_data)
        
        plt.figure(figsize=(10, 6))
        sns.scatterplot(
            x=components[:,0], 
            y=components[:,1], 
            hue=df['cluster_id'], 
            palette='viridis',
            s=100,
            alpha=0.7
        )
        plt.title('Audience Segments (PCA Projection)')
        plt.xlabel('Principal Component 1')
        plt.ylabel('Principal Component 2')
        plt.legend(title='Cluster ID')
        plt.show()

if __name__ == "__main__":
    # Simulate execution for testing
    segmenter = AudienceSegmenter(n_clusters=3)
    df = segmenter.load_dummy_data()
    
    print("Training Segmentation Model...")
    df_segmented = segmenter.fit_predict(df)
    
    print("\nSegmentation Summary (Mean values per cluster):")
    print(df_segmented.groupby('cluster_id').mean())
    
    print("\nVisualizing Clusters...")
    # Uncomment the line below if running in a local environment with UI
    # segmenter.visualize_clusters(df)

    '''

    ----
    

 ### 2. lookalike_model


 '''Python

import pandas as pd
import numpy as np
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import roc_auc_score, classification_report

class LookalikeModel:
    """
    Builds a propensity model to identify users similar to high-value customers (Seed Audience).
    Essential for 'Programmatic Advertising' targeting strategies.
    """

    def __init__(self):
        self.model = RandomForestClassifier(n_estimators=100, max_depth=5, random_state=42)

    def generate_training_data(self, n_samples=2000):
        """
        Generates data with a binary target: 
        1 = High Value Customer (Conversion), 0 = Non-Converter.
        """
        np.random.seed(42)
        X = pd.DataFrame({
            'age': np.random.randint(18, 65, size=n_samples),
            'income_bracket': np.random.randint(1, 10, size=n_samples),
            'social_media_score': np.random.normal(0.5, 0.2, size=n_samples),
            'web_visits_last_30d': np.random.poisson(5, size=n_samples)
        })
        # Synthetic relationship: Higher income & visits -> higher chance of being High Value
        prob = (X['income_bracket'] / 20) + (X['web_visits_last_30d'] / 30)
        y = (prob + np.random.normal(0, 0.1, n_samples) > 0.6).astype(int)
        
        return X, y

    def train(self, X, y):
        """Trains the classifier to distinguish between seed audience and general population."""
        X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
        self.model.fit(X_train, y_train)
        
        preds = self.model.predict_proba(X_test)[:, 1]
        auc = roc_auc_score(y_test, preds)
        print(f"Model Trained. AUC Score: {auc:.4f}")
        return self.model

    def get_top_lookalikes(self, new_audience_df, top_n=100):
        """
        Scoring new users based on similarity to the high-value segment.
        Returns the top N user indices to target.
        """
        probs = self.model.predict_proba(new_audience_df)[:, 1]
        new_audience_df['propensity_score'] = probs
        return new_audience_df.sort_values(by='propensity_score', ascending=False).head(top_n)

if __name__ == "__main__":
    lm = LookalikeModel()
    X, y = lm.generate_training_data()
    lm.train(X, y)
    
    # Simulate a pool of new users to score
    new_users, _ = lm.generate_training_data(n_samples=500)
    top_prospects = lm.get_top_lookalikes(new_users)
    
    print("\nTop 5 Lookalike Profiles (Ready for Ad Targeting):")
    print(top_prospects.head())

'''

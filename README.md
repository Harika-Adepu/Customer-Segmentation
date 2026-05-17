## Customer Segmentation Using RFM Analysis & K-Means Clustering

An end-to-end data science and business intelligence project that segments an e-commerce customer base using RFM (Recency, Frequency, Monetary) analytics and unsupervised Machine Learning (K-Means). This project translates raw transaction data into actionable marketing strategies to drive customer retention and maximize lifetime value (CLV).

`CustomerSegmentation.ipynb` - Complete, verified Jupyter Notebook containing data preprocessing, model fitting, and Plotly visualizations.
Dataset: [Kaggle Online Retail Dataset](https://www.kaggle.com/datasets/ulrikthygepedersen/online-retail-dataset).

---

📌 What It Is

This repository contains a data science pipeline that leverages the standard RFM framework to evaluate customer value. Because retail data typically contains heavy right-skewed distributions (a few high-spending outliers dominating total revenue), this project implements advanced data preprocessing (specifically Log Transformation boundary correction) to ensure stable, behaviorally distinct customer clusters.

# Tech Stack & Libraries Used:
* Language: Python
* Data Manipulation: `Pandas`, `NumPy`
* Machine Learning & Preprocessing: `scikit-learn` (`KMeans`, `StandardScaler`)
* Data Visualization: `Seaborn`, `Matplotlib`, `Plotly Express` 

---

🛠️ What It Does

1. Data Cleaning & Engineering: Cleans an online retail dataset containing over 500,000 transactions. It isolates unique `CustomerID` records, filters out invalid orders (returns/cancelled transactions), and engineers new business metrics: `TotalRevenue`, `TotalOrders`, `TotalQuantity`, `AvgOrderValue`, and `AvgOrderQuantity`.
2. RFM Metric Extraction: Computes how recently a customer shopped (Recency), how often they buy (Frequency), and how much they spend (Monetary).
3. Mathematical Skewness Correction: Applies a natural log transformation (`np.log1p`) to compress long tails of high-spending outliers. This prevents massive outlier data from warping Euclidean distance metrics during clustering.
4. Optimal Cluster Selection (K=4): Evaluates cluster variance using the Elbow Method to map the base into 4 distinct operational tiers.
5. Interactive Visualization & Geographic Diagnostics: Generates statistical scatter plots, population count distributions, and cross-border geographic heatmaps using log-scaling to identify international customer density.

---

📊 Customer Segments Identified

Based on the optimized cluster centroids, the customer base is segmented into four behaviorally transparent tiers:

| Cluster |       Segment Name       | Recency (Avg) | Frequency (Avg Orders) | Monetary (Avg Revenue) | Brief Operational Description |
|    0    | Churned / Lost Customers |   168.2 days  |      1.5 orders        |      $183.29           | Minimal lifetime value; highly inactive; haven't returned in ~6 months. |
|    1    | High-Value Occasional    |   85.4 days   |      2.7 orders        |      $2,234.11         | Solid overall spenders but buy infrequently; away for a couple of months. |
|    2    | Core VIP Customers       |   15.9 days   |      11.9 orders       |      $6,282.36         | Top tier loyalty and spending; highly active core contributors. |
|    3    | Low-Value Hibernating    |   100.2 days  |      2.1 orders        |      $527.40           | Lower transaction profiles; inactive for over 3 months. |


---

## 🚀 Business Benefits & Actionable Strategies

By deploying this segmentation framework, businesses can replace "one-size-fits-all" marketing with hyper-targeted, high-ROI retention campaigns:

* Maximize VIP Retention (Cluster 2): Minimizes churn risk for the highest-value segment through premium loyalty programs, exclusive product bundles, and high-touch service rewards without wasting margin on aggressive price discounts.
* Incentivize Re-engagement (Cluster 1): Triggers personalized cross-selling and automated milestone incentives (e.g., *"Spend \$100 more to unlock VIP Status"*) to successfully transition occasional big-spenders into frequent, loyal core customers.
* Automated Win-Back Triggers (Cluster 3 & 0): Deploys low-cost, programmatic email workflows featuring steep discount win-back codes tailored to historical preferences.
* Optimized Marketing Spend: Prevents budget waste by scaling down expensive customer acquisition costs on dead accounts (Cluster 0) whose reactivation expense exceeds their potential Customer Lifetime Value (CLV).


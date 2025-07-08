# 🛍 Customer Lifetime Value Prediction using Machine Learning

This project estimates the future value a customer brings to a business based on historical purchase behavior. By combining RFM analysis with clustering and probabilistic models, we identify high-value customers and forecast their lifetime value (CLV).

---

## 🔍 Project Overview

📈 Customer acquisition costs are rising, making it essential to focus on customer retention and maximizing value from existing customers. This project implements customer segmentation and CLV prediction to help businesses prioritize their most profitable users.

💡 **Key Idea**: Use transaction data to calculate Recency, Frequency, Monetary value, and Interpurchase Time (RFMT), apply clustering with KMeans, and predict CLV using probabilistic models like BG/NBD and Gamma-Gamma.

---

## 📁 Project Structure

```
customer-lifetime-value-ml/
├── customer.ipynb                      # Main Jupyter notebook
├── customer_lifetime_value_summary.csv # Final output with CLV values
├── requirements.txt                   # Python dependencies
├── dataset/
│   └── online_retail_II.xlsx          # Input dataset
└── README.md                          # Project documentation
```

---

## 📊 Dataset Description

* **Source**: [Online Retail II Dataset on Kaggle](https://www.kaggle.com/datasets/lakshmi25npathi/online-retail-dataset)
* **Total Records**: \~500,000
* **Features Used**:

  * `InvoiceNo`, `CustomerID`, `InvoiceDate`, `Quantity`, `UnitPrice`, `Country`

---

## 🎯 Goals

* Load and clean e-commerce transaction data
* Generate RFMT (Recency, Frequency, Monetary, Interpurchase Time) matrix
* Apply log transformation and standardization
* Perform KMeans clustering to segment customers
* Predict 90-day CLV using BG/NBD and Gamma-Gamma models
* Export results and visualize top customers

---

## ⚙️ Setup Instructions

1. **Clone the repository**

```bash
git clone https://github.com/your-username/customer-lifetime-value-ml.git
cd customer-lifetime-value-ml
```

2. **Create a virtual environment**

```bash
python3 -m venv clv_env
source clv_env/bin/activate
```

3. **Install dependencies**

```bash
pip install -r requirements.txt
```

4. **Add dataset**
   Place the `online_retail_II.xlsx` file inside the `dataset/` folder.

5. **Run the notebook**

```bash
jupyter notebook customer.ipynb
```

---

## 📊 Features Used for Clustering

| Feature             | Description                  |
| ------------------- | ---------------------------- |
| `Recency`           | Days since the last purchase |
| `Frequency`         | Total number of purchases    |
| `Monetary`          | Total amount spent           |
| `InterpurchaseTime` | Avg. time between purchases  |

---

## 🔍 Clustering

### 🎯 KMeans Clustering

* Number of clusters chosen using the Elbow Method (`KElbowVisualizer`)
* Plotted cluster centroids and customer distributions
* Resulted in distinct customer segments (low/high value)

---

## 💰 CLV Prediction

### 📈 Models Used

| Model       | Description                             |
| ----------- | --------------------------------------- |
| BG/NBD      | Models frequency & recency of purchases |
| Gamma-Gamma | Predicts average monetary value         |

```python
from lifetimes import BetaGeoFitter, GammaGammaFitter
```

Predicted:

* Expected purchases in next 90 days
* Expected monetary value per transaction
* Overall CLV = frequency × monetary × expected future transactions

---

## 📊 Results Summary

| Metric            | Value (Sample) |
| ----------------- | -------------- |
| Avg. Recency      | 425 days       |
| Avg. Frequency    | 6.1 purchases  |
| Avg. Monetary     | \$2740.61      |
| Top CLV (90 days) | \$32,000+      |

✅ Exported as: `customer_lifetime_value_summary.csv`

---

## 📈 Visualizations

* 📌 Elbow plot for optimal cluster count
* 🎯 Scatter plot of clusters (Recency vs Frequency)
* 🧾 Bar chart of top 10 customers by CLV
* 📉 Histogram of CLV distribution

---

## 🚀 Future Enhancements

* 🎯 Deploy with Streamlit dashboard
* 🔧 Add time-based cohort analysis
* 📊 Use XGBoost for regression-based CLV prediction
* 🧠 Integrate LTV segmentation with marketing campaigns
* 🧩 Combine with churn prediction for better targeting

---

## 🙌 Acknowledgments

* [Online Retail II Dataset - Kaggle](https://www.kaggle.com/datasets/lakshmi25npathi/online-retail-dataset)
* `lifetimes` Python library for CLV modeling
* scikit-learn for clustering and preprocessing

---



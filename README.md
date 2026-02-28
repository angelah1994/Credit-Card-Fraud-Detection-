# Credit Card Fraud Detection — Exploratory Data Analysis
![Python](https://img.shields.io/badge/Python-3.12-blue) 
![Libraries](https://img.shields.io/badge/Libraries-Pandas%20|%20Seaborn%20|%20Matplotlib-orange)
![Dataset](https://img.shields.io/badge/Dataset-Kaggle-20BEFF)

## 📌 Project Overview
This project performs an in-depth exploratory data analysis (EDA) on a real-world 
credit card transaction dataset to uncover patterns and behaviours that distinguish 
fraudulent transactions from legitimate ones. The analysis focuses purely on 
understanding the data through statistics and visualisation, providing actionable 
insights that could inform fraud prevention strategies.

---

## 📂 Dataset
- **Source:** [Kaggle — Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
- **Size:** 284,807 transactions over 48 hours
- **Features:** 31 columns — Time, Amount, V1–V28 (PCA-anonymised), Class
- **Target:** Class (0 = Legitimate, 1 = Fraud)
- **Missing Values:** None

> Note: Features V1–V28 are anonymised using PCA (Principal Component Analysis) 
> by the issuing bank to protect cardholder privacy. Only Amount and Time retain 
> their original form.

---

## ❓ Business Questions
1. What percentage of transactions are fraudulent?
2. Do fraudulent transactions differ in amount from legitimate ones?
3. At what time of day does fraud occur most frequently?
4. Which features are most strongly associated with fraud?
5. How clearly do key features separate fraud from legitimate transactions?

---

## 🔍 Key Findings

### 1. Extreme Class Imbalance
Out of 284,807 transactions, only 492 were fraudulent — representing just **0.17%** 
of all transactions. For every 1 fraudulent transaction, there are approximately 
578 legitimate ones. A naive system that flags nothing as fraud would still be 
99.83% accurate, highlighting why accuracy alone is a poor metric for fraud detection.

### 2. Transaction Amount Analysis
Fraudulent transactions have a median of just **$9.25** compared to **$22.00** for 
legitimate ones, suggesting fraudsters deliberately keep amounts small to avoid 
detection — a pattern known as "low and slow." Despite this, fraud has a higher 
mean ($122.21 vs $88.29) due to a small number of large fraudulent transactions 
inflating the average. The maximum legitimate transaction ($25,691) far exceeds 
the maximum fraud transaction ($2,125), confirming fraudsters rarely attempt 
high-value transactions.

### 3. Time of Day Analysis
Fraud peaks at **2am (57 transactions)**, a window when most cardholders are 
asleep and unlikely to notice suspicious activity. Secondary spikes occur at 11am 
and 6pm. Legitimate transactions follow a smooth human behaviour curve, peaking 
at 9pm. The erratic, spiky nature of fraud activity across hours stands in sharp 
contrast to the predictable rhythm of normal transactions.

### 4. Correlation Analysis
The features most negatively correlated with fraud are **V17 (-0.33), V14 (-0.30), 
V12 (-0.26), and V10 (-0.22)**, while **V11 (0.15) and V4 (0.13)** are the strongest 
positive signals. No single feature dominates, reflecting the complexity of fraud 
detection. The V features are largely independent of each other, as expected from 
PCA-generated components.

### 5. Key Feature Distributions
Boxplot analysis confirms that V17, V14, V12, and V10 shift dramatically into 
negative territory for fraud, while V11 and V4 shift upward. The limited overlap 
between fraud and legitimate distributions across these features makes them strong 
behavioural indicators. Any transaction showing simultaneously low V17, V14, V12 
and high V11, V4 values should be treated as a high-priority fraud alert.

---

## 🛠️ Tools & Libraries
| Tool | Purpose |
|------|---------|
| Python 3.12 | Core programming language |
| Pandas | Data manipulation and analysis |
| Matplotlib | Data visualisation |
| Seaborn | Statistical visualisation |
| Jupyter Notebook | Interactive development environment |

---

## 📁 Project Structure
```
creditcard_fraud_eda/
│
├── data/
│   └── creditcard.csv          # Raw dataset (download from Kaggle)
├── notebooks/
│   └── fraud_eda.ipynb         # Main analysis notebook
├── visuals/
│   ├── class_distribution.png
│   ├── amount_distribution.png
│   ├── fraud_by_hour.png
│   ├── correlation_heatmap.png
│   └── feature_boxplots.png
└── README.md
```

---

## ▶️ How to Run
1. Clone the repository
```bash
git clone https://github.com/yourusername/creditcard-fraud-eda.git
```
2. Install dependencies
```bash
pip install pandas matplotlib seaborn jupyter
```
3. Download the dataset from [Kaggle](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud) 
and place it in the `/data` folder
4. Launch Jupyter Notebook
```bash
jupyter notebook notebooks/fraud_eda.ipynb
```

---

## 💡 Business Recommendations
- Implement **stricter authentication between midnight and 3am** when fraud peaks
- Flag transactions with simultaneously low V17, V14, V12 and high V11, V4 as 
high-risk for manual review
- Avoid relying on transaction amount alone as a fraud signal — fraudsters 
deliberately keep amounts small
- Build monitoring dashboards that track hourly fraud rates in real time

---

## 👤 Author
**Your Name**  
[LinkedIn](https://linkedin.com/in/yourprofile) | [GitHub](https://github.com/yourusername)

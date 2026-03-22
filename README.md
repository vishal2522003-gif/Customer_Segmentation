# Customer Segmentation using RFM Analysis & K-Means Clustering

A data science project that groups retail customers into meaningful segments based on their buying behaviour, using RFM analysis and unsupervised machine learning.

---

## Overview

Understanding who your customers are and how they behave is one of the most useful things a business can do. This project takes transactional data from an online retail store and turns it into clear, actionable customer segments — helping a business decide where to focus its marketing effort and budget.

The analysis covers over **541,000 transactions** from a UK-based online retailer between December 2010 and December 2011, and ultimately segments **4,212 customers** into four distinct groups.

---

## Dataset

The data comes from the [UCI Machine Learning Repository — Online Retail Dataset](https://archive.ics.uci.edu/ml/datasets/Online+Retail).

| Column | Description |
|---|---|
| InvoiceNo | Unique invoice number |
| StockCode | Product code |
| Description | Product name |
| Quantity | Units purchased |
| InvoiceDate | Date and time of transaction |
| UnitPrice | Price per unit (£) |
| CustomerID | Unique customer identifier |
| Country | Country of the customer |

---

## Methodology

### 1. Data Cleaning
- Removed 135,080 rows with missing CustomerID values
- Filtered out cancelled orders (invoices starting with 'C')
- Removed records with negative quantities or prices

### 2. RFM Feature Engineering
RFM is a proven method for measuring customer value based on three dimensions:

- **Recency (R)** — How many days since the customer last made a purchase
- **Frequency (F)** — How many times the customer has purchased
- **Monetary (M)** — How much the customer has spent in total

Using December 10, 2011 as the reference date, an RFM table was built for each customer. Extreme outliers (top 1%) were removed to avoid distorting the clusters.

### 3. Normalisation
Since recency, frequency, and monetary values sit on very different scales, all three were standardised using `StandardScaler` before feeding them into the clustering model.

### 4. K-Means Clustering
The Elbow Method was used to test values of K from 2 to 10. The inertia curve showed a clear bend at **K=4**, making four clusters the natural choice.

---

## Results

Four customer segments were identified:

| Segment | Customers | % of Base | Avg Recency | Avg Frequency | Avg Spend |
|---|---|---|---|---|---|
| 🏆 Champions | 221 | 5.2% | 20 days | 15.0 purchases | £6,815 |
| ⭐ Loyal Customers | 843 | 20.0% | 31 days | 6.8 purchases | £2,567 |
| ⚠️ At Risk | 2,158 | 51.2% | 51 days | 2.2 purchases | £652 |
| 💤 Lost Customers | 990 | 23.5% | 246 days | 1.5 purchases | £439 |

### Segment Breakdown

**Champions (5.2%)** — The most valuable customers. They buy frequently, spend the most, and purchased very recently. Priority should be keeping them engaged through loyalty rewards, early product access, and personalised outreach.

**Loyal Customers (20%)** — Strong, consistent buyers with good spending and recency. A solid base to build on. Upselling and referral programmes tend to work well here.

**At Risk (51.2%)** — The largest group by far. They have bought before but are showing signs of disengagement. A well-timed win-back campaign with a relevant offer could recover a meaningful share of this group.

**Lost Customers (23.5%)** — Customers who have not purchased in a long time and had low engagement to begin with. Re-engagement is possible but requires a stronger incentive, such as a significant discount or a direct reminder of value.

---

## Key Findings

✅ **5.2% of customers (Champions) drive disproportionate value** — averaging £6,815 in lifetime spend vs. £439 for Lost Customers

✅ **51% of the customer base is At Risk** — showing early signs of churn but still recoverable with targeted campaigns

✅ **Recovery opportunity: £487K+** — If 30% of At Risk and 15% of Lost Customers return through win-back campaigns

✅ **K=4 clusters emerged naturally** — Elbow Method validated that four distinct behavioural groups exist in the data

---

## Business Impact

This analysis enables:

- **Targeted marketing** — Different campaigns for Champions (retain) vs. At Risk (win back)
- **Budget optimisation** — Allocate 60% of retention budget to 5% of customers (Champions) for maximum ROI
- **Churn prevention** — Early warning system for customers showing At Risk behaviour patterns
- **Revenue forecasting** — Predict customer lifetime value based on segment membership

---

## Visualisations

The following charts are saved in the `Figures/` folder:

- `rfm_distributions.png` — Distribution of Recency, Frequency, and Monetary values across all customers
- `elbow_curve.png` — Elbow Method plot used to determine the optimal number of clusters
- `segment_analysis.png` — Comparison of all four segments across RFM dimensions
- `cluster_3d_visualization.png` — 3D scatter plot of customer clusters in RFM space

---

## Project Structure

```
Customer_Segmentation/
│
├── Code.ipynb                  # Main analysis notebook
│
├── Data/
│   ├── data.csv                # Raw transaction dataset
│   └── customer_segments.csv  # Final segmented customer output
│
├── Figures/
│   ├── rfm_distributions.png
│   ├── elbow_curve.png
│   ├── segment_analysis.png
│   └── cluster_3d_visualization.png
│
├── README.md
└── requirements.txt            # Python dependencies
```

---

## How to Run

**Prerequisites:** Python 3.8+

Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

Then open and run `Code.ipynb` from top to bottom in Jupyter Notebook or JupyterLab. The cleaned segments will be saved automatically to `Data/customer_segments.csv`.

---

## Tools & Libraries

- **Python 3** — Core language
- **pandas** — Data manipulation
- **numpy** — Numerical operations
- **matplotlib / seaborn** — Data visualisation
- **scikit-learn** — K-Means clustering and data normalisation

---

## About

**Vishal Kumar**
MSc Data Analytics & AI — EDHEC Business School
Actively seeking analytics/consulting internship opportunities starting June 2026. Open to roles in France, Luxembourg, and Belgium.

- Email: vishal.kumar@edhec.com
- LinkedIn: [linkedin.com/in/vishalkr252](https://linkedin.com/in/vishalkr252)
- GitHub: [github.com/Vishal-VK-Kumar](https://github.com/Vishal-VK-Kumar)

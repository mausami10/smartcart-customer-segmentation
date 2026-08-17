# smartcart-customer-segmentation
Unsupervised customer segmentation using PCA and K-Means/Agglomerative clustering to identify high-value vs budget-conscious shopper segments.
# SmartCart — Customer Segmentation

An unsupervised machine learning project that segments retail customers into distinct groups based on spending behaviour, income, and demographics, to support targeted marketing.

## Problem

Not all customers are equally valuable or respond to the same offers. This project groups ~2,240 customers into behaviourally distinct segments so marketing spend can be targeted more effectively.

## Dataset

`smartcart_customers.csv` — 2,240 customers with demographics (birth year, education, marital status, income, household composition), purchase history by product category, purchase channel, and campaign response.

> Add your dataset source/link here (e.g. Kaggle) if you can share it, or a short note on how to obtain it.

## Approach

1. **Data cleaning** — filled missing income values with the median.
2. **Feature engineering** — derived age, customer tenure (days), total spending, total children, and simplified education/marital status categories.
3. **Outlier removal** — dropped customers aged 90+ or with income above £600k.
4. **Dimensionality reduction** — PCA to 3 components (~45% variance explained) after one-hot encoding and scaling.
5. **Clustering** — determined K=4 via elbow method + silhouette score, then compared K-Means and Agglomerative Clustering.
6. **Cluster profiling** — summarised each segment by average income, spending, family size, and campaign response.

## Results — customer segments

| Segment | Income | Spending | Household | Campaign response |
|---|---|---|---|---|
| High-value singles | ~£70k | ~£1,111 | Single, fewer children | 35% (highest) |
| High-value couples | ~£67k | ~£969 | Couple | 14% |
| Budget-conscious singles | ~£38.5k | ~£175 | Single, more children | 12% |
| Budget-conscious couples | ~£35k | ~£105 | Couple, more children | 7% (lowest) |

**Takeaway:** marketing spend is best directed at the two high-income, high-response segments; the two budget-conscious segments likely respond better to value-oriented promotions than premium campaigns.

## Tech stack

Python, pandas, numpy, seaborn, matplotlib, scikit-learn, kneed

## How to run

```bash
pip install -r requirements.txt
jupyter notebook SmartCart.ipynb
```

Run all cells top to bottom (`Kernel → Restart & Run All`) to reproduce the results above.

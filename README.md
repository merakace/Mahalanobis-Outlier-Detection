# Mahalanobis Distance for Multivariate Outlier Detection

**Course:** 25MSDA3H01 – Multivariate Data Analysis

## Project objective
Use Python, NumPy and Pandas to calculate Mahalanobis distance, identify multivariate outliers in a multivariate-normal dataset, create pairwise scatter plots, and validate the manual calculation against SciPy.

## Repository structure
```text
mahalanobis_outlier_detection/
├── data/
│   └── multivariate_dataset.csv
├── outputs/
│   ├── covariance_matrix.csv
│   ├── mahalanobis_results.csv
│   ├── metrics_summary.txt
│   └── pairwise_scatter_matrix.png
├── Mahalanobis_Outlier_Detection.ipynb
├── requirements.txt
└── README.md
```

## Setup
Python 3.9+ is recommended.

```bash
python -m venv .venv
# Windows:
.venv\\Scripts\\activate
# macOS/Linux:
source .venv/bin/activate

pip install -r requirements.txt
jupyter notebook
```

Open `Mahalanobis_Outlier_Detection.ipynb` and run all cells from top to bottom.

## Method
1. Load the CSV with Pandas.
2. Select the three numeric features.
3. Calculate the sample mean and covariance matrix manually:
   `S = (X - mean).T @ (X - mean) / (n - 1)`
4. Calculate squared Mahalanobis distance:
   `(x - mean).T @ inverse(S) @ (x - mean)`
5. Compare squared distances with the 99th percentile of a chi-square distribution with `p` degrees of freedom.
6. Validate distances using `scipy.spatial.distance.mahalanobis`.
7. Visualize feature relationships using a pairwise scatter matrix.

## Reproducibility
The included dataset is generated with NumPy random seed `42`. The CSV is included so the notebook can be run without regenerating data. The outputs folder contains the calculated example metrics and plot.

## Interpretation
Mahalanobis distance accounts for covariance among variables, unlike ordinary Euclidean distance. A large squared distance may indicate a multivariate outlier. The chi-square threshold is based on a multivariate-normality assumption; inspect assumptions before applying it to real-world data.

## Tools
Python, NumPy, Pandas, Matplotlib, Seaborn, SciPy, Jupyter Notebook, GitHub.

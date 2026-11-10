# K-Means vs Mini-Batch K-Means on UCI Online Retail

Reproducible experiment accompanying the article
"Effect of Training Data Size on the Quality and Efficiency of K-Means
and Mini-Batch K-Means on Retail Transaction Data".

## Contents
- `Online_Retail_KMeans_MiniBatch_Reproducible.ipynb`: full experiment
- `results/`: raw results, summary (mean/SD), paired tests, parameters, metadata

## Design
- Dataset: UCI Online Retail [DOI: 10.24432/C5BW33], 530,104 rows after cleaning
- Group-aware 80/20 split by InvoiceNo; fixed evaluation sample of 10,000 rows
- Training sizes: 1,000 to 100,000 rows (nested within each seed), 30 seeds (42-71)
- Feature scenarios: (A) Quantity, UnitPrice; (B) + TotalAmount; log1p + z-score
- K = 5; K-Means (Lloyd) vs MiniBatchKMeans; n_init = 1 and 10
- Metrics: Silhouette, Davies-Bouldin, Calinski-Harabasz, held-out inertia, ARI, fit time
- Statistics: paired exact Wilcoxon, Holm correction, rank-biserial effect size

## Data
The dataset is not redistributed here. Download `Online Retail.xlsx` from the
UCI Machine Learning Repository. Expected SHA-256:
`43465a06f2ccf7c8b5bd2892bc7defb52f97487934fe93b16ae4c3936424676d`

## Reproducing
Run the notebook (Google Colab or local) with scikit-learn 1.8.0.
Fit times depend on hardware; quality metrics are deterministic given the seeds.
Memory usage was not measured.


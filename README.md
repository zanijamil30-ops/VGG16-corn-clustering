# 🌽 Corn / Seeds Clustering — Short README

A compact unsupervised ML pipeline for clustering seed/kernel images using **color histograms**, **LBP texture**, and **deep VGG16 (512-D) features**.  
Best results were achieved with **K-Means on VGG16 embeddings**.

---

## 🔗 Links

- 🌐 **Kaggle Dataset:** https://www.kaggle.com/datasets/muratkokludataset/pumpkin-seeds-dataset

---

## ⚙️ Quick Overview

- **Data:** ~1,050 RGB images (3 classes), resized to `224×224`
- **Features:** Color Histograms, LBP, VGG16
- **Dimensionality Reduction:** PCA, t-SNE, UMAP
- **Clustering:** K-Means, GMM, Hierarchical, Spectral, DBSCAN
- **Evaluation:** Silhouette, DBI, CH, ARI, NMI + Confusion Matrix

---

## ▶️ Quick Start

### 1️⃣ Install
pip install -r requirements.txt

### 2️⃣ Run Pipeline
python main.py

### Outputs
results/          # feature files, predictions, metrics.json  
visualizations/   # PCA, t-SNE, UMAP, dendrogram, sample grids  

## 📈 Results Summary

| Algorithm            | ARI      | NMI      | Notes                                |
|---------------------:|:--------:|:--------:|:-------------------------------------|
| **K-Means (VGG16)**  | **0.991**| **0.983**| ✅ Best performer                     |
| GMM                  | 0.991    | 0.983    | Similar performance                   |
| Spectral / Hierarch. | 0.97–0.99| 0.95–0.98| Very good                             |
| DBSCAN               | Poor     | Poor     | ❌ Not suitable for high-dimensional features |


### 📝 Notes & Tips
Set seeds: np.random.seed(42), random.seed(42)

Save intermediate arrays: features_combined.npy, meta.npy

Visual validation: sample grids + centroid images help confirm cluster quality

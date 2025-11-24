🌽 Corn / Seeds Clustering — Short README

A compact, easy-to-run unsupervised pipeline for clustering seed/kernel images using color, texture (LBP) and deep (VGG16) features.
Best results were achieved with K-Means on VGG16 embeddings.

🔗 Links

📁 Local Dataset (uploaded)
/mnt/data/Corn_3_Classes_Image_Dataset.zip

🌐 Kaggle Dataset
https://www.kaggle.com/datasets/muratkokludataset/pumpkin-seeds-dataset

⚙️ Quick Overview

📂 Data: ~1,050 RGB images (3 classes), resized to 224×224.

🧩 Features: Color histograms, LBP texture, VGG16 (512-D) embeddings.

📉 Dimensionality Reduction: PCA, t-SNE, UMAP.

🤖 Clustering: K-Means, GMM, Hierarchical, Spectral, DBSCAN.

📊 Evaluation: Silhouette, DBI, CH, ARI, NMI + Confusion Matrix.

▶️ Quick Start
# 1) install
pip install -r requirements.txt

# 2) run pipeline
python main.py

# outputs:
results/          # feature files, predictions, metrics.json
visualizations/   # PCA, t-SNE, UMAP, dendrogram, sample grids

📈 Results Summary
Algorithm	ARI	NMI	Notes
K-Means (VGG16)	≈ 0.991	≈ 0.983	✅ Best performer
GMM	≈ 0.991	≈ 0.983	Similar to K-Means
Spectral / Hierarchical	0.97–0.99	0.95–0.98	Very good
DBSCAN	Poor	Poor	Not suitable for high-dimensional features
📝 Notes & Tips

🔁 Set seeds for reproducibility: np.random.seed(42), random.seed(42)

💾 Save intermediate arrays (features_combined.npy, meta.npy)

📷 Visual checks (sample grids + centroid images) help validate clusters

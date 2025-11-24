🌽 Corn Kernel Clustering — Unsupervised Machine Learning Project

A complete unsupervised ML pipeline for clustering corn kernel images using traditional features (color histograms, LBP) and deep learning features (VGG16).
Multiple clustering algorithms are compared and evaluated using internal and external metrics.

📁 Project Structure
corn-kernel-clustering/
│
├── main.py                  # full end-to-end pipeline (preprocess → features → clustering)
├── requirements.txt         # required Python libraries
├── README.md                # project documentation
├── .gitignore               # ignored files
│
├── results/                 # generated outputs (metrics, predictions)  [gitignored]
│   └── README.md
│
├── visualizations/          # PCA, t-SNE, UMAP plots + sample images   [gitignored]
│
└── data/                    # dataset location (optional)
    ├── raw/                 # original dataset ZIP (ignored)
    └── processed/           # resized 224×224 images (ignored)

🔧 1. About the Project

This project performs unsupervised clustering to automatically group images of three Zea mays (corn) varieties without using labels:

Zea_mays_Chulpi_Cancha

Zea_mays_Indurata

Zea_mays_Rugosa

A complete ML pipeline is implemented:

Image preprocessing

Feature extraction

Dimensionality reduction

Clustering

Evaluation (internal & external)

Visualization

🔍 2. Dataset Overview

1,050 total images

Balanced classes (350 per variety)

All images resized to 224 × 224 RGB

Used for representation learning and unsupervised classification

🧠 3. Feature Extraction
3.1 Color Histograms (RGB – 8 bins × 3 channels)

Captures global color distribution

Functions used:

numpy.histogram()

numpy.concatenate()

Pros: fast, simple

Cons: no texture or shape information

3.2 Local Binary Patterns (LBP)

Captures surface texture patterns

Useful because corn kernels differ in surface structure

Functions used:

skimage.feature.local_binary_pattern()

skimage.color.rgb2gray()

Feature dimension: P + 2 bins

3.3 Deep Features (VGG16 – Best Performer)

VGG16 pretrained on ImageNet

Extracted 512-D deep embeddings from the avg-pooling layer

Functions used:

tensorflow.keras.applications.vgg16.VGG16()

preprocess_input()

model.predict()

Why deep features work best:

Capture shape, edges, texture, color, and semantic information

Provide highly discriminative representations

Led to ARI ≈ 0.99, NMI ≈ 0.98

📉 4. Dimensionality Reduction
4.1 PCA (Principal Component Analysis)

Reduces dimensionality

Useful for 2D/3D visualization

Speeds up t-SNE

sklearn.decomposition.PCA().fit_transform()

4.2 t-SNE

Non-linear dimensionality reduction

Reveals complex structure and cluster separation

sklearn.manifold.TSNE()

4.3 UMAP

Faster and more scalable than t-SNE

Preserves local + global manifold structure

umap.UMAP().fit_transform()

🤖 5. Clustering Algorithms
5.1 K-Means (Primary Model)

Minimizes within-cluster variance

Stable + fast

Strong performance with deep embeddings

sklearn.cluster.KMeans()

5.2 Gaussian Mixture Models (GMM)

Soft (probabilistic) clustering

sklearn.mixture.GaussianMixture()

5.3 Hierarchical Clustering

Creates dendrogram to visualize merges

scipy.cluster.hierarchy.linkage()

scipy.cluster.hierarchy.dendrogram()

5.4 DBSCAN

Density-based clustering

Good for noise/outlier detection

Struggled due to high-dimensional space

sklearn.cluster.DBSCAN()

5.5 Spectral Clustering

Graph-based clustering

Works for non-spherical clusters

sklearn.cluster.SpectralClustering()

📊 6. Evaluation Metrics
6.1 Internal Metrics (Unsupervised)
Metric	Meaning	Good When	Function
Silhouette Score	Separation between clusters	→ closer to 1	silhouette_score()
Davies–Bouldin Index	Cluster compactness	→ closer to 0	davies_bouldin_score()
Calinski–Harabasz	Variance ratio	→ higher is better	calinski_harabasz_score()

Observed Values:

Silhouette ≈ 0.13

DB Index ≈ 2.80

CH Score ≈ 116

(Silhouette low due to high-dimensional deep embeddings — normal + acceptable)

6.2 External Metrics (Using True Labels for Analysis Only)
Metric	Meaning	Range	Function
ARI	Matching predicted vs true labels	0 → 1	adjusted_rand_score()
NMI	Shared information	0 → 1	normalized_mutual_info_score()

Observed:

ARI ≈ 0.9914

NMI ≈ 0.9834

Excellent performance.

6.3 Confusion Matrix

sklearn.metrics.confusion_matrix()

Nearly perfect diagonal → clusters match real classes almost exactly.

🖼️ 7. Visualizations
Visualization	Purpose
PCA plot	Linear separability check
t-SNE plot	Non-linear structure visualization
UMAP plot	Preserves local/global geometry
Sample images per cluster	Qualitative cluster validation
Centroid images	Representative cluster images
Dendrogram	Visualizes hierarchical merging

Visualizations saved in:
/visualizations/

🏆 8. Results Summary
Clustering Performance Comparison
Algorithm	ARI	NMI	Remarks
K-Means	0.991	0.983	★ Best performer
GMM	0.991	0.983	Same as K-Means
Spectral	0.988	0.979	Very strong
Hierarchical	0.972	0.954	Good
DBSCAN	Poor	Poor	Failed due to high-dimensional space
🧠 9. Why K-Means + VGG16 Is the Best Model

K-Means with deep VGG16 embeddings consistently produced the highest clustering accuracy.
This combination is:

Highly discriminative (captures texture, shape, color)

Fast and stable

Nearly identical to true class labels

Simple to implement and deploy

With ARI ≈ 0.99 and NMI ≈ 0.98, it is the most reliable and practical model for real-world use.

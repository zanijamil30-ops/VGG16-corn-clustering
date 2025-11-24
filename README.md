🌽 Corn Kernel Clustering — Unsupervised Machine Learning Pipeline

This project performs unsupervised clustering on corn kernel images using a complete computer vision + machine learning pipeline.
It extracts visual features (color, texture, deep learning), applies dimensionality reduction (PCA, t-SNE, UMAP), runs multiple clustering algorithms, and evaluates how well the model discovers the three corn varieties.

📁 Dataset

The dataset contains 1,050 images of three Zea mays varieties:

Zea_mays_Chulpi_Cancha

Zea_mays_Indurata

Zea_mays_Rugosa

Each class has ~350 RGB images.

Example dataset ZIP path used during development:

/mnt/data/Corn_3_Classes_Image_Dataset.zip

🔧 Project Structure
corn-clustering/
│
├── main.py                # complete pipeline
├── requirements.txt       # install dependencies
├── README.md              # project description
├── .gitignore             # ignore cache & generated files
│
├── results.jpeg             
└── visualizations.jpeg

🚀 Pipeline Overview

This project contains six core steps, all implemented in main.py.

1. Preprocessing

Unzip dataset

Resize images to 224×224

Convert to RGB

Store processed images

Libraries Used:
PIL, glob, os

2. Feature Extraction

Three complementary feature types were extracted:

✔ Color Histograms

RGB histogram (8 bins × 3 channels)

Captures overall color tone

numpy.histogram()

✔ Local Binary Patterns (LBP)

Captures texture micro-patterns

skimage.feature.local_binary_pattern()

✔ VGG16 Deep Features (Best Performers)

Pretrained CNN on ImageNet

512-dimensional embeddings

tensorflow.keras.applications.vgg16

3. Dimensionality Reduction
✔ PCA

Linear reduction

Helps visualize clusters in 2D/3D

✔ t-SNE

Non-linear visualization

Reveals natural grouping

✔ UMAP

Faster, preserves structure well

Libraries: sklearn, umap-learn

4. Clustering Algorithms

Multiple clustering algorithms were applied and compared:

K-Means (Best performer)

Gaussian Mixture Models (GMM)

Hierarchical Clustering

DBSCAN

Spectral Clustering

Libraries: sklearn.cluster, scipy.cluster.hierarchy

5. Evaluation Metrics
Internal Metrics

Evaluate clustering without labels:

Metric	Meaning
Silhouette Score	Separation quality
Davies–Bouldin Index	Cluster compactness
Calinski–Harabasz Score	Variance ratio
External Metrics

(Used only for analysis, not training)

Metric	Meaning
ARI	matches predicted vs. true labels
NMI	shared information
Confusion Matrix

Shows cluster ↔ true class alignment.

6. Visualization

Figures include:

PCA clusters

t-SNE clusters

UMAP clusters

Sample images per cluster

Centroid (representative) images

Hierarchical dendrogram

All plots saved to /visualizations/.

⭐ Results Summary
Algorithm	ARI	NMI
K-Means	≈ 0.991	≈ 0.983
GMM	≈ 0.991	≈ 0.983
Spectral	≈ 0.988	≈ 0.979
Hierarchical	≈ 0.972	≈ 0.954
DBSCAN	Very poor	Very poor

✔ Deep VGG16 embeddings + KMeans achieved near-perfect unsupervised clustering.
✔ Clear separation in PCA, t-SNE, and UMAP visualizations.
✔ Confusion matrix shows clusters almost perfectly match real classes.

🧪 How to Run
1. Install dependencies
pip install -r requirements.txt

2. Place dataset ZIP in data/ or anywhere local.
3. Run the full pipeline
python main.py


Outputs will be saved in:

/results/

/visualizations/

📌 Technologies Used

Python

NumPy

Scikit-Learn

SciPy

Matplotlib

Scikit-Image

TensorFlow / Keras

UMAP

📄 License

 MIT License

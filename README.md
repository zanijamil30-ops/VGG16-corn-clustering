<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8"/>
  <title>Corn Kernel Clustering — README</title>
  <style>
    body { font-family: Arial, Helvetica, sans-serif; line-height:1.5; max-width:800px; margin:36px auto; color:#111; }
    h1 { color:#2b6cb0; }
    h2 { color:#2c5282; margin-top:1.2em; }
    p { margin:0.6em 0; }
    pre { background:#f7fafc; padding:12px; border:1px solid #e2e8f0; overflow:auto; }
    a.button { display:inline-block; padding:8px 12px; background:#2b6cb0; color:#fff; text-decoration:none; border-radius:4px; }
    ul { margin:0.2em 0 0.8em 1.2em; }
    .note { font-size:0.95em; color:#4a5568; }
  </style>
</head>
<body>
  <h1>Corn Kernel Clustering — Short README</h1>

  <p><strong>Purpose:</strong> Unsupervised clustering pipeline for <em>Zea mays</em> kernel images using color histograms, LBP, and VGG16 embeddings. Best results obtained with <strong>K-Means on VGG16 features</strong>.</p>

  <h2>Quick Links</h2>
  <p>
    <strong>Dataset (local):</strong>
    <!-- local path provided as-is so environment/tooling can convert it to a URL -->
    <a class="button" href="/mnt/data/Corn_3_Classes_Image_Dataset.zip">/mnt/data/Corn_3_Classes_Image_Dataset.zip</a>
  </p>

  <h2>How to run</h2>
  <p>Install dependencies and run the single script:</p>
  <pre>
pip install -r requirements.txt
python main.py
  </pre>

  <h2>Outputs</h2>
  <ul>
    <li><strong>results/</strong> — saved feature matrices, predicted labels, metrics.json</li>
    <li><strong>visualizations/</strong> — PCA, t-SNE, UMAP plots, sample grids, dendrogram</li>
  </ul>

  <h2>Core files</h2>
  <ul>
    <li><strong>main.py</strong> — end-to-end pipeline (preprocess → features → reduce → cluster → evaluate → visualize)</li>
    <li><strong>requirements.txt</strong> — required packages</li>
  </ul>

  <p class="note"><strong>Tip:</strong> The dataset path above is the local file uploaded during development. If running elsewhere, place the dataset ZIP at that path or update <code>main.py</code> to point to your dataset location.</p>

  <footer style="margin-top:1.6em; font-size:0.9em; color:#718096;">
    Created for: Corn Kernel Clustering project — compact README (HTML)
  </footer>
</body>
</html>

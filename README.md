<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8"/>
  <title>📦 Corn / Seeds Clustering — Short README</title>
  <meta name="viewport" content="width=device-width,initial-scale=1"/>
  <style>
    body { font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial; max-width:900px; margin:28px auto; color:#111; line-height:1.5; padding:0 18px; }
    h1 { color:#0b5cff; margin-bottom:6px; }
    h2 { color:#0a4aa6; margin-top:20px; }
    .lead { color:#334155; margin-bottom:12px; }
    .btn { display:inline-block; margin:6px 8px 6px 0; padding:8px 12px; background:#0b5cff; color:#fff; border-radius:6px; text-decoration:none; font-weight:600; }
    .btn--muted { background:#edf2ff; color:#0b5cff; border:1px solid #dbeafe; }
    pre { background:#f8fafc; padding:12px; border-left:3px solid #e2e8f0; overflow:auto; border-radius:6px; }
    ul { margin:6px 0 12px 1.1em; }
    .meta { font-size:0.95em; color:#475569; }
    footer { margin-top:26px; color:#64748b; font-size:0.9em; }
    .emoji { font-size:1.05em; margin-right:6px; }
  </style>
</head>
<body>
  <h1>🌽 Corn / Seeds Clustering — Short README</h1>
  <p class="lead">A compact, easy-to-run unsupervised pipeline for clustering seed/kernel images using **color**, **texture (LBP)** and **deep (VGG16)** features. Best results were achieved with <strong>K-Means on VGG16 embeddings</strong>.</p>

  <h2>🔗 Links</h2>
  <p>
    <!-- Local dataset path (development environment) -->
    <a class="btn" href="/mnt/data/Corn_3_Classes_Image_Dataset.zip" title="Local dataset (uploaded)"><span class="emoji">📁</span>Local dataset</a>

    <!-- Kaggle dataset link shared by user -->
    <a class="btn btn--muted" href="https://www.kaggle.com/datasets/muratkokludataset/pumpkin-seeds-dataset" target="_blank" title="Kaggle dataset"><span class="emoji">🌐</span>Kaggle: Pumpkin Seeds</a>
  </p>

  <h2>⚙️ Quick Overview</h2>
  <ul>
    <li>📂 <strong>Data:</strong> ~1,050 RGB images (3 classes), resized to <code>224×224</code>.</li>
    <li>🧩 <strong>Features:</strong> Color histograms, LBP texture, VGG16 (512-D) deep embeddings.</li>
    <li>📉 <strong>Dimensionality:</strong> PCA, t-SNE, UMAP used for visualization.</li>
    <li>🤖 <strong>Clustering:</strong> K-Means (primary), GMM, Hierarchical, DBSCAN, Spectral.</li>
    <li>📊 <strong>Evaluation:</strong> Silhouette, Davies-Bouldin, Calinski-Harabasz (internal); ARI, NMI, confusion matrix (external).</li>
  </ul>

  <h2>▶️ Quick Start</h2>
  <pre>
# 1) install
pip install -r requirements.txt

# 2) run (single-script pipeline)
python main.py

# outputs:
results/          # features, predictions, metrics.json
visualizations/   # PCA, t-SNE, UMAP plots, sample grids
  </pre>

  <h2>📈 Results (summary)</h2>
  <p class="meta">(Short summary of clustering performance observed in experiments)</p>
  <table style="border-collapse:collapse; margin-top:8px;">
    <tr>
      <th style="text-align:left; padding:8px 12px; border-bottom:1px solid #e2e8f0;">Algorithm</th>
      <th style="text-align:left; padding:8px 12px; border-bottom:1px solid #e2e8f0;">ARI</th>
      <th style="text-align:left; padding:8px 12px; border-bottom:1px solid #e2e8f0;">NMI</th>
      <th style="text-align:left; padding:8px 12px; border-bottom:1px solid #e2e8f0;">Notes</th>
    </tr>
    <tr>
      <td style="padding:8px 12px;">K-Means (VGG16)</td>
      <td style="padding:8px 12px;">≈ 0.991</td>
      <td style="padding:8px 12px;">≈ 0.983</td>
      <td style="padding:8px 12px;">✅ Best performer</td>
    </tr>
    <tr>
      <td style="padding:8px 12px;">GMM</td>
      <td style="padding:8px 12px;">≈ 0.991</td>
      <td style="padding:8px 12px;">≈ 0.983</td>
      <td style="padding:8px 12px;">Similar to K-Means</td>
    </tr>
    <tr>
      <td style="padding:8px 12px;">Spectral / Hierarchical</td>
      <td style="padding:8px 12px;">0.97–0.99</td>
      <td style="padding:8px 12px;">0.95–0.98</td>
      <td style="padding:8px 12px;">Good</td>
    </tr>
    <tr>
      <td style="padding:8px 12px;">DBSCAN</td>
      <td style="padding:8px 12px;">Poor</td>
      <td style="padding:8px 12px;">Poor</td>
      <td style="padding:8px 12px;">Not suitable (high-dim features)</td>
    </tr>
  </table>

  <h2>📝 Notes & Tips</h2>
  <ul>
    <li>🔁 Use reproducible seeds: <code>np.random.seed(42)</code>, <code>random.seed(42)</code>.</li>
    <li>💾 Save intermediate outputs (<code>features_combined.npy</code>, <code>meta.npy</code>) to speed experiments.</li>
    <li>📷 Visual checks (sample grids & centroid images) are very helpful for qualitative validation.</li>
  </ul>

  <footer>
    <small>Made for quick use — click the <strong>Local dataset</strong> button to open the uploaded ZIP in your environment. ✨</small>
  </footer>
</body>
</html>

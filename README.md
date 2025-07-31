
<h1 align="center" style="color:#4A90E2;">KDiscShapeNet</h1>
<h3 align="center">A Structure-Aware Time Series Clustering Model with Supervised Contrastive Learning</h3>

---

## 🌐 Overview

**KDiscShapeNet** is a clustering method based on the **Kolmogorov–Arnold Network (KAN)**, designed to process and cluster sequential time series data. It integrates:

- **Supervised Contrastive Loss (SupCon)**
- **Center Loss**
- **Differentiable K-Shape Loss**

These techniques jointly enhance clustering **performance**, **stability**, and **flexibility**.

It supports multiple benchmark datasets (e.g., Trace, ECG200, Beef, StarLightCurves) and evaluates clustering quality using **t-SNE visualization** and metrics such as **ARI**, **NMI**, and **Silhouette Score**.

---

## ✨ Key Features

- 🧠 **KAN Network**: Captures complex, nonlinear relationships in time series.
- 🧲 **Supervised Contrastive Loss**: Enhances feature separability by label guidance.
- 🎯 **Center Loss**: Forces samples toward their class centers.
- 🔁 **Differentiable K-Shape Loss**: Ensures prototype alignment with shape patterns.
- 📉 **t-SNE Visualization**: High-dimensional feature space visualization.

---

## 📦 Dependencies

Make sure the following libraries are installed:

```bash
pip install numpy==1.21.5 torch==1.10.0 scikit-learn==0.24.2 \
            matplotlib==3.4.3 seaborn==0.11.2 tqdm==4.62.3 scipy==1.7.3
```

Also, ensure `pykan` is available and `KANLayer` can be imported from `pykan_local/kan`.

> ⚠️ **Before running the project, deploy the KAN network first.**

---

## 📁 Dataset

Supported datasets:

- Trace (TRAIN/TEST)
- ECG200
- ItalyPowerDemand
- Beef
- SonyAIROBotSurface1
- GunPoint
- StarLightCurves
- **ETTh1 & ETTh2** (Hourly data)
- **ETTm1 & ETTm2** (15-min interval data)

Each `.tsv` file format:

| Column       | Description                        |
|--------------|------------------------------------|
| `Label`      | Integer class label                |
| `Features`   | Feature values (sequence points)   |

---

## 🧬 Model Architecture

The model includes:

1. **KANEncoder**  
   Uses stacked KAN layers + normalization for sequential encoding.

2. **Loss Functions**  
   - `CenterLoss`: Tightens class distributions.  
   - `SupConLoss`: Contrastive learning with supervision.  
   - `Differentiable K-Shape Loss`: Ensures prototype alignment via shape similarity.

---

## 🚀 How to Run

1. Download datasets (`*_TRAIN.tsv`, `*_TEST.tsv`)
2. Adjust file paths in notebooks if needed.
3. Run training via Jupyter:

```bash
jupyter notebook 1KDiscShapeNet_Trace.ipynb
```

Other example notebooks:
- `2KDiscShapeNet_ECG200.ipynb`
- `3KDiscShapeNet_GunPoint.ipynb`, etc.

---

## 📈 Evaluation

The following metrics are used:

- 🟢 **Adjusted Rand Index (ARI)**
- 🔵 **Normalized Mutual Information (NMI)**
- 🟣 **Silhouette Score**

These indicators help measure clustering performance objectively.

---

## 📄 License

MIT License. See the [LICENSE](./LICENSE) file for details.

---

## 🙏 Acknowledgements

Special thanks to the authors of **KAN: Kolmogorov–Arnold Networks (ICLR 2025)**  
for their open-source project:  
🔗 [https://github.com/KindXiaoming/pykan](https://github.com/KindXiaoming/pykan)  
Their code laid the foundation for our model development.

---

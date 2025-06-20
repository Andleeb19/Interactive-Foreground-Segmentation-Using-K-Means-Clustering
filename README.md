# 🖼️ Interactive Foreground Segmentation using K-Means Clustering (Lazy Snapping)

This repository contains an implementation of a basic version of the **Lazy Snapping** image segmentation algorithm using **K-Means clustering** on RGB color pixels. This approach allows interactive figure-ground segmentation with user-defined seed pixels.

---

## 📌 Objective

To segment foreground objects from background in images using user-defined strokes (seed pixels) and K-Means clustering, inspired by the Lazy Snapping technique.

---

## 🧠 Methodology

### Step-by-step Overview:

1. **K-Means Clustering**:
   - Color pixels are clustered using the K-Means algorithm.
   - Separate clusters are computed for foreground and background using seed pixels.

2. **Seed Pixel Extraction**:
   - Foreground and background seed pixels are extracted from user strokes.
     - Foreground: Red strokes
     - Background: Blue strokes

3. **Likelihood Calculation**:
   - For every pixel, compute its likelihood of belonging to each class using:
     \[
     p(C_k | I_p) = e^{-\|I_p - C_k\|}
     \]
   - The class likelihood is a weighted sum across all clusters.
   - A pixel is assigned to the class with the higher overall likelihood.

---

## 🛠️ Implementation Details

- **Language**: Python
- **Libraries**: `OpenCV`, `NumPy`, `scikit-learn`
- **Modules**:
  - `KMeansClustering`: Performs pixel-level color clustering
  - `LazySnapping`: Executes the segmentation logic
  - `lzsnap()`: Main function for processing and segmentation

---

## 📊 Results and Evaluation

### ✅ Parameters:
- Cluster count (N): Tested with 32, 64, 128

### 🖼️ Test Images:

1. **Van Gogh**:
   - N=32: Acceptable, but rough segmentation
   - N=64: Balanced result with clear edges
   - N=128: Detailed but some over-segmentation

2. **Lady**:
   - Robust across different stroke variations
   - N=64 is optimal; lower values miss details, higher introduce noise

3. **Mona Lisa**:
   - Visually pleasing for N=64
   - Higher N gives fine-grained segmentation, but at cost of stability

---

## 🧪 Observations

- **Best Performing Value of N**: 64 clusters
- **Lower N**: Under-segmentation
- **Higher N**: Finer detail, but possible artifacts
- Removing squared distance improved results due to better handling of low-value exponential responses.

---

## ✅ Conclusions

- Lazy Snapping with K-Means is effective for semi-automatic segmentation.
- Performance depends on:
  - Cluster count (N)
  - Quality and placement of seed pixels
- N=64 offers a solid trade-off between segmentation quality and computational cost.

---

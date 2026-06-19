<div align="center">

# 🔵 K-Means Clustering — From Scratch

### Discovering hidden structure in unlabeled data, two dimensions at a time (and three)

![Python](https://img.shields.io/badge/Python-3.14-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![AI](https://img.shields.io/badge/Artificial%20Intelligence-Lab%2011-8A2BE2?style=for-the-badge)
![Unsupervised](https://img.shields.io/badge/Learning-Unsupervised-1D9E75?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

**No labels. No teacher. Just distance — and a centroid that keeps moving until it doesn't.**

</div>

---

## 🎯 Why this project

Every previous lab in this series (KNN, Naive Bayes) assumed the answer key already existed — the data came pre-labeled. **K-Means throws that assumption away.** Given nothing but raw points, the algorithm has to *discover* the groups itself, purely from geometric similarity. This notebook builds the entire algorithm from first principles — distance function, assignment step, centroid update, convergence check — then stress-tests it with extra points, more clusters, predictions on unseen data, and a jump into 3D.

---

## 🧠 The core idea

```
function K_MEANS(data, k):
    centroids ← first k points in data

    repeat:
        clusters ← k empty groups
        for point in data:
            nearest ← index of closest centroid (Euclidean distance)
            clusters[nearest].append(point)

        new_centroids ← mean of each cluster

        if new_centroids == centroids:
            break   # convergence reached

        centroids ← new_centroids

    return centroids, clusters
```

Three steps, looped until stable: **assign → average → repeat.** Everything else in this notebook is this loop applied to a different question.

---

## 🧪 Section 1 — Building K-Means From Scratch
<img width="1188" height="734" alt="image" src="https://github.com/user-attachments/assets/68e1c46c-c126-4835-b704-a48d8f484b98" />


A clearly-separated 2D dataset (`(1,1)`-ish cluster vs `(10,10)`-ish cluster) is used to validate the implementation end-to-end:

- `euclidean_distance()` — dimension-agnostic distance via a loop over coordinates
- `get_closest_centroid()` — linear scan to find the nearest centroid for a point
- `update_centroids()` — recomputes each centroid as the mean of its assigned points
- `k_means()` — the full iterative loop, with a convergence check that stops once centroids stop moving

**Result:** converges in 3 iterations to two perfectly separated clusters — `[1,1],[1,2],[2,1]` and `[10,10],[10,11],[11,10]`.

---

## 🧭 Student Activities — Stress-Testing the Algorithm

| Activity | What changed | Outcome |
|---|---|---|
| **Add a midpoint** `[5, 5]` | Ambiguous point between both clusters | Joined **Cluster 1** — slightly closer to the lower-left group after centroid shifts |
| **Increase K to 3** | One extra cluster on a 2-cluster dataset | Converged back to **2 populated clusters + 1 empty one** — confirms K=2 is the natural fit |

These activities reveal something important about K-Means: it will *always* produce exactly K clusters if you ask for them, even when the data doesn't actually contain that many natural groups — which is exactly why methods like the **Elbow Method** (SSE vs. K) matter for choosing K responsibly.

---

## 📐 Task 1 — Calculating SSE (Sum of Squared Errors)
<img width="1188" height="744" alt="image" src="https://github.com/user-attachments/assets/24727cbe-58e6-402d-a346-78e8919e0d52" />


```python
def calculate_sse(clusters, centroids):
    total_error = 0
    for i in range(len(clusters)):
        for point in clusters[i]:
            total_error += euclidean_distance(point, centroids[i]) ** 2
    return total_error
```

SSE measures how tightly each cluster is packed around its centroid — the foundation metric behind the Elbow Method for choosing K.

**Result:** `SSE = 2.667` for the converged 2-cluster solution — a small residual error confirming tight, well-separated clusters.

---

## 🔮 Task 2 — Predicting on New, Unseen Data

```python
def predict(new_point, final_centroids):
    return get_closest_centroid(new_point, final_centroids)
```

Once centroids are trained, classifying a brand-new point is just one distance comparison away — no retraining required.

**Result:** `[8, 8]` is assigned to **Cluster 2** (the upper-right group) — geometrically the correct call.

---

## 🧊 Task 3 — Challenge: Scaling to 3D Data

```python
dataset_3d = [
    [1, 2, 5], [2, 1, 4], [1, 1, 6],
    [10, 8, 9], [9, 10, 8], [11, 9, 10]
]
```

Because `euclidean_distance()` and `update_centroids()` both loop over `range(len(point))` instead of hardcoding `x, y`, the **exact same code runs unmodified on 3-dimensional points** — no special-casing required.

**Result:** Converges in 3 iterations to two clean 3D clusters, centroids `[10.0, 9.0, 9.0]` and `[1.33, 1.33, 5.0]`.

---

## ✨ Highlights

- ✅ K-Means implemented entirely from first principles — no `scikit-learn` dependency
- ✅ Dimension-agnostic distance and centroid logic — proven to generalize from 2D to 3D without modification
- ✅ Convergence detection via direct centroid comparison (no fixed iteration count required)
- ✅ Hands-on exploration of K-Means' core weakness: it always returns exactly K clusters, even when that's the wrong number
- ✅ SSE implemented as the quantitative foundation for the Elbow Method
- ✅ Prediction on unseen points using only the trained centroids — no full retrain needed

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Python 3.14** | Core implementation |
| **math** | Euclidean distance calculations |
| **random** | Reserved for centroid initialization strategies |

No external ML libraries — every line of the clustering logic is hand-written.

---

## 🚀 Getting Started

### Prerequisites
```bash
python --version   # Python 3.8+
```

### Run the Notebook
```bash
git clone https://github.com/mehrali-hub/ai-kmeans-clustering.git
cd ai-kmeans-clustering
jupyter notebook mehrali_24p0500_lab11.ipynb
```

### Quick Usage
```python
centroids, clusters = k_means(dataset, k=2)
sse = calculate_sse(clusters, centroids)
cluster_id = predict([8, 8], centroids)
```

---

## 📁 Project Structure

```
ai-kmeans-clustering/
│
├── mehrali_24p0500_lab11.ipynb   # K-Means implementation, experiments & 3D extension
└── README.md                     # Project documentation
```

---

## 🎓 Key Takeaways

- **Unsupervised learning finds structure without labels** — clustering groups points by similarity alone
- K-Means is an iterative **optimization** algorithm: assign, average, repeat until stable
- **K is a hyperparameter, not a discovery** — the algorithm will force K clusters even on data that only has 2 natural groups
- **SSE quantifies cluster tightness** and underlies principled K-selection via the Elbow Method
- Writing distance and centroid logic with loops over dimensions (instead of hardcoded `x, y`) makes the algorithm trivially generalize to any number of features

---

## 👩‍💻 Author

**Mehr Ali**
BSCS-4B · FAST NUCES Peshawar
🏆 Kaggle Notebook Expert (Top ~2% Global)

[![GitHub](https://img.shields.io/badge/GitHub-mehrali--hub-181717?style=flat-square&logo=github)](https://github.com/mehrali-hub)

---

<div align="center">
<sub>Built as part of the Artificial Intelligence coursework — K-Means is the foundational clustering algorithm behind customer segmentation, anomaly detection, and exploratory data analysis across modern data science.</sub>
</div>

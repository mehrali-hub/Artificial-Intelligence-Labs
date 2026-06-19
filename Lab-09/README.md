<div align="center">

# 🌸 K-Nearest Neighbors — From Scratch to Scikit-Learn

### Classifying paper tissue quality, Iris flowers, and fruit — by vote of the nearest neighbors

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)
![AI](https://img.shields.io/badge/Artificial%20Intelligence-Lab%209-8A2BE2?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

**No training phase. No model weights. Just distance, votes, and neighbors.**

</div>

---

## 🎯 Why this project

KNN is the simplest possible machine learning algorithm — and one of the most instructive. There's nothing to "train": every prediction is made on the fly by measuring distance to every known point and letting the closest ones vote. This notebook builds that idea up in three stages: **a manual toy example**, **a from-scratch implementation on real Iris data**, and finally **a production-grade scikit-learn pipeline** with hyperparameter tuning — showing exactly what the library is doing under the hood.

---

## 🧠 The core idea

```
function CLASSIFY(point, training_data, k):
    distances ← []
    for each (features, label) in training_data:
        d ← EUCLIDEAN_DISTANCE(point, features)
        distances.append((d, label))

    sort distances ascending
    neighbors ← first k entries

    return MAJORITY_VOTE(labels of neighbors)
```

Every section of this notebook is this exact loop — only the dataset, the distance dimensions, and who's doing the sorting (you, or `sklearn`) change.

---

## 🧪 Experiment Section — Manual Walkthrough

A tiny 4-point "paper tissue quality" dataset (`Good` / `Bad`) is used to build intuition before touching a real dataset.

- **Euclidean distance** and a **bubble-sort neighbor ranking** implemented by hand
- **Experiment 1** — does the prediction for `[3, 7]` change between `k=1` and `k=3`? → No, stays `Good`
- **Experiment 2** — does adding more training points change the outcome? → No, majority vote still favors `Good`
- **Experiment 3** — classify four new points at once with `k=3`, observing a clean `Good` / `Bad` split based on proximity

| Point | Prediction (k=3) |
|---|---|
| [5, 6] | Bad |
| [2, 3] | Good |
| [8, 8] | Bad |
| [4, 5] | Good |

---

## 🌸 Task 1 — KNN From Scratch on the Iris Dataset
<img width="1188" height="822" alt="image" src="https://github.com/user-attachments/assets/77e4eb1c-373d-4a2d-9053-8241be9b3727" />


A 12-sample mini Iris dataset (`Setosa`, `Versicolor`, `Virginica`) with **4 features** (sepal length/width, petal length/width) instead of the toy 2D example.

- `euclidean_distance_iris()` extended to handle 4-dimensional feature vectors
- `classify_iris()` sorts all distances and takes a majority vote among the `k` nearest
- Tested on 3 unseen flowers, then a **bonus sweep across k = 1, 3, 5** to check prediction stability

| Flower | k=1 | k=3 | k=5 |
|---|---|---|---|
| [5.0, 3.3, 1.4, 0.2] | Setosa | Setosa | Setosa |
| [6.0, 2.7, 4.5, 1.5] | Versicolor | Versicolor | Versicolor |
| [7.2, 3.2, 6.0, 1.8] | Virginica | Virginica | Virginica |

**All three predictions stayed perfectly stable across every k** — a sign the test points sit deep inside their class cluster, far from any decision boundary.

---

## 🍎 Task 2 — Scikit-Learn KNN on Real-World Fruit Data
<img width="1188" height="698" alt="image" src="https://github.com/user-attachments/assets/773e11c0-ae21-4db7-9eee-2f4ae86b2e99" />


Moving from hand-rolled code to a production pipeline using `KNeighborsClassifier` on `fruit_data_with_colors.csv`.

- **Data cleaning**: drops non-numeric columns, fills missing values with the column mean
- **Train/test split**: first 50 rows for training, remainder held out for testing
- **Hyperparameter sweep**: trains and evaluates the model for every `k` from 1 to 10
- **Visualization**: plots *K vs. Accuracy* with `matplotlib` to visually identify the best `k`

```python
for k in range(1, 11):
    knn = KNeighborsClassifier(n_neighbors=k)
    knn.fit(X_train, y_train)
    y_pred = knn.predict(X_test)
    scores.append(accuracy_score(y_test, y_pred))
```

This is the same `distance → sort → vote` logic from the scratch implementation — just compiled, vectorized, and production-ready.

---

## ✨ Highlights

- ✅ Same algorithmic core implemented twice — by hand, then via `scikit-learn` — for a direct side-by-side comparison
- ✅ Progression from 2D toy data → 4D real Iris data → real-world noisy CSV data
- ✅ Manual Euclidean distance and majority-vote logic written from first principles
- ✅ Hyperparameter (`k`) sweep with accuracy tracking and visualization
- ✅ Reflection section connecting empirical behavior to KNN theory (odd `k`, bias/variance trade-off, lazy learning)

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Python** | Core implementation |
| **math** | Manual Euclidean distance calculations |
| **pandas** | Loading and cleaning the fruit dataset |
| **scikit-learn** | `KNeighborsClassifier`, `accuracy_score` |
| **matplotlib** | K vs. Accuracy visualization |

---

## 🚀 Getting Started

### Prerequisites
```bash
pip install pandas matplotlib scikit-learn
```

### Run the Notebook
```bash
git clone https://github.com/mehrali-hub/ai-knn-classifier.git
cd ai-knn-classifier
jupyter notebook mehrali_24p0500_lab9.ipynb
```

### Quick Usage
```python
# From-scratch classification
prediction = classify(training_data, [3, 7], k=3)

# Iris flower classification
species = classify_iris(iris_training_data, [5.0, 3.3, 1.4, 0.2], k=3)

# Scikit-learn pipeline
knn = KNeighborsClassifier(n_neighbors=best_k)
knn.fit(X_train, y_train)
```

---

## 📁 Project Structure

```
ai-knn-classifier/
│
├── mehrali_24p0500_lab9.ipynb     # Manual KNN, Iris KNN, and sklearn pipeline
├── fruit_data_with_colors.csv     # Real-world dataset for Task 2
└── README.md                      # Project documentation
```

---

## 🎓 Key Takeaways

- KNN is a **lazy learner** — no training step, all the work happens at prediction time
- **Odd values of k** avoid tie votes in binary classification
- Too small a `k` → overfits to noise; too large a `k` → underfits and ignores local structure
- Hand-implementing the algorithm first makes the `scikit-learn` version far more transparent — it's the exact same logic, just optimized

---

## 👩‍💻 Author

**Mehr Ali**
BSCS-4B · FAST NUCES Peshawar
🏆 Kaggle Notebook Expert (Top ~2% Global)

[![GitHub](https://img.shields.io/badge/GitHub-mehrali--hub-181717?style=flat-square&logo=github)](https://github.com/mehrali-hub)

---

<div align="center">
<sub>Built as part of the Artificial Intelligence coursework — KNN is the conceptual foundation for instance-based learning used throughout recommendation systems, anomaly detection, and pattern recognition.</sub>
</div>

<div align="center">

# 🗺️ A* Search Algorithm — Romania Map Problem

### Finding optimal paths using Informed Search & Euclidean Heuristics

![Python](https://img.shields.io/badge/Python-3.11-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![AI](https://img.shields.io/badge/Artificial%20Intelligence-Lab%205-8A2BE2?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

</div>

---

## 📖 Overview

This project implements the **A\* Search Algorithm**, one of the most widely used informed search algorithms in Artificial Intelligence, to solve the classic **Romania Map Problem**. The goal is to find the shortest path between two cities (Arad → Bucharest) using a combination of actual path cost (`g(n)`) and a heuristic estimate of remaining cost (`h(n)`).

> **A\* evaluates nodes using:**  `f(n) = g(n) + h(n)`
> where `g(n)` is the cost from the start node and `h(n)` is the estimated cost to the goal.

---

## 🧠 How It Works

1. **Graph Representation** — Romania's cities and road distances are modeled as a weighted graph (adjacency dictionary).
2. **Heuristic Function** — Straight-line (Euclidean) distance is computed from each city's latitude/longitude, scaled to kilometers (`× 111`), giving an admissible heuristic.
3. **Priority Queue (Min-Heap)** — A `heapq`-based open list expands the node with the lowest `f(n)` value at each step.
4. **Path Reconstruction** — Once the goal is reached, the path is traced back through parent pointers.

---

## ✨ Features

- ✅ Clean, object-oriented `Node` class with custom comparator for heap ordering
- ✅ Geographic heuristic computed dynamically from coordinates (not hardcoded)
- ✅ Efficient priority-queue-based frontier using Python's `heapq`
- ✅ Closed-set tracking to avoid redundant node expansion
- ✅ Full path + total distance returned for any city pair

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Python 3.11** | Core implementation |
| **heapq** | Priority queue for the open list |
| **math** | Euclidean distance heuristic calculation |
| **Jupyter Notebook** | Development & demonstration environment |

---

## 🚀 Getting Started

### Prerequisites
```bash
python --version   # Python 3.8+
```

### Run the Notebook
```bash
git clone https://github.com/mehrali-hub/ai-astar-romania.git
cd ai-astar-romania
jupyter notebook AI_lab_5.ipynb
```

### Example Usage
```python
path, distance = astar("Arad", "Bucharest")
print("Shortest path:", path)
print("Distance:", round(distance))
```

**Output:**
```
Shortest path from Arad to Bucharest: ['Arad', 'Sibiu', 'Fagaras', 'Bucharest']
Distance: 450
```

---

## 📊 Result

```
Arad → Sibiu → Fagaras → Bucharest
Total Distance = 450 km
```

The algorithm correctly identifies the optimal route by balancing actual road distances against the straight-line heuristic — demonstrating A*'s efficiency over uninformed search strategies like BFS or Dijkstra's algorithm.

---

## 📁 Project Structure

```
ai-astar-romania/
│
├── AI_lab_5.ipynb       # Main notebook — implementation & results
└── README.md            # Project documentation
```

---

## 🎯 Key Learning Outcomes

- Implementing informed search strategies in AI
- Designing admissible heuristics from real-world geographic data
- Using `heapq` for efficient priority-queue-based graph traversal
- Understanding trade-offs between completeness, optimality, and efficiency in search algorithms

---

## 👩‍💻 Author

**Mehr Ali**
BSCS-4B · FAST NUCES Peshawar
Kaggle Notebook Expert (Top ~2% Global) 

[![GitHub](https://img.shields.io/badge/GitHub-mehrali--hub-181717?style=flat-square&logo=github)](https://github.com/mehrali-hub)

---

<div align="center">
<sub>Built as part of the Artificial Intelligence coursework — exploring classical search algorithms that form the foundation of modern AI planning systems.</sub>
</div>

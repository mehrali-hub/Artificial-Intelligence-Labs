
# 🧠 Romania Map Pathfinding using BFS & DFS

![Python](https://img.shields.io/badge/Python-3.10-blue)
![AI Lab](https://img.shields.io/badge/Artificial%20Intelligence-Lab-green)
![Graph Search](https://img.shields.io/badge/Search-BFS%20%26%20DFS-orange)

---

## 📌 Project Overview

This project implements two fundamental Artificial Intelligence search algorithms:

- Breadth First Search (BFS)
- Depth First Search (DFS)

The algorithms are applied to the famous Romania Road Map problem, where cities are represented as graph nodes and roads are represented as graph edges.

The objective is to find a path between a start city and a goal city.

---

## 🗺️ Romania Road Map

The Romania map is modeled as an undirected graph using NetworkX.

### Graph Representation

![Romania Map](https://raw.githubusercontent.com/USERNAME/REPO/main/images/romania-map.png)

---

## 🎯 Problem Statement

Given:

- A graph representing Romania
- A start city
- A goal city

Find a valid path using:

### Breadth First Search (BFS)

BFS explores:

```text
Level by Level
```

It guarantees the shortest path in terms of number of edges.

---

### Depth First Search (DFS)

DFS explores:

```text
Deep First
```

It follows one path completely before backtracking.

---

## ⚙️ Technologies Used

- Python
- NetworkX
- Matplotlib
- Jupyter Notebook

---

## 📂 Project Structure

```text
AI-Lab-Romania-Pathfinding-BFS-DFS
│
├── README.md
├── Romania_Search.ipynb
│
├── images
│   ├── romania-map.png
│   ├── bfs-path.png
│   ├── bfs-output.png
│   ├── dfs-output.png
│   └── bfs-vs-dfs.png
│
└── requirements.txt
```

---

## 🚀 BFS Algorithm

### Working

1. Create Queue
2. Add Start Node
3. Visit Neighboring Cities
4. Continue Level by Level
5. Stop when Goal is Found

### Implementation

```python
queue.pop(0)
```

---

## 🚀 DFS Algorithm

### Working

1. Create Stack
2. Add Start Node
3. Explore Deeply
4. Backtrack if Necessary
5. Stop when Goal is Found

### Implementation

```python
stack.pop()
```

---

## 🧪 Test Cases

### Test Case 1

```text
Start: Arad
Goal : Bucharest
```

### BFS Result

![BFS Output](images/bfs-output.png)

---

### DFS Result

![DFS Output](images/dfs-output.png)

---

### Test Case 2

```text
Start: Oradea
Goal : Eforie
```

Algorithms successfully find a valid route.

---

### Test Case 3

```text
Start: Arad
Goal : Nowhere
```

Result:

```text
None
```

No path exists.

---

## 📍 BFS Path Visualization

The shortest path discovered by BFS is highlighted on the graph.

![BFS Path](images/bfs-path.png)

---

## 📊 BFS vs DFS Comparison

![Comparison](images/bfs-vs-dfs.png)

| Feature | BFS | DFS |
|----------|----------|----------|
| Data Structure | Queue | Stack |
| Exploration | Level-by-Level | Deep First |
| Shortest Path | ✅ Yes | ❌ Not Always |
| Memory Usage | Higher | Lower |
| Completeness | Complete | Complete |
| Optimality | Optimal | Not Optimal |

---

## 📚 Learning Outcomes

Through this lab I learned:

- Graph Representation
- State Space Search
- Breadth First Search
- Depth First Search
- Path Finding
- AI Search Techniques
- Graph Visualization using NetworkX
- Data Structures in Search Algorithms

---

## 🔮 Future Improvements

- Uniform Cost Search (UCS)
- Greedy Best First Search
- A* Search Algorithm
- Interactive GUI
- Real Road Distances

---

## 👨‍💻 Author

**Mehr Ali**

BS Computer Science – 4th Semester

FAST NUCES Peshawar

Aspiring Data Scientist | Machine Learning Engineer | AI Engineer

---

⭐ If you found this project useful, consider giving it a star.

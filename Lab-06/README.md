<div align="center">

# ♛ 8-Queens Problem — Hill Climbing & Simulated Annealing

### Comparing Local Search Strategies for Constraint Satisfaction

![Python](https://img.shields.io/badge/Python-3.10-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C?style=for-the-badge)
![AI](https://img.shields.io/badge/Artificial%20Intelligence-Lab%206-8A2BE2?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

</div>

---

## 📖 Overview

This project tackles the classic **8-Queens Problem** — placing 8 queens on an 8×8 chessboard so that no two queens share a row, column, or diagonal — using two local search algorithms from Artificial Intelligence:

- 🧗 **Hill Climbing** — greedily moves to the best neighboring state, but can get stuck at local minima
- 🔥 **Simulated Annealing** — probabilistically accepts worse moves early on to escape local minima, becoming stricter as "temperature" cools

Both solutions are visualized directly on a rendered chessboard.

---

## 🧠 How It Works

**Heuristic:** `h(board)` = number of pairs of queens attacking each other (same row or same diagonal). The goal is `h = 0`.

### Hill Climbing
- Generates a random initial board
- Evaluates all `8 × 7 = 56` possible single-queen moves at each step
- Always moves to the **best** neighbor found
- Restarts from a new random board if it hits a local minimum (`h > 0`, no better neighbor)

### Simulated Annealing
- Starts at a high temperature `T = 100.0`, cooling by a factor of `0.995` each step
- Picks a **random** neighbor each iteration
- Always accepts improving moves
- Accepts worsening moves with probability `e^(-Δh / T)` — exploring more freely early, converging more strictly as `T → 0`
- Tracks the full `h` value history to plot convergence over time

---

## ✨ Features

- ✅ Clean objective function counting attacking queen pairs
- ✅ Full neighbor-generation logic for Hill Climbing's steepest-ascent search
- ✅ Temperature-based probabilistic acceptance for Simulated Annealing
- ✅ Visual chessboard rendering with `matplotlib` (♛ pieces on alternating squares)
- ✅ Convergence plot showing `h` value decreasing over annealing steps
- ✅ Side-by-side comparison table of both algorithms' behavior

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Python 3.10** | Core implementation |
| **random** | Random board generation & stochastic move selection |
| **math** | Exponential acceptance probability (`e^(-Δh/T)`) |
| **matplotlib** | Chessboard rendering & convergence visualization |

---

## 🚀 Getting Started

### Prerequisites
```bash
pip install matplotlib
```

### Run the Notebook
```bash
git clone https://github.com/mehrali-hub/ai-8queens-search.git
cd ai-8queens-search
jupyter notebook AI_lab_6.ipynb
```

### Example Usage
```python
hc_solution = hill_climbing()
print("h value:", h(hc_solution))   # 0 = solved

sa_solution, h_history = simulated_annealing()
print("h value:", h(sa_solution))   # 0 = solved
```

---

## 📊 Algorithm Comparison

| | Hill Climbing | Simulated Annealing |
|---|---|---|
| Accepts worse moves? | Never | Sometimes |
| Gets stuck at local minimum? | Yes | Less likely |
| Uses temperature? | No | Yes (cools over time) |
| Move selection | Best of all neighbors | Random neighbor |
| Reliability | Lower | Higher |

**Hill Climbing** evaluates all 56 neighbors and greedily picks the best — fast, but prone to getting trapped and needing restarts.

**Simulated Annealing** explores randomly and tolerates worse states early on (controlled by temperature), making it far more likely to escape local minima and reach a true `h = 0` solution.

---

## 📁 Project Structure

```
ai-8queens-search/
│
├── AI_lab_6.ipynb       # Main notebook — implementation, visualization & comparison
└── README.md            # Project documentation
```

---

## 🎯 Key Learning Outcomes

- Implementing local search algorithms (Hill Climbing & Simulated Annealing)
- Designing heuristic functions for constraint satisfaction problems
- Understanding the exploration–exploitation trade-off via temperature scheduling
- Visualizing search convergence and solution states with `matplotlib`

---

## 👩‍💻 Author

**Mehr Ali**
BSCS-4B · FAST NUCES Peshawar
Kaggle Notebook Expert (Top ~2% Global)

[![GitHub](https://img.shields.io/badge/GitHub-mehrali--hub-181717?style=flat-square&logo=github)](https://github.com/mehrali-hub)

---

<div align="center">
<sub>Built as part of the Artificial Intelligence coursework — exploring local search algorithms that underpin optimization and constraint satisfaction in modern AI systems.</sub>
</div>

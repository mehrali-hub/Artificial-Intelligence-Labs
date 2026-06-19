<div align="center">

# 🧩 Constraint Satisfaction Problems — Backtracking Search

### A unified solver for Map Coloring · N-Queens · Sudoku

![Python](https://img.shields.io/badge/Python-3.14-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![AI](https://img.shields.io/badge/Artificial%20Intelligence-CSP-8A2BE2?style=for-the-badge)
![Algorithm](https://img.shields.io/badge/Algorithm-Backtracking-1D9E75?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

**One search strategy. Three classic AI problems. Zero brute force.**

</div>

---

## 🎯 Why this project

Most CSP tutorials solve *one* puzzle and stop. This notebook proves the same backtracking engine — **assign → check consistency → recurse → undo on failure** — generalizes cleanly across three structurally different problems: a graph-coloring problem, a permutation problem, and a grid-filling problem. It's a small demonstration of a big AI idea: model the problem correctly (variables, domains, constraints), and one search algorithm solves all of them.

---

## 🧠 The core idea

```
function BACKTRACK(assignment):
    if assignment is complete:
        return assignment

    var ← SELECT-UNASSIGNED-VARIABLE()
    for value in DOMAIN(var):
        if CONSISTENT(var, value, assignment):
            assignment[var] ← value
            result ← BACKTRACK(assignment)
            if result ≠ failure:
                return result
            undo assignment[var]

    return failure
```

Every problem in this repo is just this loop wearing a different costume — a different `variables`, `domains`, and `is_consistent()`.

---

## 🗺️ Problem 1 — Map Coloring
<img width="1188" height="734" alt="image" src="https://github.com/user-attachments/assets/889d0840-2cd3-43ae-94c3-7b8b7bf20989" />


Assign a color to each region so that **no two adjacent regions share a color**.

- `variables` = regions, `domains` = available colors, `neighbors` = adjacency constraints
- `is_consistent()` rejects any coloring that conflicts with an already-colored neighbor
- A **verbose mode** prints every assign/backtrack step for full transparency
- Generalized into `solve_map_coloring(regions, color_domains, constraint_pairs)` — a reusable solver tested on a 5-region map under 3, 4, and 5-color budgets, demonstrating the graph's **chromatic number** in action

| Map | Colors available | Solvable? |
|---|---|---|
| 4-region | 3 | ✅ `{'A': 'Red', 'B': 'Green', 'C': 'Blue', 'D': 'Red'}` |
| 5-region (extended) | 3 | ✅ |
| 5-region, fully connected | 4 | ❌ |
| 5-region, fully connected | 5 | ✅ |

---

## ♛ Problem 2 — N-Queens
<img width="1188" height="1188" alt="image" src="https://github.com/user-attachments/assets/5b05ffce-4eaa-4d9e-9122-4e9db0e4c89b" />


Place N queens on an N×N board so **no two attack each other** (row, column, or diagonal).

- `variables` = columns, `domains` = rows, `is_safe()` checks row + diagonal conflicts
- Extended beyond "find one solution" into:
  - **`count_all_n_queens_solutions()`** — exhaustive count, not just first-found
  - **Performance benchmarking** across N = 4, 8, 10, 12 using `time.perf_counter()`

| N | Solution found? | Time |
|---|---|---|
| 4 | ✅ | 0.000066s |
| 8 | ✅ | 0.001445s |
| 10 | ✅ | 0.001315s |
| 12 | ✅ | 0.004542s |

**4-Queens has exactly 2 valid solutions** — confirmed by exhaustive count.

---

## 🔢 Problem 3 — Sudoku Solver
<img width="1188" height="1188" alt="image" src="https://github.com/user-attachments/assets/5bd547f0-d114-4e55-8ef2-c5ab2059a60d" />


Fill a 9×9 grid so every **row, column, and 3×3 box** contains digits 1–9 exactly once.

- `find_empty()` scans for the next open cell; `is_valid()` checks row/column/box constraints
- Recursive `solve()` backtracks on any dead end
- An independent `verify_board()` re-validates the finished grid from scratch — the solver is checked, not just trusted
- Stress-tested on both an **easy** and a genuinely **hard** puzzle (deep backtracking required) — both solved and verified ✅

---

## ✨ Highlights

- ✅ **One algorithmic pattern, three domains** — same `assign → check → recurse → undo` skeleton throughout
- ✅ Generalized, reusable map-coloring solver (any regions, colors, constraints)
- ✅ Solution-*counting* variant for N-Queens, not just first-found
- ✅ Empirical runtime benchmarking as problem size scales
- ✅ Independent verification step for Sudoku — trust, but check
- ✅ Verbose tracing mode showing every assignment and backtrack
- ✅ Reflection section linking implementation choices to CSP theory

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Python 3.14** | Core implementation |
| **Recursion / Backtracking** | Shared search strategy across all three problems |
| **time** | Runtime benchmarking for N-Queens scaling |

No external dependencies — pure Python, fully self-contained.

---

## 🚀 Getting Started

### Prerequisites
```bash
python --version   # Python 3.8+
```

### Run the Notebook
```bash
git clone https://github.com/mehrali-hub/ai-csp-backtracking.git
cd ai-csp-backtracking
jupyter notebook mehrali_24p0500_lab8.ipynb
```

### Quick Usage
```python
# Map Coloring
solution = backtrack({})
# {'A': 'Red', 'B': 'Green', 'C': 'Blue', 'D': 'Red'}

# N-Queens
solution = solve_n_queens(8)
total = count_all_n_queens_solutions(4)   # 2

# Sudoku
solve(board)
verify_board(board)   # True
```

---

## 📁 Project Structure

```
ai-csp-backtracking/
│
├── mehrali_24p0500_lab8.ipynb   # All 3 CSP implementations + experiments
└── README.md                    # You are here
```

---

## 🎓 Key Takeaways

- Formulating real-world problems as **variables, domains, constraints** unlocks one general-purpose algorithm instead of three bespoke ones
- Backtracking beats brute force by **pruning early** — a dead-end is detected the moment a constraint breaks, not after a full assignment is built
- Constraint *density* directly determines solvability — more neighbors competing for fewer colors pushes the chromatic number up
- Even "simple" recursive search scales impressively when paired with smart constraint checks — 12-Queens solved in under 5 milliseconds

---

## 👩‍💻 Author

**Mehr Ali**
BSCS-4B · FAST NUCES Peshawar
🏆 Kaggle Notebook Expert (Top ~2% Global)

[![GitHub](https://img.shields.io/badge/GitHub-mehrali--hub-181717?style=flat-square&logo=github)](https://github.com/mehrali-hub)

---

<div align="center">
<sub>Built as part of the Artificial Intelligence coursework — the same constraint-satisfaction techniques here power real-world scheduling, resource allocation, and planning systems.</sub>
</div>

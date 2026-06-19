<div align="center">

# 🧬 Genetic Algorithms Lab

### Evolutionary Search for Binary Optimization & String Matching

![Python](https://img.shields.io/badge/Python-3.14-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![AI](https://img.shields.io/badge/Artificial%20Intelligence-Lab%207-8A2BE2?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

</div>

---

## 📖 Overview

This project implements a **Genetic Algorithm (GA)** from scratch — an evolutionary search technique inspired by natural selection. Candidate solutions ("chromosomes") evolve across generations through **selection**, **crossover**, and **mutation**, gradually converging toward an optimal solution.

The lab builds a complete GA toolbox, applies it to a **binary optimization** problem (maximizing the number of 1-bits), then extends it to a **target string matching** challenge — evolving random strings until they match a target phrase like `"HELLO"`.

<img width="1188" height="734" alt="image" src="https://github.com/user-attachments/assets/7fdf8347-3ea5-4d83-8413-810aed4da888" />

---

## 🧠 How It Works

**Core GA cycle:** `Initialize → Evaluate Fitness → Select Parents → Crossover → Mutate → Repeat`

| Component | Function | Role |
|---|---|---|
| Chromosome creation | `create_chromosome()` | Generates a random candidate solution |
| Fitness evaluation | `fitness()` | Scores how good a chromosome is |
| Parent selection | `select_parent()` | Roulette-wheel (fitness-proportional) selection |
| Crossover | `crossover()` | Single-point crossover combining two parents |
| Mutation | `mutate()` | Randomly flips genes based on a mutation rate |

### 1. Binary Optimization (Warm-Up)
- 9-bit chromosomes, fitness = count of 1-bits (goal: all 1s)
- Full GA loop (`run_binary_ga`) runs across generations until the optimal chromosome is found or `MAX_GENS` is reached

### 2. Parameter Experiments
Systematic exploration of how GA behavior changes with:
- **Mutation rate** (0.01 → 0.5)
- **Population size** (4 → 50)
- **Crossover rate** (0.0 → 1.0)

Each experiment runs 3 trials per parameter setting and reports average generations-to-convergence.

### 3. Target String Matching (Challenge)
- Chromosomes are character strings instead of bits
- Fitness = number of characters matching the target string position-by-position
- Successfully evolves random strings into `"HELLO"`, `"AI LAB"`, and `"GENETIC"` within a handful of generations

---

## ✨ Features

- ✅ Modular, reusable GA components (selection, crossover, mutation) shared across both problems
- ✅ Roulette-wheel selection implemented from first principles
- ✅ Generalized binary GA runner with configurable population, mutation, and crossover rates
- ✅ Controlled experiments isolating the effect of each GA hyperparameter
- ✅ Extension from binary chromosomes to character-string chromosomes
- ✅ Reflection section connecting empirical results to GA theory

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Python 3.14** | Core implementation |
| **random** | Stochastic chromosome generation, selection, crossover, mutation |
| **string** | Character set for the target string matching challenge |

---

## 🚀 Getting Started

### Prerequisites
```bash
python --version   # Python 3.8+
```

### Run the Notebook
```bash
git clone https://github.com/mehrali-hub/ai-genetic-algorithms.git
cd ai-genetic-algorithms
jupyter notebook mehrali_24p0500_lab7.ipynb
```

### Example Usage
```python
# Binary optimization
result = run_binary_ga(
    pop_size=20, chrom_length=9, max_gens=50,
    mutation_rate=0.05, crossover_rate=0.8, verbose=True
)

# Target string matching
result = run_string_ga(
    target="HELLO", pop_size=100, max_gens=500,
    mutation_rate=0.05, crossover_rate=0.8, verbose=True
)
print(result["best"], result["reached"])
```

---

## 📊 Results

| Experiment | Outcome |
|---|---|
| Binary GA (9-bit, 3 runs) | Optimal chromosome `[1,1,1,1,1,1,1,1,1]` reached consistently |
| Mutation rate sweep | Moderate rates converge fastest; too low = slow, too high = unstable |
| Population size sweep | Larger populations aid diversity but cost more time per generation |
| Crossover rate sweep | Crossover accelerates convergence; mutation alone is slower |
| String matching | `"HELLO"` matched by Gen 5; `"AI LAB"` by Gen 13; `"GENETIC"` by Gen 10 |

---

## 📁 Project Structure

```
ai-genetic-algorithms/
│
├── mehrali_24p0500_lab7.ipynb   # Main notebook — GA toolbox, experiments & string matching
└── README.md                    # Project documentation
```

---

## 🎯 Key Learning Outcomes

- Implementing the core GA cycle: selection, crossover, mutation
- Understanding fitness-proportional (roulette-wheel) selection
- Empirically isolating the effect of GA hyperparameters through controlled experiments
- Generalizing a GA framework across different chromosome representations (bits vs. characters)
- Recognizing why GAs are stochastic heuristics with no optimality guarantee

---

## 👩‍💻 Author

**Mehr Ali**
BSCS-4B · FAST NUCES Peshawar
Kaggle Notebook Expert (Top ~2% Global)

[![GitHub](https://img.shields.io/badge/GitHub-mehrali--hub-181717?style=flat-square&logo=github)](https://github.com/mehrali-hub)

---

<div align="center">
<sub>Built as part of the Artificial Intelligence coursework — exploring evolutionary search techniques that power optimization, scheduling, and design problems across modern AI.</sub>
</div>

# 🧠 AI Lab 4 – Greedy Best-First Search on Romania Map

![AI](https://img.shields.io/badge/Artificial%20Intelligence-Greedy%20Search-blue)
![Python](https://img.shields.io/badge/Python-3.x-yellow)
![Algorithm](https://img.shields.io/badge/Search%20Algorithm-Best%20First-green)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

## 📌 Project Overview

This project demonstrates the implementation of the **Greedy Best-First Search (GBFS)** algorithm using the famous **Romania Map Problem** from Artificial Intelligence.

The algorithm searches for a path from a given starting city to **Bucharest** by always selecting the city that appears closest to the goal according to a heuristic function.

The project helps understand:

- State Space Search
- Heuristic-Based Search
- Artificial Intelligence Problem Solving
- Path Finding Algorithms
- Romania Map Search Problem

---

## 🎯 Objective

The objective of this lab is to:

✔ Implement Greedy Best-First Search

✔ Use heuristic values to guide the search

✔ Find a route from **Arad** to **Bucharest**

✔ Calculate the total path distance

✔ Understand informed search strategies in AI

---

## 🗺️ Romania Map Problem

The Romania Map is one of the most widely used examples in AI for demonstrating search algorithms.

The cities are connected through roads with different distances, and the goal is to find a route to **Bucharest**.

---

## ⚙️ Algorithm Used

### Greedy Best-First Search (GBFS)

Greedy Best-First Search selects the node with the **lowest heuristic value**.

### Evaluation Function

```text
f(n) = h(n)

# Computational Probability (Stat 110)

A collection of vectorized Python and NumPy simulations exploring foundational concepts, theorems, and classic paradoxes from Harvard's Stat 110 (*Introduction to Probability*). 

The goal of this repository is to bridge theoretical, proof-based mathematics with high-performance scientific computing by eliminating slow Python loops in favor of vectorized, matrix-based implementations.

## Core Philosophy: Vectorization over Loops

In pure mathematics, problems are solved by manipulating structures and spaces simultaneously. Standard programming often relies on sequential `for` or `while` loops, which are computationally slow and mask the underlying linear algebra. 

Every simulation in this repository leverages **NumPy** to run hundreds of thousands of independent trials simultaneously using matrix manipulations, broadcasting, and vectorized operations.

---

## Completed Simulations

### 1. The Birthday Problem (Chapter 1)
* **The Math:** Exploring the combinatorics behind the probability that at least two people share a birthday in a room of $N$ people.
* **The Optimization Journey:** * *First Approach:* Nested loops checking individual elements ($\sim$36 seconds for $10^6$ trials).
  * *Second Approach:* Python `set()` length comparisons ($\sim$5.8 seconds).
  * *Third Approach (Vectorized):* Generating a multidimensional matrix of size $(\text{trials} \times N)$, sorting along rows, and computing differences between adjacent elements ($\mathbf{< 0.8\text{ seconds}}$).

### 2. The Monty Hall Problem (Chapter 2)
* **The Math:** Simulating the classic conditional probability paradox to demonstrate why switching doors yields a $2/3$ win rate compared to the $1/3$ win rate of staying.
* **The Implementation:** Evaluated both the "Stay" and "Switch" strategies across $10^6$ trials simultaneously using boolean masking and random matrix indexing, completely removing the need for iterative state tracking.

---

## Performance Benchmarks

| Simulation | Method | Trials | Execution Time |
| :--- | :--- | :--- | :--- |
| **Birthday Problem ($N=23$)** | Iterative (Nested Loops) | $1,000,000$ | ~35.96 seconds |
| **Birthday Problem ($N=23$)** | Native Sets | $1,000,000$ | ~5.83 seconds |
| **Birthday Problem ($N=23$)**| **Vectorized Matrix Diff** | $1,000,000$ | **~0.73 seconds** |
| **Monty Hall Paradox** | Vectorized Boolean Masking | $1,000,000$ | *[Insert Your Time] seconds* |

---

## Tech Stack & Toolkit

* **Language:** Python 3
* **Libraries:** NumPy (Matrix operations & random sampling), Matplotlib (Data visualization & convergence tracking)
* **Framework Inspiration:** *Introduction to Probability* by Joseph K. Blitzstein and Jessica Hwang / Harvard Stat 110.

---

## Repository Structure

```text
├── README.md
├── Chapter_1_Combinatorics/
│   └── birthday_problem.ipynb      # Includes iterative vs vectorized comparisons
└── Chapter_2_Conditional/
    └── monty_hall.ipynb            # Matrix conditional logic simulation
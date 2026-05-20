# Bounded Knapsack Problem

Implementation and comparison of four algorithmic approaches to solve the Bounded Knapsack Problem, done as part of an algorithms course.

---

## Problem

Given n items each with a value, a weight, and a maximum available quantity, find the most valuable combination that fits within a weight capacity W.

---

## Algorithms

| Function | Approach | Time Complexity | Space Complexity |
|---|---|---|---|
| `knapfrac` | Greedy (fractional relaxation) | O(n log n) | O(n) |
| `knapdyn` | Dynamic Programming (bottom-up) | O(n · W · B) | O(n · W) |
| `knapdynMem` | Dynamic Programming (memoization) | O(n · W · B) | O(n · W) |
| `knapBnB` | Branch and Bound | O(2^n) worst case | O(n) |

`B` = max quantity per item, `W` = knapsack capacity, `n` = number of items

---

## Notebook Structure

- **Part I** — Fractional knapsack (greedy, used as upper bound in B&B)
- **Part II** — Dynamic programming, bottom-up and memoized, with solution reconstruction
- **Part III** — Branch and Bound with fractional upper bound pruning
- **Part IV** — Complexity analysis and empirical comparison with `timeit`
- **Part V** — Unbounded variant (adapting the bounded functions by setting `bi = floor(W / wi)`)

---

## Run

```bash
git clone https://github.com/your-username/bounded-knapsack.git
cd bounded-knapsack
jupyter notebook projet.ipynb
```

No external libraries needed, only standard Python (`timeit`).

---

## Results

On small to large test instances, `knapfrac` is fastest but only gives the fractional optimum. `knapdynMem` tends to beat `knapdyn` on sparse instances by skipping unused states. `knapBnB` is competitive on small inputs but slows down significantly as n grows without aggressive pruning.

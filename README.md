# CS1463 Course Project  
## Comparative Study of Two Metaheuristic Algorithms over TSP

This project implements and compares two metaheuristic algorithms for solving the Traveling Salesman Problem (TSP):

1. **Genetic Algorithm (GA)** — in-class algorithm  
2. **Variable Neighborhood Search (VNS)** — new algorithm  

The goal is to find the shortest possible tour that visits each city exactly once and returns to the starting city.

---

## 1. Project Description

The Traveling Salesman Problem (TSP) is an optimization problem where a salesman must visit a set of cities exactly once and return to the starting city while minimizing the total travel distance.

Since TSP is difficult to solve exactly for large numbers of cities, this project uses metaheuristic algorithms to find good approximate solutions in a reasonable amount of time.

---

## 2. Algorithms Used

### 2.1 Genetic Algorithm (GA)

The Genetic Algorithm is inspired by natural evolution. It works with a population of candidate tours and improves them over generations.

The GA implementation includes:

- Random initial population
- Tournament selection
- Ordered Crossover (OX)
- Swap mutation
- Elitism to keep the best solution
- Fixed stopping rule based on number of generations

Main parameters:

| Parameter | Value |
|---|---|
| Population size | 100 |
| Crossover rate | 0.9 |
| Mutation rate | 0.1 |
| Tournament size | 3 |
| Small instance stopping rule | 100 generations |
| Large instance stopping rule | 200 generations |

---

### 2.2 Variable Neighborhood Search (VNS)

Variable Neighborhood Search is a single-solution metaheuristic. It improves one solution by applying different neighborhood moves. If the algorithm gets stuck, it switches to another neighborhood structure to escape the local optimum.

The VNS implementation includes:

- Random initial tour
- Local search using limited 2-opt
- Three neighborhood operators:
  - Swap
  - 2-opt reverse segment
  - Insert
- Fixed stopping rule based on number of iterations

Main parameters:

| Parameter | Value |
|---|---|
| Neighborhoods | Swap, 2-opt, Insert |
| Local search attempts | 30 |
| Small instance stopping rule | 100 iterations |
| Large instance stopping rule | 200 iterations |

---

## 3. Dataset

Two TSPLIB instances are used in this project:

| Instance | Number of Cities | Known Optimal Tour Length | Size |
|---|---:|---:|---|
| berlin52 | 52 | 7542 | Small |
| kroA100 | 100 | 21282 | Large |

The datasets are downloaded automatically in the code using `gdown`.

---

## 4. Experimental Setup

Each algorithm is tested on both datasets using the same experimental setup.

For each dataset:

- Each algorithm is run **20 independent times**
- Seeds from `0` to `19` are used
- The same stopping rule is applied to both algorithms
- The following metrics are recorded:
  - Best tour length
  - Worst tour length
  - Average tour length
  - Standard deviation
  - Gap from known optimal solution
  - Average runtime

Stopping rules:

| Instance | GA Stopping Rule | VNS Stopping Rule |
|---|---|---|
| berlin52 | 100 generations | 100 iterations |
| kroA100 | 200 generations | 200 iterations |

---

## 5. Requirements

The project is implemented in Python 3.

Required libraries:

```python
numpy
pandas
matplotlib
gdown

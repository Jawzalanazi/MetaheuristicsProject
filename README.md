### CS1463 Course Project 
### Comparative Study of Two Metaheuristic Algorithms over TSP

This project compares two metaheuristic algorithms for solving the Traveling Salesman Problem (TSP):

- Genetic Algorithm (GA)
- Variable Neighborhood Search (VNS)

The goal is to find a short route that visits each city exactly once and returns to the starting city.

### Problem Description

The Traveling Salesman Problem (TSP) asks for the shortest possible tour among a set of cities.

In this project, each solution is represented as a permutation of city numbers.

Example:

[3, 1, 4, 2, 5]

This means the tour starts from city 3, then visits city 1, city 4, city 2, city 5, and finally returns to city 3.

The main constraint is that each city must be visited exactly once.

### Algorithms

### 1. Genetic Algorithm (GA)

GA is the in-class algorithm used in this project. It is inspired by natural evolution and works with a population of solutions.

Main steps:

- Generate an initial population of random tours
- Evaluate each tour using total tour length
- Select parents using tournament selection
- Apply ordered crossover
- Apply swap mutation
- Keep the best solution using elitism
- Repeat until the stopping rule is reached

GA parameters:

| Parameter | Value |
|---|---|
| Population size | 100 |
| Crossover rate | 0.9 |
| Mutation rate | 0.1 |
| Tournament size | 3 |
| berlin52 stopping rule | 100 generations |
| kroA100 stopping rule | 200 generations |

### 2. Variable Neighborhood Search (VNS)

VNS is the new algorithm used in this project. It works with one solution at a time and changes the neighborhood structure when no improvement is found.

Main steps:

- Start with a random tour
- Improve it using limited 2-opt local search
- Apply different neighborhood moves
- If a better solution is found, restart from the first neighborhood
- If no improvement is found, move to the next neighborhood
- Repeat until the stopping rule is reached

VNS neighborhoods:

- Swap
- 2-opt
- Insert

VNS parameters:

| Parameter | Value |
|---|---|
| Neighborhoods | Swap, 2-opt, Insert |
| Local search attempts | 30 |
| berlin52 stopping rule | 100 iterations |
| kroA100 stopping rule | 200 iterations |

### Datasets

Two TSPLIB instances were used:

| Instance | Number of Cities | Known Optimal Tour Length | Size |
|---|---:|---:|---|
| berlin52 | 52 | 7542 | Small |
| kroA100 | 100 | 21282 | Large |

The dataset files are downloaded in the code using `gdown`.

### Experimental Setup

Both algorithms were tested using the same setup.

- Each algorithm was run 20 times
- Random seeds from 0 to 19 were used
- Both algorithms used the same stopping rule for each instance
- The results were compared using solution quality and runtime

Evaluation metrics:

- Best tour length
- Worst tour length
- Average tour length
- Standard deviation
- Gap from the known optimal solution
- Average runtime

Stopping rules:

| Instance | GA | VNS |
|---|---|---|
| berlin52 | 100 generations | 100 iterations |
| kroA100 | 200 generations | 200 iterations |

### Result Summary

The comparison was based on effectiveness and efficiency.

Effectiveness means how good the tour length is compared to the known optimal solution.

Efficiency means how fast the algorithm runs.

Based on the results:

VNS found shorter tours on both berlin52 and kroA100.
GA was faster on the small instance.
GA has stronger exploration because it uses a population of solutions.
VNS has stronger exploitation because it uses 2-opt local search and different neighborhoods.

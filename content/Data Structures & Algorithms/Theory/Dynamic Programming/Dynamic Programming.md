
### Overview

- An algorithmic technique used to optimize recursive solutions when the same subproblems are called again
- It is mainly an **optimization** over plain recursion. Whenever we see a recursive solution that has repeated calls for the same inputs, we can optimize it using Dynamic Programming
- The idea is to simply store the results of subproblems so that we do not have to re-compute them when needed later. This simple optimization typically reduces time complexities from exponential to polynomial
---
### When to Use Dynamic Programming

#### 1. Optimal Substructure 
---
A problem has **optimal substructure** if an **optimal solution to the entire problem can be constructed from optimal solutions of its subproblems**. This means that solving smaller instances of the problem helps build the final solution efficiently.

- Example: **Shortest Path (Dijkstra, Floyd-Warshall)** → The shortest path from A to C via B is optimal only if the path from A to B and B to C is also optimal.

- Example: **0/1 Knapsack** → The best way to fill a knapsack of weight `W` depends on how we optimally fill smaller knapsacks with weight `< W`.

#### 2. Overlapping Subproblems
---
A problem has **overlapping subproblems** if it **reuses the results of previously computed subproblems multiple times**. Instead of recomputing them, DP allows us to store solutions and retrieve them when needed.

- Example: **Fibonacci Sequence**
    - A naïve recursive approach computes `F(5) = F(4) + F(3)`, but `F(4)` is also computed when finding `F(3)`.
    - Using **memoization**, we store `F(4)` and avoid redundant computations.

- Example: **Edit Distance (Levenshtein Distance)**
    - When computing the minimum number of operations to convert one string into another, many subproblems (smaller substrings) repeat.

---
### Approaches of Dynamic Programming

#### ***1. Top-Down Approach (Memoization):***

In the top-down approach, also known as [****memoization****](https://www.geeksforgeeks.org/what-is-memoization-a-complete-tutorial/), we keep the solution recursive and add a memoization table to avoid repeated calls of same subproblems.

- Before making any recursive call, we first check if the memoization table already has solution for it.
- After the recursive call is over, we store the solution in the memoization table.

#### ***2. Bottom-Up Approach (Tabulation):***

In the bottom-up approach, also known as ****tabulation****, we start with the ****smallest subproblems**** and gradually build up to the final solution.

- We write an iterative solution (avoid recursion overhead) and build the solution in bottom-up manner.
- We use a DP table where we first fill the solution for base cases and then fill the remaining entries of the table using recursive formula.
- We only use recursive formula on table entries and do not make recursive calls.

## Overview
*An algorithmic optimization technique that breaks problems **into smaller subproblems**, solves each subproblem **once**, and **stores** thee result to avoid redundant work.*

- Used when a problem has overlapping subproblems and optimal substructure
	- **Overlapping Subproblems**: 
	- **Optimal Substructure**: 
- More efficient than brute-force approaches like recursion and backtracking 

---
## Common DP Patterns

#### Fibonacci Numbers (Simple Recurrence)

#### DFS + Memoization

#### Backtracking + Memoization

#### Knapsack Problem (Subset Selection)

- **0/1 Knapsack:**
- **Unbounded Knapsack:**

#### State Machine
#### Longest Common Subsequence (LCS) (String Comparison)

---
## DP Approaches

#### Top-Down (Memoization)
In the top-down approach, also known as [****memoization****](https://www.geeksforgeeks.org/what-is-memoization-a-complete-tutorial/), we keep the solution recursive and add a memoization table to avoid repeated calls of same subproblems.

- Before making any recursive call, we first check if the memoization table already has solution for it.
- After the recursive call is over, we store the solution in the memoization table.

#### Bottom-Up (Tabulation)
In the bottom-up approach, also known as ****tabulation****, we start with the ****smallest subproblems**** and gradually build up to the final solution.

- We write an iterative solution (avoid recursion overhead) and build the solution in bottom-up manner.
- We use a DP table where we first fill the solution for base cases and then fill the remaining entries of the table using recursive formula.
- We only use recursive formula on table entries and do not make recursive calls.

---
## When to Use Dynamic Programming

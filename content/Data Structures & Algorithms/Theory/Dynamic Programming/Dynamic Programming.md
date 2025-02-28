
### Overview

- An algorithmic technique used to optimize recursive solutions when the same subproblems are called again
- It is mainly an **optimization** over plain recursion. Whenever we see a recursive solution that has repeated calls for the same inputs, we can optimize it using Dynamic Programming
- The idea is to simply store the results of subproblems so that we do not have to re-compute them when needed later. This simple optimization typically reduces time complexities from exponential to polynomial
---
### When to Use Dynamic Programming

#### 1. Optimal Substructure 

#### 2. Overlapping Subproblems


---
### Approaches of Dynamic Programming

#### ****1. Top-Down Approach (Memoization):****

In the top-down approach, also known as [****memoization****](https://www.geeksforgeeks.org/what-is-memoization-a-complete-tutorial/), we keep the solution recursive and add a memoization table to avoid repeated calls of same subproblems.

- Before making any recursive call, we first check if the memoization table already has solution for it.
- After the recursive call is over, we store the solution in the memoization table.

#### ****2. Bottom-Up Approach (Tabulation):****

In the bottom-up approach, also known as ****tabulation****, we start with the ****smallest subproblems**** and gradually build up to the final solution.

- We write an iterative solution (avoid recursion overhead) and build the solution in bottom-up manner.
- We use a DP table where we first fill the solution for base cases and then fill the remaining entries of the table using recursive formula.
- We only use recursive formula on table entries and do not make recursive calls.

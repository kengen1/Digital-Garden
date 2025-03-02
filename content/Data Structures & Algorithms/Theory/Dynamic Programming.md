## Overview
*An algorithmic optimization technique that breaks problems **into smaller subproblems**, solves each subproblem **once**, and **stores** thee result to avoid redundant work.*

- Used when a problem has overlapping subproblems and optimal substructure
	- **Overlapping Subproblems**: the same subproblems are solved multiple times
	- **Optimal Substructure**: the optimal solution to a problem is built from optimal solutions to its subproblems
- More efficient than brute-force approaches like recursion and backtracking 

---
## Common DP Patterns

- ***Fibonacci Numbers*** (Simple Recurrence) : 
	- Where each state depends on previous states

- ***Knapsack Problem*** (Subset Selection) : 
	- Maximize total value while staying within constraint
	- **0/1 Knapsack :** Each item can either be taken once or not at all
	- **Unbounded Knapsack :** Items can be taken multiple times, allowing repetition

- ***Longest Common Subsequence*** (LCS) :  
	- Find the longest subsequence common to two strings

- ***State Machine :*** 
	- Used when problems involve sequential decisions with multiple states

- ***DFS + Memoization :*** 
	- Naturally recursive problem but involves overlapping subproblems 
	- Instead of recomputing results, store them in a cache (memoization table)

- ***Backtracking + Memoization :*** 
	- A problem with exponential search space but contains repeated computations


---
## Dynamic Programming Approaches

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


---
## Steps to Solve a Dynamic Programming Problem

**1️⃣ Identify the Problem Type**
- Can it be broken into subproblems?
- Do subproblems overlap?
- Does it have optimal substructure?

**2️⃣ Choose Top-Down vs. Bottom-Up**
- **Top-Down (Recursion + Memoization)** → If naturally **recursive**.
- **Bottom-Up (Tabulation)** → If we can **build solutions iteratively**.

**3️⃣ Define DP State**
- What does `dp[i]` or `dp[i][j]` represent?
- Example: `dp[i]` for Fibonacci means "Fibonacci number at index `i`".
- Example: `dp[i][w]` for Knapsack means "max value using first `i` items with weight limit `w`".

 **4️⃣ Implement Transition Formula**
- Convert **recurrence relation** into **code**.
- Example (Knapsack transition):
	```
	dp[i][w] = max(dp[i-1][w], dp[i-1][w-weight[i]] + value[i])
	```

**5️⃣ Optimize Space (if needed)**
- Many DP problems only use the last 1-2 rows of the DP table.
- Example: Fibonacci can be optimized from O(n) space to O(1):

---

## Common Recurrence Relation Patterns

| **Problem Type**                                 | **Examples**                     | **Key Recurrence Pattern**                                      |
| ------------------------------------------------ | -------------------------------- | --------------------------------------------------------------- |
| **Linear DP (Sequence-based)**                   | Fibonacci, Climbing Stairs       | `dp[i] = dp[i-1] + dp[i-2]`                                     |
| **Subset Selection (Knapsack-style)**            | 0/1 Knapsack, Unbounded Knapsack | `dp[i][w] = max(dp[i-1][w], dp[i-1][w - weight[i]] + value[i])` |
| **String Matching (LCS-style)**                  | LCS, Edit Distance               | `dp[i][j] = max(dp[i-1][j], dp[i][j-1])`                        |
| **State Machine DP (Multiple Choices Per Step)** | Stock Trading, Job Scheduling    | `dp[i][state] = max(previous_state_transitions)`                |


### Overview:
a general algorithmic technique that considers searching *every possible combination in order to solve a computational problem*

---
### Types of Backtracking Problems:

- ***decisions problems*** : searching for a feasible solution
- ***optimization problems***: search for the best solution
- ***enumeration problems***: find the set of all possible feasible solutions to the problem of this type

---
### How Does Backtracking Work?

Backtracking follows a ***Depth-First-Search (DFS)*** approach to explore possible solutions
It consists of the following steps:

1. **Choose**: Select the next decision to make
2. **Explore** : Attempt to build a valid solution by making a choice and proceeding recursively
3. **Backtrack**: If a choice leads to an invalid solution, undo it and try the next possible choice 

---
### Determining When to Use Backtracking:

- Not every constraint satisfaction problem should be solved using backtracking.  
- It is a powerful **brute-force approach**, but is often not the most efficient method. 
- Many problems can be solved more optimally using a **Greedy** or **Dynamic Programming** approach.
	- These can achieve logarithmic or polynomial time complexity rather than the exponential time complexity of backtracking 


# When to Use Backtracking? A Decision Tree Approach

#### 1️⃣ Does the problem involve making a series of independent decisions?
   - **Yes →** Consider **Dynamic Programming (DP) or Greedy Algorithms** instead.
   - **No →** Proceed to the next question.

#### 2️⃣ Does the problem require exploring multiple possibilities systematically?
   - **Yes →** Backtracking might be suitable.
   - **No →** Consider **DP or Greedy** for a more optimal approach.

#### 3️⃣ Can we prune invalid states early to avoid redundant work?
   - **Yes →** Backtracking can be **efficient** when combined with pruning.
   - **No →** The problem might be too large for backtracking to be effective.

#### 4️⃣ Does the problem lack a greedy or DP structure?
   - **Yes →** Backtracking is often the best approach.
   - **No →** Use **DP** if optimal substructure exists or **Greedy** if local choices lead to a global optimum.

#### 5️⃣ Does the problem involve constraints or conditional decision-making?
   - **Yes →** Backtracking is required to enforce constraints.
   - **No →** Consider alternative approaches like **Greedy** or **DP**.

---
### Complexity Analysis for Backtracking

Since backtracking algorithm is purely brute force therefore in terms of time complexity, it performs very poorly. Generally backtracking can be seen having below mentioned time complexities:

- Exponential (O(K^N))
- Factorial (O(N!))

These complexities are due to the fact that at each state we have multiple choices due to which the number of paths increases and sub-trees expand rapidly.

--- 
#### Final Decision Summary:
✅ **Use Backtracking** if:
   - The problem requires **exploring all possible choices**.
   - There are **constraints** that must be satisfied at every step.
   - The problem lacks a **clear Greedy** or **DP approach**.
   - We can **prune invalid solutions early** to reduce time complexity.

❌ **Avoid Backtracking** if:
   - Choices are **independent of each other** → Use **DP/Greedy**.
   - The problem has **optimal substructure** → Use **DP**.
   - A **local greedy choice** leads to the global best solution → Use **Greedy**.

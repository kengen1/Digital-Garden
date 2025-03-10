
*A method of traversal for ordering nodes in a **Directed Acyclic Graphs (DAG)** such that for every directed edge `u --> v` , `u` appears before `v` in the ordering*

---
### Depth-First-Search (Recursion + Stack) Method

*utilises **post-order traversal***

#### Algorithm Design
1. Build the graph:
	- Represent the directed graph as an adjacency list

2. Perform DFS to detect cycles and process nodes:
	- Maintain a `visited[]` array
		- `0` --> Unvisited
		- `1` --> Visiting (Part of current DFS path)
		- `2` --> Processed (Node has been completed explored)
	- If a cycle has been detected, return a failure
	- Once DFS on a node completes, add it to the stack

3. Extract order:
	- The stack contains the nodes in reverse topological order
	- Pop elements from the stack to get the correct order


#### Code C++

```cpp

```

---
### Breadth-First-Search (Kahn's Algorithm)

*relies on **in-degree counting***

#### Algorithm Design
1. Build the graph:
	- Represent the directed graph as an adjacency list
	- Compute the **in-degree** (number of incoming edges for each node)

2. Initialize queue
	- push all nodes with in-degree = 0 (no edges) into the queue

3. Process nodes in the queue
	- while the queue is not empty 
		- deque a node and add it to the topological order list
		- reduce the in-degree of all its neighbours
		- if any neighbours in-degree becomes 0, enqueue it 

4. Check for cycles
	- if the final topological order does not contain all nodes, a cycle exists

#### Code C++

```cpp

```


---

### Which one to use?

| Approach | Time Complexity | Space Complexity | Use Case                                       |
| -------- | --------------- | ---------------- | ---------------------------------------------- |
| DFS      | `O(V + E)`      | `O(V + E)`       | Cycle-detection and topological order          |
| BFS      | `O(V + E)`      | `O(V + E)`       | Iterative approach, efficient for large graphs |


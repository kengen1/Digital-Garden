
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

#### Pseudocode
```cpp
vector<int> topologicalSort(int numNodes, vector<vector<int>>& edges) {
    // Step 1: Build Adjacency List
    vector<vector<int>> adjList(numNodes);
    for (auto& edge : edges) {
        int from = edge[0], to = edge[1];
        adjList[from].push_back(to);
    }

    // Step 2: Initialize DFS tracking variables
    vector<int> visited(numNodes, 0);
    stack<int> topoStack;
    vector<int> result;

    // Step 3: Perform DFS on all unvisited nodes
    for (int node = 0; node < numNodes; node++) {
        if (visited[node] == 0) {
            if (dfs(node, adjList, visited, topoStack))
                return {};  // Cycle detected, return empty array
        }
    }

    // Step 4: Extract topological order
    while (!topoStack.empty()) {
        result.push_back(topoStack.top());
        topoStack.pop();
    }

    return result;
}

// DFS function to detect cycles and perform topological sorting
bool dfs(int node, vector<vector<int>>& adjList, vector<int>& visited, stack<int>& topoStack) {
    if (visited[node] == 1) return true;  // Cycle detected
    if (visited[node] == 2) return false; // Already processed

    visited[node] = 1; // Mark as visiting
    for (int neighbor : adjList[node]) {
        if (dfs(neighbor, adjList, visited, topoStack))
            return true;  // Cycle detected
    }

    visited[node] = 2; // Mark as processed
    topoStack.push(node); // Add to stack
    return false;
}
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

#### Pseudocode

```cpp
vector<int> topologicalSortBFS(int numNodes, vector<vector<int>>& edges) {
    // Step 1: Build adjacency list and compute in-degrees
    vector<vector<int>> adjList(numNodes);
    vector<int> inDegree(numNodes, 0);

    for (auto& edge : edges) {
        int from = edge[0], to = edge[1];
        adjList[from].push_back(to);
        inDegree[to]++;
    }

    // Step 2: Initialize queue with nodes having in-degree 0
    queue<int> q;
    for (int node = 0; node < numNodes; node++) {
        if (inDegree[node] == 0)
            q.push(node);
    }

    // Step 3: Process queue
    vector<int> order;
    while (!q.empty()) {
        int node = q.front();
        q.pop();
        order.push_back(node);

        for (int neighbor : adjList[node]) {
            inDegree[neighbor]--;
            if (inDegree[neighbor] == 0)
                q.push(neighbor);
        }
    }

    // Step 4: Check for cycle
    if (order.size() != numNodes)
        return {};  // Cycle detected

    return order;
}

```


---

### Which one to use?

| Approach | Time Complexity | Space Complexity | Use Case                                       |
| -------- | --------------- | ---------------- | ---------------------------------------------- |
| DFS      | `O(V + E)`      | `O(V + E)`       | Cycle-detection and topological order          |
| BFS      | `O(V + E)`      | `O(V + E)`       | Iterative approach, efficient for large graphs |


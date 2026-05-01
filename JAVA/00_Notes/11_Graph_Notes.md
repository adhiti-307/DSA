# 📘 Graphs – Complete Notes

---

# 🔹 1. What is a Graph?

A Graph is a **non-linear data structure** consisting of:

* **Vertices (nodes)**
* **Edges (connections)**

```text id="g1"
Graph = (V, E)
```

---

# 🔹 2. Types of Graphs

---

## 🔸 Based on Direction

```text id="g2"
Undirected → edges have no direction  
Directed (DiGraph) → edges have direction  
```

---

## 🔸 Based on Weight

```text id="g3"
Unweighted → all edges equal  
Weighted → edges have weights  
```

---

## 🔸 Other Types

```text id="g4"
Cyclic → contains cycle  
Acyclic → no cycle  
Connected → all nodes reachable  
Disconnected → not all connected  
```

---

# 🔹 3. Graph Representation

---

## 🔸 3.1 Adjacency Matrix

```text id="g5"
0 1 1
1 0 1
1 1 0
```

👉 Space: **O(V²)**

---

## 🔸 3.2 Adjacency List (Most Used)

```text id="g6"
1 → 2, 3  
2 → 1, 3  
3 → 1, 2  
```

👉 Space: **O(V + E)**

---

## 🔸 Java Representation

```java id="g7"
ArrayList<ArrayList<Integer>> adj = new ArrayList<>();

for(int i = 0; i < n; i++){
    adj.add(new ArrayList<>());
}
```

---

# 🔹 4. Graph Traversal

---

## 🔸 4.1 Breadth First Search (BFS)

Uses **Queue**

```text id="g8"
Level-wise traversal
```

---

### ✅ Code

```java id="g9"
void bfs(int start, ArrayList<ArrayList<Integer>> adj, int n){
    boolean[] visited = new boolean[n];
    Queue<Integer> q = new LinkedList<>();

    q.add(start);
    visited[start] = true;

    while(!q.isEmpty()){
        int node = q.poll();
        System.out.print(node + " ");

        for(int nei : adj.get(node)){
            if(!visited[nei]){
                visited[nei] = true;
                q.add(nei);
            }
        }
    }
}
```

---

## 🔸 4.2 Depth First Search (DFS)

Uses **Recursion / Stack**

```text id="g10"
Go deep before exploring neighbors
```

---

### ✅ Code

```java id="g11"
void dfs(int node, boolean[] visited, ArrayList<ArrayList<Integer>> adj){
    visited[node] = true;
    System.out.print(node + " ");

    for(int nei : adj.get(node)){
        if(!visited[nei]){
            dfs(nei, visited, adj);
        }
    }
}
```

---

# 🔹 5. Cycle Detection

---

## 🔸 5.1 Undirected Graph (DFS)

```java id="g12"
boolean dfs(int node, int parent){
    visited[node] = true;

    for(int nei : adj.get(node)){
        if(!visited[nei]){
            if(dfs(nei, node)) return true;
        } else if(nei != parent){
            return true;
        }
    }
    return false;
}
```

---

## 🔸 5.2 Directed Graph

Use **DFS + recursion stack**

---

# 🔹 6. Topological Sort (DAG)

Used for:

* Task scheduling
* Dependency resolution

---

## 🔸 Kahn’s Algorithm (BFS)

```java id="g13"
Queue<Integer> q = new LinkedList<>();
int[] indegree = new int[n];

// fill indegree

for(int i = 0; i < n; i++){
    if(indegree[i] == 0) q.add(i);
}

while(!q.isEmpty()){
    int node = q.poll();

    for(int nei : adj.get(node)){
        indegree[nei]--;
        if(indegree[nei] == 0){
            q.add(nei);
        }
    }
}
```

---

# 🔹 7. Shortest Path Algorithms

---

## 🔸 7.1 Dijkstra (Weighted Graph)

```text id="g14"
Greedy + Min Heap
```

---

## 🔸 7.2 BFS (Unweighted Graph)

```text id="g15"
Shortest path in unweighted graph
```

---

## 🔸 7.3 Bellman-Ford

```text id="g16"
Handles negative weights
```

---

# 🔹 8. Union-Find (Disjoint Set)

Used for:

* Cycle detection
* Connectivity

```java id="g17"
int find(int x){
    if(parent[x] != x){
        parent[x] = find(parent[x]);
    }
    return parent[x];
}
```

---

# 🔹 9. Time Complexity

| Algorithm        | Complexity |
| ---------------- | ---------- |
| BFS              | O(V + E)   |
| DFS              | O(V + E)   |
| Dijkstra         | O(E log V) |
| Topological Sort | O(V + E)   |

---

# 🔹 10. Common Problems

* BFS Traversal
* DFS Traversal
* Detect Cycle
* Topological Sort
* Shortest Path
* Number of Islands

---

# 🔹 11. Common Mistakes

```text id="g18"
❌ Not marking visited  
❌ Infinite loops  
❌ Wrong graph representation  
❌ Ignoring disconnected components  
```

---

# 🔹 12. Interview Tips

```text id="g19"
✔ Use BFS → shortest path  
✔ Use DFS → traversal / cycle  
✔ Think in terms of nodes & edges  
✔ Practice adjacency list  
```

---

# 🧠 Quick Revision

```text id="g20"
Graph → nodes + edges  
BFS → level order  
DFS → depth first  
Topo Sort → DAG  
Union-Find → connectivity  
```

---

# 🔥 Final Insight

```text id="g21"
Most graph problems = traversal + pattern
```

👉 Master:

* BFS
* DFS
* Topological Sort

---

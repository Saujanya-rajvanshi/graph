# graph

## INDEX 
- [basic](#basic)
- [types](#types)
- [graph representation](#graph-representation)
- [graph traversal](#graph-traversal)



### basic 
---
* non linear data structure
* it consist of nodes and edges
* G = (V,E)

---

###### types 
---

## 🔷 Types of Graphs (Data Structures)

### 🔹 1. Based on Direction

* **Undirected Graph** – edges have no direction
* **Directed Graph (Digraph)** – edges have direction

---

### 🔹 2. Based on Weights

* **Weighted Graph** – edges have weights
* **Unweighted Graph** – edges have no weights

---

### 🔹 3. Based on Connectivity

* **Connected Graph** – path exists between every pair of vertices
* **Disconnected Graph** – at least one vertex is unreachable

---

### 🔹 4. Based on Cycles

* **Cyclic Graph** – contains at least one cycle
* **Acyclic Graph** – no cycles

---

### 🔹 5. Special Graph Types

* **Complete Graph** – edge between every pair of vertices
* **Null Graph** – no edges
* **Regular Graph** – all vertices have same degree
* **Bipartite Graph** – vertices divided into two sets
* **Complete Bipartite Graph** – every vertex of one set connects to all in other
* **Multigraph** – multiple edges allowed
* **Pseudograph** – self-loops allowed

---

### 🔹 6. Tree-Based Graphs

* **Tree** – connected, acyclic graph
* **Forest** – collection of trees

---

### 🔹 7. Directed Special Graphs

* **DAG (Directed Acyclic Graph)** – no cycles (used in scheduling)
---

## graph representation

#### 1. Adjacency matrix representation 
* graph represented in a form of matrix of size v*v
* filled with either 1 or 0

#### 2. Adjacency list representation 
* every vertex of a graph contains list of its adjacent vertices 
* space complexity O(|V|+|E|)

---

### 🔷 Difference Between Adjacency Matrix and Adjacency List

| **Aspect**               | **Adjacency Matrix**                 | **Adjacency List**                         |
| ------------------------ | ------------------------------------ | ------------------------------------------ |
| **Definition**           | Uses a 2D matrix to represent edges  | Uses a list for each vertex to store edges |
| **Space Complexity**     | **O(V²)**                            | **O(V + E)**                               |
| **Best for**             | Dense graphs                         | Sparse graphs                              |
| **Edge Existence Check** | **O(1)**                             | **O(V)**                                   |
| **Add Edge**             | **O(1)**                             | **O(1)**                                   |
| **Remove Edge**          | **O(1)**                             | **O(V)**                                   |
| **Add Vertex**           | Expensive (resize matrix)            | Easy                                       |
| **Remove Vertex**        | Very expensive (remove row & column) | Moderate (remove lists)                    |
| **Memory Usage**         | High                                 | Efficient                                  |
| **Traversal Efficiency** | Less efficient                       | More efficient                             |
| **Implementation**       | Simple                               | Slightly complex                           |
| **Scalability**          | Poor for large graphs                | Good for large graphs                      |
| **Real-World Usage**     | Dense networks                       | Social networks, web graphs                |

---

### ⭐ Interview Summary Line

**Adjacency Matrix is preferred for dense graphs due to O(1) edge lookup, while Adjacency List is preferred for sparse graphs because of lower space usage.**

---

If you want:
✔️ **Time-complexity only short table**
✔️ **C++ code comparison**
✔️ **When to choose which (decision tree)**

Just say 👍





## graph traversal 
* start from one vertex and go along the edges to visit other vertices untill all vertices.
* decide the order of vertices
* traverse without getting into looping

### TWO GRAPH TRAVERSAL TECHNIQUES
* **DFS**(DEPTH FIRST SEARCH)
* **BFS**(BREADTH FIRST SEARCH)

**DFS**

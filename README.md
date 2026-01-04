# graph

## INDEX 
- [basic](#basic)
- [types](#types)
- [graph representation](#graph-representation)




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



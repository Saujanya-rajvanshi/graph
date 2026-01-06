# graph

## INDEX 
- [basic](#basic) 
- [types](#types) 
- [graph representation](#graph-representation)
- [graph traversal](#graph-traversal)
- [transitive closure](#transitive-closure)
- [minimum cost spaning trees](#minimum-cost-spaning-trees)
- [Dijkstra’s Algorithm – Single Source Shortest Path](#Dijkstras-Algorithm-Single-Source-Shortest-Path)
- [Floyd-Warshall Algorithm – All-Pairs Shortest Path](#Floyd-Warshall-Algorithm-All-Pairs-Shortest-Path)
- [striver questions](#striver-question)


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

Connected Graph 

Connected Graph:
A graph is **connected** if there is a **path between every pair of vertices**.
Disconnected Graph:
If **any vertex cannot be reached** from another, the graph is disconnected.
Connected Component:
Each **maximal connected subgraph** in a disconnected graph.

Example :
If all nodes can reach each other → connected; otherwise → multiple connected components.

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

### Interview Summary Line
Adjacency Matrix is preferred for dense graphs due to O(1) edge lookup, while Adjacency List is preferred for sparse graphs because of lower space usage.


## graph traversal 
* start from one vertex and go along the edges to visit other vertices untill all vertices.
* decide the order of vertices
* traverse without getting into looping

### TWO GRAPH TRAVERSAL TECHNIQUES
* **DFS**(DEPTH FIRST SEARCH) - [DFS](#DFS)
* **BFS**(BREADTH FIRST SEARCH)  - [BFS](#BFS)

## DFS
---

## 🔍 DFS (Depth First Search)

🔹 **Data Structure Used**: **Stack**
🔹 **Maximum Stack Size**: Total number of vertices in the graph

---

## 🪜 Steps to Implement DFS Traversal

**Step 1️⃣**
📦 Define a **stack** of size equal to the total number of vertices in the graph.

**Step 2️⃣**
▶️ Select **any vertex** as the starting point.
👀 Visit that vertex and **push it onto the stack**.

**Step 3️⃣**
🔗 From the vertex at the **top of the stack**, visit **any one non-visited adjacent vertex** and **push it onto the stack**.

**Step 4️⃣**
🔁 Repeat **Step 3** until there is **no new adjacent vertex** to visit from the vertex at the top of the stack.

**Step 5️⃣**
↩️ If no new vertex is found, perform **backtracking** by **popping one vertex** from the stack.

**Step 6️⃣**
🔄 Repeat **Steps 3, 4, and 5** until the **stack becomes empty**.

**Step 7️⃣**
✅ When the stack is empty, DFS traversal is complete and the **final spanning tree** is obtained.

---

✔️ DFS explores **depth first**
✔️ Uses **stack (explicit or recursion)**
✔️ Involves **backtracking**


### DFS Traversal (Worked Example)

### 🔹 Given

* **Graph vertices**: `A B C D E F G`
* **Traversal technique**: **DFS (Depth First Search)**
* **Data Structure used**: **Stack**
* **Auxiliary arrays**:

  * `status[]` → visited / not visited
  * `output[]` → traversal order

---

## 🔹 Initial Setup

1. **Status Array**

```
A B C D E F G
0 0 0 0 0 0 0   (0 = not visited, 1 = visited)
```

2. **Stack size** = number of vertices = **7**

3. **Output** → empty initially

---

## 🔹 Step-by-Step DFS Traversal

### 🟢 Step 1: Start from vertex **A**

* Visit `A`
* Push `A` into stack

```
Stack: A
Output: A
Status: 1 0 0 0 0 0 0
```

---

### 🟢 Step 2: Visit unvisited adjacent of **A**

* Choose `B`
* Push `B`

```
Stack: B A
Output: A B
Status: 1 1 0 0 0 0 0
```

---

### 🟢 Step 3: Visit unvisited adjacent of **B**

* Choose `C`
* Push `C`

```
Stack: C B A
Output: A B C
Status: 1 1 1 0 0 0 0
```

---

### 🟢 Step 4: Visit unvisited adjacent of **C**

* Choose `E`
* Push `E`

```
Stack: E C B A
Output: A B C E
Status: 1 1 1 0 1 0 0
```

---

### 🟢 Step 5: Visit unvisited adjacent of **E**

* Choose `D`
* Push `D`

```
Stack: D E C B A
Output: A B C E D
Status: 1 1 1 1 1 0 0
```

---

### 🔁 Backtracking Begins

* `D` has no unvisited adjacent → **pop**
* From `E`, visit `F`

```
Stack: F E C B A
Output: A B C E D F
Status: 1 1 1 1 1 1 0
```

---

### 🔁 Continue Backtracking

* From `F`, visit `G`

```
Stack: G F E C B A
Output: A B C E D F G
Status: 1 1 1 1 1 1 1
```

---

## ✅ Final DFS Traversal Order

```
A → B → C → E → D → F → G
```

---

### BFS 
---

## 🔍 BFS (Breadth First Search)

🔹 **Data Structure Used**: **Queue**
🔹 **Maximum Queue Size**: Total number of vertices in the graph
🔹 **Traversal Style**: **Level by level**

---

## 🪜 Steps to Implement BFS Traversal

**Step 1️⃣**
📦 Define a **queue** of size equal to the total number of vertices in the graph.

**Step 2️⃣**
▶️ Select **any vertex** as the starting point.
👀 Visit that vertex and **insert it into the queue**.

**Step 3️⃣**
🔗 Visit **all non-visited adjacent vertices** of the **front vertex** and **insert them into the queue**.

**Step 4️⃣**
🚪 If there is **no new adjacent vertex** for the front vertex, **remove (dequeue)** it from the queue.

**Step 5️⃣**
🔁 Repeat **Steps 3 and 4** until the **queue becomes empty**.

**Step 6️⃣**
✅ When the queue becomes empty, BFS traversal is complete and the **final spanning tree** is obtained.

---

## ⭐ Key Points (Very Important)

* ✔️ BFS uses **Queue**
* ✔️ Explores **breadth first (level-wise)**
* ✔️ No backtracking
* ✔️ Time Complexity: **O(V + E)**
* ✔️ Space Complexity: **O(V)**

---

---

## BFS Traversal (WORKED EXAMPLE)

### 🔹 Given

* **Vertices**: `A B C D E F G`
* **Data Structure**: **Queue**
* **Auxiliary Arrays**:

  * `visited[]` → visited / not visited
  * `result[]` → traversal order

---

## 🔹 Initial State

### 🟡 Visited Array

```
A B C D E F G
0 0 0 0 0 0 0
```

### 🟡 Queue

```
[  ]
```

### 🟡 Result

```
[  ]
```

---

## 🪜 BFS Step-by-Step

### 🟢 Step 1: Select **A** as starting vertex

* Visit `A`
* Insert `A` into queue

```
Queue   : A
Visited : 1 0 0 0 0 0 0
Result  : A
```

---

### 🟢 Step 2: Dequeue **A**, insert its unvisited adjacent vertices

* Adjacent of A → `D, E, B`
* Insert into queue

```
Queue   : D E B
Visited : 1 1 0 1 1 0 0
Result  : A
```

---

### 🟢 Step 3: Dequeue **D**

* No new unvisited adjacent vertices

```
Queue   : E B
Visited : 1 1 0 1 1 0 0
Result  : A D
```

---

### 🟢 Step 4: Dequeue **E**

* Adjacent → `C, F`
* Insert unvisited ones

```
Queue   : B C F
Visited : 1 1 1 1 1 1 0
Result  : A D E
```

---

### 🟢 Step 5: Dequeue **B**

* No new unvisited adjacent

```
Queue   : C F
Result  : A D E B
```

---

### 🟢 Step 6: Dequeue **C**

* Adjacent → `G`
* Insert `G`

```
Queue   : F G
Visited : 1 1 1 1 1 1 1
Result  : A D E B C
```

---

### 🟢 Step 7: Dequeue **F**, then **G**

* No new vertices

```
Queue   : empty
Result  : A D E B C F G
```

---

## ✅ Final BFS Traversal Order

```
A → D → E → B → C → F → G
```
---
## 🔹 Difference Between BFS and DFS

| **Aspect**              | **BFS (Breadth First Search)**           | **DFS (Depth First Search)**      |
| ----------------------- | ---------------------------------------- | --------------------------------- |
| **Traversal Type**      | Level-by-level                           | Depth-wise                        |
| **Data Structure Used** | Queue                                    | Stack / Recursion                 |
| **Exploration Style**   | Visits all neighbors first               | Goes deep before backtracking     |
| **Backtracking**        | ❌ No                                     | ✅ Yes                             |
| **Memory Usage**        | Higher                                   | Lower (generally)                 |
| **Shortest Path**       | ✅ Finds shortest path (unweighted graph) | ❌ Not guaranteed                  |
| **Implementation**      | Easier                                   | Slightly complex                  |
| **Use Case**            | Level order traversal, shortest path     | Cycle detection, topological sort |
| **Time Complexity**     | O(V + E)                                 | O(V + E)                          |
| **Space Complexity**    | O(V)                                     | O(V)                              |

---

*BFS uses a queue and explores level by level, while DFS uses a stack and explores depth first.*


## transitive closure

* Shows **reachability** between all vertex pairs
* If **u can reach v**, mark **1**, else **0**
* Final result is a **Boolean matrix**
* Based on **paths**, not just direct edges
* Also called **Reachability Matrix**
* Can be found using **Warshall’s Algorithm**

##### **Adjacency vs Reachability Matrix (One Example)**

**Graph:** 0 → 1 → 2

| From \ To               | 0 | 1 | 2 |
| ----------------------- | - | - | - |
| **Adjacency Matrix**    |   |   |   |
| 0                       | 0 | 1 | 0 |
| 1                       | 0 | 0 | 1 |
| 2                       | 0 | 0 | 0 |
| **Reachability Matrix** |   |   |   |
| 0                       | 1 | 1 | 1 |
| 1                       | 0 | 1 | 1 |
| 2                       | 0 | 0 | 1 |

* **Adjacency** → direct edge only
* **Reachability** → direct + indirect path

## minimum cost spaning trees

* **Spanning Tree**: Connects **all vertices**, **no cycles**, **V − 1 edges**

* **Minimum Spanning Tree (MST)**: Spanning tree with **minimum total edge weight**

* **Graph type**: **Connected + weighted + undirected** graph

* **Cost of MST**: Sum of weights of selected edges (minimum)

* **Algorithms used**: **Prims** and **Kruskals**  

* **Key property**:
  No cycles, still fully connected ✔

  <img width="631" height="158" alt="image" src="https://github.com/user-attachments/assets/9e5e9b23-94ee-4cb0-b264-f7658e146231" />

#### Prims
---

## 🌳 Prim’s Algorithm (Minimum Spanning Tree)

**Definition**

* Prim’s algorithm constructs a **Minimum Spanning Tree (MST)**.
* It grows the tree **one vertex at a time**.
* Uses **greedy approach**.

**Key Points**

* Starts from **any one vertex**.
* At each step, picks the **minimum weight edge** connecting:

  * a vertex **inside the tree**
  * to a vertex **outside the tree**
* Stops when **all vertices are included**.
* Total iterations = **(n − 1)**

---

## 📌 Representation Used

```
vertex ( parent , cost )
```

---

## 🧮 Example 
<img width="184" height="96" alt="image" src="https://github.com/user-attachments/assets/15dbfaee-da5f-4ef7-8c70-158a463e5140" />

### Step 1

```
Tree Vertices:
a ( - , 0 )

Remaining Vertices in Q:
b ( - , ∞ )
c ( - , ∞ )
d ( - , ∞ )
e ( - , ∞ )
```

---

### Step 2

```
Selected Vertex:
b ( a , 4 )

Tree Vertices:
a ( - , 0 )
b ( a , 4 )

Remaining Vertices in Q:
c ( b , 8 )
d ( - , ∞ )
e ( - , ∞ )
```

---

### Step 3

```
Selected Vertex:
c ( b , 8 )

Tree Vertices:
a ( - , 0 )
b ( a , 4 )
c ( b , 8 )

Remaining Vertices in Q:
d ( c , 7 )
e ( - , ∞ )
```

---

### Step 4

```
Selected Vertex:
d ( c , 7 )

Tree Vertices:
a ( - , 0 )
b ( a , 4 )
c ( b , 8 )
d ( c , 7 )

Remaining Vertices in Q:
e ( d , 2 )
```

---

### Step 5

```
Selected Vertex:
e ( d , 2 )

Tree Vertices:
a ( - , 0 )
b ( a , 4 )
c ( b , 8 )
d ( c , 7 )
e ( d , 2 )
```

### Remaining Vertices in Q

```
e ( d , 9 )
h ( i , 7 )
g ( i , 6 )
```

---

### Step – Select Minimum

```
Selected:
g ( i , 6 )
```

### Tree Vertices

```
a ( - , 0 )
b ( a , 4 )
c ( b , 8 )
d ( c , 7 )
i ( c , 2 )
g ( i , 6 )
```

---

### Update Remaining Vertices

```
h ( g , 1 )
e ( d , 9 )
```

---

### Step – Select Minimum

```
Selected:
h ( g , 1 )
```

---

### Update Remaining Vertices

```
e ( h , 2 )
```

---

### Final Selection

```
Selected:
e ( h , 2 )
```

---

## ✅ Final MST Edges

```
a – b (4)
b – c (8)
c – d (7)
c – i (2)
i – g (6)
g – h (1)
h – e (2)
```

---

## 💰 Total Cost of MST

```
4 + 8 + 7 + 2 + 6 + 1 + 2 = 30
```

---

---

### 🧠 Prim's Algorithm – Minimum Spanning Tree (MST)
---

### 🧾 Pseudocode

```plaintext
MST-PRIM(G, w, r) // G: graph, w: weight function, r: initial vertex
1. for each u ∈ V[G]                      // for all vertices in the graph
2.     key[u] ← ∞                         // set cost of each vertex to ∞
3.     π[u] ← NIL                         // set parent of each vertex to NIL
4. key[r] ← 0                             // set cost of initial vertex to 0
5. Q ← V[G]                               // add all vertices to a priority queue
6. while Q ≠ ∅                            // repeat until Q is empty
7.     u ← EXTRACT-MIN(Q)                // extract min-cost vertex from Q
8.     for each v ∈ Adj[u]               // for all adjacent vertices
9.         if v ∈ Q and w(u, v) < key[v] // if v is in Q and edge weight is less
10.            π[v] ← u                  // update parent of v to u
11.            key[v] ← w(u, v)          // update cost of v
```

---

### 🧮 Key Concepts

- **key[u]**: Minimum weight to connect vertex `u` to the MST.
- **π[u]**: Parent of vertex `u` in the MST.
- **Q**: Priority queue containing all vertices not yet included in MST.
- **EXTRACT-MIN(Q)**: Retrieves vertex with the smallest key value.

---

#### ✅ Correctness
Prim’s algorithm **always yields a valid Minimum Spanning Tree** for a connected, weighted, undirected graph.

---

### ⏱️ Time Complexity
- **Using Binary Heap**: \( O(|E| \log |V|) \)
- **Using Fibonacci Heap**: \( O(|V| \log |V| + |E|) \)


---

## 🌉 Kruskal's Algorithm – Minimum Spanning Tree (MST)

### 📌 Overview
Kruskal's algorithm is a **greedy algorithm** used to find the **Minimum Spanning Tree (MST)** of a **weighted, connected, undirected graph**. It builds the MST by selecting edges in increasing order of weight, ensuring no cycles are formed.

---

### 🧾 Steps of Kruskal's Algorithm

1. **Sort all edges** in non-decreasing order of their weights.
2. **Initialize MST** as an empty set.
3. **For each edge (u, v)** in sorted order:
   - If `u` and `v` belong to **different trees** (i.e., no cycle is formed):
     - **Add edge (u, v)** to the MST.
     - **Union** the sets containing `u` and `v`.

---

### 🧮 Key Concepts

- **Greedy Choice**: Always pick the smallest weight edge that doesn't form a cycle.
- **Cycle Detection**: Use **Disjoint Set Union (DSU)** or **Union-Find** data structure.
- **Edge Sorting**: Crucial for the greedy approach.

---

## ✅ Correctness
Kruskal’s algorithm **always yields an optimal MST** for a connected, undirected, weighted graph.

---

## ⏱️ Time Complexity
- **Sorting edges**: \( O(E \log E) \)
- **Union-Find operations**: \( O(E \cdot \alpha(V)) \), where \( \alpha \) is the inverse Ackermann function.

---


---

---

## ⚔️ Prim’s vs Kruskal’s Algorithm – MST Comparison

### 📌 When to Use

| Algorithm        | Preferred When…                                      |
|------------------|------------------------------------------------------|
| **Prim’s**       | Graph is **dense** (many edges), \( E = O(V^2) \)    |
| **Kruskal’s**    | Graph is **sparse** (few edges), \( E = O(V) \)      |
|                  | Edges are already sorted or sortable in linear time  |

---

### 🔍 Key Differences

| Feature               | **Prim’s Algorithm**                                      | **Kruskal’s Algorithm**                                  |
|-----------------------|-----------------------------------------------------------|-----------------------------------------------------------|
| **Approach**          | Vertex-based: grows MST one vertex at a time              | Edge-based: adds edges in increasing weight order         |
| **Graph Representation** | Adjacency matrix                                       | Edge list                                                 |
| **Initialization**    | Starts from an arbitrary vertex                           | Starts with all vertices as separate trees (forest)       |
| **Edge Selection**    | Chooses minimum weight edge from connected vertices       | Chooses minimum weight edge from all edges                |
| **Cycle Detection**   | Implicit via visited vertices                             | Explicit via Union-Find (Disjoint Set Union)              |
| **Suitable For**      | Dense graphs                                              | Sparse graphs                                              |
| **Starting Point**    | Requires a starting vertex                                | No specific starting point                                |

---

### ✅ Summary

- **Prim’s** is ideal for dense graphs and uses a priority queue to grow the MST from a starting vertex.
- **Kruskal’s** is better for sparse graphs and builds the MST by sorting edges and connecting disjoint sets.

---

##### Dijkstras Algorithm Single Source Shortest Path

# 🛣️ Dijkstra’s Algorithm – Single Source Shortest Path

## 📌 Overview
Dijkstra’s algorithm finds the **shortest path** from a **single source vertex** to all other vertices in a **weighted, directed graph** with **non-negative edge weights**.

---

## 🧾 Pseudocode

```plaintext
Dijkstra(G, w, s)
1. Initialize-Single-Source(G, s)
2. S = ∅
3. Q = G.V
4. while Q ≠ ∅
5.     u = Extract-Min(Q)
6.     S = S ∪ {u}
7.     for each vertex v ∈ G.Adj[u]
8.         Relax(u, v, w)

Relax(u, v, w)
1. if v.d > u.d + w(u, v)
2.     v.d = u.d + w(u, v)
3.     v.π = u

Initialize-Single-Source(G, s)
1. for each vertex v ∈ G.V
2.     v.d = ∞
3.     v.π = NIL
4. s.d = 0
```

---

## 🧮 Key Concepts

- **v.d**: Current shortest distance from source `s` to vertex `v`.
- **v.π**: Predecessor of `v` on the shortest path.
- **Relaxation**: Updates `v.d` if a shorter path is found via `u`.

### Relaxation Formula:
\[
v.d = \min(v.d, u.d + w(u,v))
\]

---

## ✅ Correctness
Dijkstra’s algorithm **correctly computes shortest paths** from the source to all reachable vertices, provided all edge weights are non-negative.

---

## ⏱️ Time Complexity
- **Using Binary Heap + Adjacency List**: \( O((V + E) \log V) \)
- **Using Fibonacci Heap**: \( O(E + V \log V) \)

---

## 📊 Example Graph

### Vertices: S, A, B, C, D  
### Edges and Weights:
- S → A = 10  
- S → C = 5  
- C → A = 3  
- C → D = 2  
- A → B = 1  
- D → B = 6  
- C → B = 9  

### Step-by-Step Execution:
1. **Start at S**:  
   - S.d = 0  
   - A.d = ∞ → updated to 10  
   - C.d = ∞ → updated to 5  

2. **Extract C (5)**:  
   - A.d = min(10, 5+3) = 8  
   - D.d = min(∞, 5+2) = 7  

3. **Extract D (7)**:  
   - B.d = min(∞, 7+6) = 13  

4. **Extract A (8)**:  
   - B.d = min(13, 8+1) = 9  

5. **Extract B (9)**: Final shortest path tree formed.

---



## 📊 Example

<img width="163" height="85" alt="image" src="https://github.com/user-attachments/assets/bc54d763-aece-409b-8134-bd2027069256" />

### Given Edges and Weights:
```
<c, d> = 1
<c, f> = 2
<d, e> = 2
<a, b> = 3
<g, h> = 3
<b, c> = 4
<e, f> = 5
<a, d> = 6
<b, e> = 8
<d, g> = 9
<b, d> = 70
```

### Sorted Edge List:
1. <c, d> = 1  
2. <c, f> = 2  
3. <d, e> = 2  
4. <a, b> = 3  
5. <g, h> = 3  
6. <b, c> = 4  
7. <e, f> = 5  
8. <a, d> = 6  
9. <b, e> = 8  
10. <d, g> = 9  
11. <b, d> = 70  

### Selected Edges for MST:
- <c, d>, <c, f>, <d, e>, <a, b>, <g, h>, <b, c>, <e, f>, <a, d>

### Final MST Cost:
```
Cost = 1 + 2 + 2 + 3 + 3 + 4 + 5 + 6 = 26
```

---

---

###### Floyd Warshall Algorithm All-Pairs Shortest Path

# 🔁 Floyd-Warshall Algorithm – All-Pairs Shortest Path

## 📌 Overview
The **Floyd-Warshall Algorithm** is a **dynamic programming** technique used to find the **shortest paths between all pairs of vertices** in a weighted graph.

- Works for **directed and undirected graphs**
- Handles **positive and negative edge weights**
- **Fails** if the graph contains a **negative cycle**
- Also computes the **transitive closure** of a graph

---

## 🧾 Algorithm Steps

1. **Create a matrix** `D` representing the graph’s edge weights.
2. **Initialize** `D[i][j]` with:
   - `0` if `i == j`
   - `w(i, j)` if edge exists
   - `∞` if no edge exists
3. For each vertex `k` from `1` to `n`:
   - For each pair `(i, j)`:
     - Update `D[i][j] = min(D[i][j], D[i][k] + D[k][j])`

---

## 🧮 Pseudocode

```plaintext
Floyd-Warshall(w)
1. n = number of vertices
2. D⁰ = w
3. for k = 1 to n
4.     for i = 1 to n
5.         for j = 1 to n
6.             Dᵏ[i][j] = min(Dᵏ⁻¹[i][j], Dᵏ⁻¹[i][k] + Dᵏ⁻¹[k][j])
7. return Dⁿ
```

---

## ✅ Correctness
The algorithm guarantees the shortest path between every pair of vertices **if no negative cycles exist**.

---

## ⏱️ Time Complexity
- **O(n³)** where `n` is the number of vertices

---

## 📊 Example Use Case

Given a graph with vertices A, B, C, D, E and edge weights:

- A → B = 10  
- A → C = 30  
- A → D = 50  
- B → D = 20  
- C → D = 10  
- D → E = 30  

The algorithm iteratively updates the shortest paths using intermediate vertices and computes the final shortest distance matrix.

---



<img width="520" height="297" alt="image" src="https://github.com/user-attachments/assets/1937256f-8754-4f9d-b741-c0a41407463e" />


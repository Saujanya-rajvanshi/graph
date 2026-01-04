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

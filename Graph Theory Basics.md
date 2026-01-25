# **Module 1.4: Graph Theory Basics**
*Duration: 3-4 weeks*

## **Week 1: Introduction to Graphs and Basic Terminology**

### **1.1 What is a Graph?**

#### **Formal Definition**
- A graph **G = (V, E)** consists of:
  - **V**: A nonempty set of vertices (nodes, points)
  - **E**: A set of edges (links, lines) connecting pairs of vertices
- **Order**: |V| = number of vertices
- **Size**: |E| = number of edges
- *CS Connection*: Networks, relationships, state machines, data structures

#### **Types of Graphs**
1. **Undirected Graph**: Edges have no direction (unordered pairs)
   - Edge {u, v} = {v, u}
   - *Examples*: Friendship network, road connections

2. **Directed Graph (Digraph)**: Edges have direction (ordered pairs)
   - Edge (u, v) ≠ (v, u)
   - *Examples*: Web links, state transitions, dependencies

3. **Weighted Graph**: Edges have numerical weights
   - *Examples*: Network latency, road distances, costs

4. **Simple Graph**: No loops (edge from vertex to itself) and no multiple edges

5. **Multigraph**: May have multiple edges between same vertices

6. **Pseudograph**: May have loops and multiple edges

#### **Important Graph Families**
- **Complete Graph (Kₙ)**: Every pair of vertices connected by edge
  - |E| = n(n-1)/2 for undirected
- **Cycle Graph (Cₙ)**: Vertices arranged in a cycle
- **Path Graph (Pₙ)**: Vertices arranged in a path
- **Star Graph**: One central vertex connected to all others
- **Wheel Graph**: Cycle + central vertex connected to all
- **Bipartite Graph**: V can be partitioned into U, W with all edges between U and W
  - *Complete Bipartite Kₘ,ₙ*: All possible edges between parts

### **1.2 Basic Terminology**

#### **Vertex Relationships**
- **Adjacent vertices**: Connected by an edge
- **Incident**: Edge e is incident to vertices u and v if e = {u,v} or (u,v)
- **Neighborhood N(v)**: Set of vertices adjacent to v
  - *Closed neighborhood*: N[v] = N(v) ∪ {v}
- **Degree** (undirected):
  - deg(v) = number of edges incident to v (loops count twice)
  - *Isolated vertex*: deg(v) = 0
  - *Pendant vertex*: deg(v) = 1
- **In-degree/Out-degree** (directed):
  - deg⁺(v) = number of edges leaving v
  - deg⁻(v) = number of edges entering v

#### **Handshaking Theorem**
- **Undirected**: ∑_{v∈V} deg(v) = 2|E|
  - *Corollary*: Number of vertices with odd degree is even
- **Directed**: ∑_{v∈V} deg⁺(v) = ∑_{v∈V} deg⁻(v) = |E|

#### **Subgraphs**
- **Subgraph H of G**: V(H) ⊆ V(G) and E(H) ⊆ E(G)
- **Induced Subgraph**: Contains all edges of G between vertices in H
- **Spanning Subgraph**: Contains all vertices of G

### **1.3 Graph Representations in CS**

#### **Adjacency Matrix**
- A[i][j] = 1 if edge from i to j (0 otherwise)
- **Undirected**: Symmetric matrix
- **Weighted**: A[i][j] = weight
- **Space**: O(|V|²)
- **Advantages**: O(1) edge lookup, easy to implement
- **Disadvantages**: Wastes space for sparse graphs

#### **Adjacency List**
- Array of lists: list[i] contains neighbors of vertex i
- **Space**: O(|V| + |E|)
- **Advantages**: Efficient for sparse graphs, natural for traversal
- **Disadvantages**: O(deg(v)) edge lookup

#### **Edge List**
- List of tuples (u, v, weight)
- **Space**: O(|E|)
- **Advantages**: Simple, good for edge-based algorithms
- **Disadvantages**: O(|E|) neighbor lookup

#### **Comparison Table**
| Representation | Space | Edge Query | List Neighbors | Add Vertex | Add Edge |
|---------------|-------|------------|----------------|------------|----------|
| Adj Matrix | O(V²) | O(1) | O(V) | O(V²) | O(1) |
| Adj List | O(V+E) | O(deg(v)) | O(deg(v)) | O(1) | O(1) |
| Edge List | O(E) | O(E) | O(E) | O(1) | O(1) |

### **Practice Problems: Week 1**

#### **Basic Concepts**
1. For a simple undirected graph with 10 vertices, maximum edges? (45)
2. For K₅, list all degrees. (All 4)
3. Draw all simple graphs with 3 vertices (up to isomorphism)

#### **Handshaking Applications**
1. Prove: In any graph, at least two vertices have same degree
2. Is there a graph with degree sequence (3,3,3,3,3,3)? Why?
3. Show: Sum of degrees = twice number of edges

#### **Graph Representations**
1. Given adjacency matrix, convert to adjacency list
2. Implement Graph class with both representations
3. Compare storage for |V|=1000, |E|=5000

#### **CS Applications**
1. **Social Network**: Undirected graph, vertices=users, edges=friendships
   - Degree = number of friends
   - Adjacency matrix vs list for 1M users?
2. **Web Graph**: Directed, vertices=pages, edges=links
   - PageRank uses random walks on this graph
3. **State Machine**: Directed, vertices=states, edges=transitions
   - Model program execution

## **Week 2: Connectivity and Traversal**

### **2.1 Paths and Connectivity**

#### **Paths and Cycles**
- **Walk**: Sequence v₀, e₁, v₁, e₂, ..., eₖ, vₖ where eᵢ = (vᵢ₋₁, vᵢ)
- **Trail**: Walk with no repeated edges
- **Path**: Walk with no repeated vertices
- **Cycle**: Path that starts and ends at same vertex (length ≥ 3 for simple graph)
- **Length**: Number of edges

#### **Connectivity**
- **Connected Graph**: Path between every pair of vertices (undirected)
- **Connected Components**: Maximal connected subgraphs
- **k-Connected**: Removing fewer than k vertices doesn't disconnect
- **Cut Vertex/Articulation Point**: Removing it increases components
- **Bridge/Cut Edge**: Removing it increases components

#### **Connectivity in Digraphs**
- **Strongly Connected**: Directed path both ways between every pair
- **Weakly Connected**: Underlying undirected graph is connected
- **Strongly Connected Components (SCCs)**: Maximal strongly connected subgraphs

### **2.2 Graph Traversal Algorithms**

#### **Depth-First Search (DFS)**
```python
def dfs(graph, start):
    visited = set()
    stack = [start]
    while stack:
        vertex = stack.pop()
        if vertex not in visited:
            visited.add(vertex)
            # Process vertex
            stack.extend(neighbors(vertex) - visited)
```
- **Uses**: Stack (LIFO), recursion natural
- **Applications**: Topological sort, cycle detection, connected components
- **Complexity**: O(|V| + |E|) for adjacency list

#### **Breadth-First Search (BFS)**
```python
def bfs(graph, start):
    visited = set()
    queue = deque([start])
    while queue:
        vertex = queue.popleft()
        if vertex not in visited:
            visited.add(vertex)
            # Process vertex
            queue.extend(neighbors(vertex) - visited)
```
- **Uses**: Queue (FIFO)
- **Applications**: Shortest paths (unweighted), level-order traversal
- **Complexity**: O(|V| + |E|) for adjacency list

#### **DFS vs BFS Comparison**
| Aspect | DFS | BFS |
|--------|-----|-----|
| Data Structure | Stack | Queue |
| Memory | O(height) | O(width) |
| Finds Shortest Path? | No | Yes (unweighted) |
| Applications | Topological sort, backtracking | Shortest paths, web crawling |

### **2.3 Applications of Traversal**

#### **Connected Components (Undirected)**
```python
def connected_components(graph):
    visited = set()
    components = []
    for vertex in graph.vertices:
        if vertex not in visited:
            component = set()
            dfs_from(vertex, visited, component)
            components.append(component)
    return components
```

#### **Cycle Detection**
- **Undirected**: DFS, if back-edge to visited (not parent) → cycle
- **Directed**: DFS with three colors (white=unvisited, gray=visiting, black=visited)

#### **Topological Sort (DAGs)**
- Linear ordering where for edge (u,v), u comes before v
- **Algorithm**: DFS, add vertex to front when finished
- **Application**: Task scheduling, dependency resolution

### **Practice Problems: Week 2**

#### **Paths and Cycles**
1. Find all simple paths from A to D in given graph
2. Prove: If all vertices have degree ≥ 2, graph contains a cycle
3. In bipartite graph, all cycles have even length

#### **Connectivity**
1. Find articulation points and bridges in a graph
2. Determine if directed graph is strongly connected
3. Compute number of connected components

#### **Traversal Implementation**
1. Implement DFS recursively and iteratively
2. Implement BFS to find shortest path length
3. Use DFS for topological sort

#### **CS Applications**
1. **Garbage Collection**: Objects as vertices, references as edges
   - Mark-and-sweep = DFS from roots
2. **Code Analysis**: Call graph (functions as vertices, calls as edges)
   - Find unreachable code
3. **Network Analysis**:
   - BFS for shortest propagation time
   - DFS for exploring network structure

## **Week 3: Trees and Special Graphs**

### **3.1 Trees**

#### **Tree Definitions**
- **Tree**: Connected, acyclic undirected graph
- **Forest**: Collection of trees (acyclic, not necessarily connected)
- **Rooted Tree**: Tree with designated root vertex
- **Properties** (equivalent for simple graph with n vertices):
  1. Connected and has n-1 edges
  2. Acyclic and has n-1 edges
  3. Connected and acyclic
  4. Unique path between any two vertices

#### **Tree Terminology**
- **Parent/Child**: In rooted tree, parent is closer to root
- **Ancestor/Descendant**: Transitive closure of parent/child
- **Siblings**: Vertices with same parent
- **Leaf**: Vertex with degree 1 (except root may be leaf)
- **Internal Vertex**: Non-leaf vertex
- **Level**: Distance from root
- **Height**: Maximum level

#### **Binary Trees**
- **Binary Tree**: Each vertex has at most 2 children
- **Full Binary Tree**: Every vertex has 0 or 2 children
- **Complete Binary Tree**: All levels filled except last, filled left to right
- **Properties**:
  - Maximum nodes at level i: 2ⁱ
  - Maximum nodes in tree of height h: 2ʰ⁺¹ - 1
  - Height of complete tree with n nodes: ⌊log₂ n⌋

### **3.2 Spanning Trees**

#### **Definition**
- **Spanning Tree** of connected graph G: Subgraph that is tree and includes all vertices
- Every connected graph has at least one spanning tree
- **Number of spanning trees**: Kirchhoff's theorem (matrix tree theorem)

#### **Minimum Spanning Tree (MST)**
- For weighted graph, spanning tree with minimum total weight
- **Algorithms**:
  1. **Kruskal's**: Sort edges, add cheapest that doesn't create cycle
  2. **Prim's**: Grow tree from vertex, add cheapest edge connecting tree to new vertex
- **Applications**: Network design, clustering, approximation algorithms

### **3.3 Special Graph Classes**

#### **Planar Graphs**
- Can be drawn in plane without edge crossings
- **Euler's Formula**: For connected planar graph: v - e + f = 2
  - v = vertices, e = edges, f = faces
- **Corollaries**:
  - e ≤ 3v - 6 (for v ≥ 3, no triangles: e ≤ 2v - 4)
  - K₅ and K₃,₃ are non-planar
- **Applications**: Circuit board layout, map coloring

#### **Bipartite Graphs**
- V = X ∪ Y, all edges between X and Y
- **Characterization**: No odd cycles
- **Maximum Matching**: Maximum set of edges with no shared vertices
- **Applications**: Assignment problems, dating/matching

#### **Eulerian and Hamiltonian Graphs**
- **Eulerian Path**: Visits every edge exactly once
  - Exists iff 0 or 2 vertices have odd degree (connected)
- **Eulerian Circuit**: Eulerian path that's a cycle
  - Exists iff all vertices have even degree (connected)
- **Hamiltonian Path**: Visits every vertex exactly once
- **Hamiltonian Cycle**: Hamiltonian path that's a cycle
  - NP-complete to determine existence

### **Practice Problems: Week 3**

#### **Trees**
1. Prove: Tree with n vertices has n-1 edges
2. Find all non-isomorphic trees with 5 vertices (3 trees)
3. Implement tree traversals: preorder, inorder, postorder

#### **Spanning Trees**
1. Apply Kruskal's and Prim's to find MST
2. Prove: If all edge weights distinct, MST is unique
3. Implement union-find for Kruskal's

#### **Special Graphs**
1. Check if graph is bipartite using BFS coloring
2. Determine if graph has Eulerian path/circuit
3. Draw K₄ as planar graph

#### **CS Applications**
1. **File System**: Tree structure (directories = internal vertices, files = leaves)
2. **Network Routing**: Spanning tree for broadcast (STP protocol)
3. **Circuit Design**: Planar graphs for PCB layout
4. **Job Assignment**: Bipartite matching (workers ↔ tasks)

## **Week 4: Graph Algorithms and Applications**

### **4.1 Shortest Path Algorithms**

#### **Single-Source Shortest Path**
1. **BFS**: For unweighted graphs, O(V+E)
2. **Dijkstra's Algorithm**: Non-negative weights, O((V+E) log V) with heap
   ```python
   def dijkstra(graph, source):
       dist = {v: float('inf') for v in graph}
       dist[source] = 0
       pq = [(0, source)]
       while pq:
           d, u = heappop(pq)
           if d > dist[u]:
               continue
           for v, w in graph[u]:
               if dist[u] + w < dist[v]:
                   dist[v] = dist[u] + w
                   heappush(pq, (dist[v], v))
       return dist
   ```

3. **Bellman-Ford**: Handles negative weights, detects negative cycles, O(VE)
   - Relax all edges V-1 times

#### **All-Pairs Shortest Path**
- **Floyd-Warshall**: Dynamic programming, O(V³)
  ```python
  def floyd_warshall(graph):
      dist = [[float('inf')] * n for _ in range(n)]
      for i in range(n):
          dist[i][i] = 0
      for u, v, w in edges:
          dist[u][v] = w
      for k in range(n):
          for i in range(n):
              for j in range(n):
                  if dist[i][j] > dist[i][k] + dist[k][j]:
                      dist[i][j] = dist[i][k] + dist[k][j]
      return dist
  ```

### **4.2 Network Flow**

#### **Max Flow - Min Cut Theorem**
- **Flow Network**: Directed graph with source s, sink t, capacities on edges
- **Maximum Flow**: Maximum amount that can flow from s to t
- **Minimum Cut**: Minimum capacity cut separating s and t
- **Ford-Fulkerson Method**: Augmenting path algorithm
- **Edmonds-Karp**: BFS for augmenting paths (O(VE²))

#### **Applications of Flow**
- **Bipartite Matching**: Convert to flow problem
- **Project Selection**: Max flow with profits/costs
- **Image Segmentation**: Graph cut algorithms

### **4.3 Graph Coloring**

#### **Vertex Coloring**
- **Proper Coloring**: Assign colors to vertices so adjacent vertices different
- **Chromatic Number χ(G)**: Minimum colors needed
- **Bounds**:
  - χ(G) ≤ Δ(G) + 1 (Δ = maximum degree)
  - For planar graphs: χ(G) ≤ 4 (Four Color Theorem)
- **Applications**: Register allocation, scheduling, frequency assignment

#### **Greedy Coloring**
- Color vertices in some order, use smallest available color
- Works well with appropriate ordering (largest-degree-first, etc.)

### **4.4 Advanced Topics Preview**

#### **Random Graphs**
- **Erdős–Rényi G(n,p)**: n vertices, each edge with probability p
- **Properties**: Phase transitions (connectivity, giant component)

#### **Small-World Networks**
- High clustering, short average path length
- **Watts-Strogatz model**: Rewire regular lattice

#### **Scale-Free Networks**
- Power-law degree distribution
- **Barabási–Albert model**: Preferential attachment

### **Practice Problems: Week 4**

#### **Shortest Paths**
1. Implement Dijkstra's with binary heap
2. Apply Bellman-Ford to detect negative cycles
3. Use Floyd-Warshall for all-pairs on small graph

#### **Network Flow**
1. Implement Edmonds-Karp for max flow
2. Solve bipartite matching via flow
3. Find min cut in flow network

#### **Graph Coloring**
1. Color map using 4 colors
2. Implement greedy coloring with different orderings
3. Model course scheduling as graph coloring

#### **CS Applications**
1. **GPS Navigation**: Dijkstra/A* for shortest path
2. **Internet Routing**: Bellman-Ford (distance vector), Dijkstra (link state)
3. **Compiler Optimization**: Graph coloring for register allocation
4. **Social Network Analysis**: Betweenness centrality, communities

## **Comprehensive Assessment for Module 1.4**

### **Theory Exam (Sample)**
**Part A: Definitions (20%)**
1. Define: tree, bipartite graph, Eulerian circuit, chromatic number
2. Explain: DFS vs BFS, when to use each

**Part B: Proofs (25%)**
1. Prove: Tree with n vertices has n-1 edges
2. Prove: In any graph, number of odd-degree vertices is even
3. Prove: If G is bipartite, it has no odd cycles

**Part C: Problems (30%)**
1. Given adjacency list, perform DFS and BFS
2. Find MST using Kruskal's algorithm
3. Use Dijkstra's to find shortest paths from source

**Part D: Applications (25%)**
1. Model a computer network as graph, identify critical nodes (articulation points)
2. Schedule exams (courses conflict if shared students) using graph coloring
3. Design database schema for social network graph

### **Practical Implementation Projects**

#### **Project 1: Graph Algorithm Library**
```python
class Graph:
    def __init__(self, directed=False):
        self.adj_list = {}
        self.directed = directed
    
    def add_vertex(self, v):
        # Implement
        
    def add_edge(self, u, v, weight=1):
        # Implement
    
    def dfs(self, start):
        # Implement with stack
        
    def bfs(self, start):
        # Implement with queue
        
    def dijkstra(self, source):
        # Implement
        
    def kruskal_mst(self):
        # Implement
        
    def is_bipartite(self):
        # Implement with BFS coloring
```

#### **Project 2: Social Network Analyzer**
- Build graph from Twitter/Reddit data (or synthetic)
- Compute:
  - Degree distribution
  - Connected components
  - Diameter (longest shortest path)
  - Clustering coefficient
  - PageRank or centrality measures

#### **Project 3: Pathfinding Visualizer**
- Grid-based graph (obstacles as blocked vertices)
- Implement BFS, Dijkstra, A*
- Visualize algorithm steps
- Compare performance

### **Common CS Interview Questions Covered**
1. "Clone a graph" (BFS/DFS with mapping)
2. "Course schedule" (topological sort on DAG)
3. "Number of islands" (connected components in grid)
4. "Word ladder" (BFS on implicit graph)
5. "Network delay time" (Dijkstra's algorithm)

### **Transition Checklist to Phase 2**
Before moving to Calculus, ensure you can:
- ✅ Represent graphs in code (adjacency list/matrix)
- ✅ Implement DFS/BFS and know their applications
- ✅ Find shortest paths (BFS for unweighted, Dijkstra for weighted)
- ✅ Find MST (Kruskal/Prim)
- ✅ Detect cycles, connected components
- ✅ Model problems as graphs (networks, relationships, states)

### **Resources for Module 1.4**

#### **Primary Texts**
- "Introduction to Algorithms" (CLRS) - Graph chapters
- "Algorithm Design Manual" by Skiena - Practical graph algorithms
- "Graph Theory" by Diestel (advanced)

#### **Interactive Tools**
- **Graphviz**: Visualize graphs from dot language
- **Gephi**: Network analysis and visualization
- **NetworkX** (Python): Graph library with algorithms

#### **Visual Learning**
- **3Blue1Brown**: "Graph Theory" series
- **VisuAlgo**: Interactive algorithm visualizations
- **Red Blob Games**: Pathfinding tutorials

#### **Practice Platforms**
- **LeetCode**: Graph tag (200+ problems)
- **HackerRank**: Graph theory section
- **Project Euler**: Some graph-based problems

---

**Next Phase**: **Phase 2: Calculus & Continuous Mathematics** - We'll transition from discrete structures to continuous mathematics, starting with limits and derivatives.

**Immediate Action**: Complete the Module 1.4 assessment. If you struggle with graph algorithms, practice by implementing them from scratch and solving problems on LeetCode. Remember: graphs model relationships everywhere in CS!

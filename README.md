# network_analysis
  Answers about Network Analysis exercises

1. Define:

  (a) Subgraph: A subgraph is a graph that is obtained by removing some vertices and/or edges from an original graph while preserving the connectivity among the remaining vertices. In other words, a subgraph of a graph G is a graph that is obtained by deleting some vertices and edges from G.

  (b) Bipartite graph: A bipartite graph is a graph whose vertices can be divided into two disjoint sets, such that every edge of the graph connects a vertex from one set to a vertex from the other set. In other words, a graph G is bipartite if its vertex set can be partitioned into two sets V1 and V2 such that every edge in G connects a vertex in V1 to a vertex in V2.

  (c) Hamiltonian graph: A Hamiltonian graph is a graph that contains a Hamiltonian cycle, which is a cycle that visits every vertex of the graph exactly once. In other words, a graph G is Hamiltonian if there exists a cycle that passes through every vertex of G exactly once.

  (d) Eulerian graph: An Eulerian graph is a graph that contains an Eulerian cycle, which is a cycle that traverses every edge of the graph exactly once. In other words, a graph G is Eulerian if there exists a cycle that covers every edge of G exactly once.

2. Describe how a breadth-first search algorithm works. 

  A breadth-first search algorithm (BFS) is a graph traversal algorithm that visits all the vertices of a graph in breadth-first order. It starts from a source vertex, maintains a queue of vertices yet to be visited, and visits all adjacent vertices of a dequeued vertex before enqueuing them. The BFS algorithm ensures that the shortest path to all reachable vertices from the source vertex is obtained. It can also be used to determine whether a path exists between two vertices and to find the shortest path between them. BFS can be implemented using a queue data structure and a visited array or set to keep track of visited vertices.

3. How many edges does a complete graph with n vertices have? What about a complete directed graph with n vertices?

  A complete graph with n vertices has n(n-1)/2 edges. This is because every vertex is connected to every other vertex in the graph, except itself, resulting in (n-1) edges for each vertex. However, each edge is counted twice since it connects two vertices, so the total number of edges is n(n-1)/2.

  On the other hand, a complete directed graph with n vertices has n(n-1) directed edges. This is because each vertex has n-1 outgoing edges to connect to all other vertices in the graph, resulting in a total of n(n-1) directed edges.


4. What are isomorphic graphs? Draw an example.

  Isomorphic graphs are graphs that have the same structure, but may differ in vertex and edge labels. That is, two graphs are isomorphic if one graph can be obtained from the other by relabeling its vertices and edges. Formally, two graphs G and H are isomorphic if there exists a bijective function f from the vertices of G to the vertices of H, such that two vertices u and v in G are adjacent if and only if f(u) and f(v) in H are adjacent.

  ```ruby
  import networkx as nx

  G1 = nx.Graph()
  G1.add_edges_from([(1, 2), (1, 3), (2, 4), (3, 4)])

  G2 = nx.Graph()
  G2.add_edges_from([(5, 6), (5, 7), (6, 8), (7, 8)])

  mapping = {5: 1, 6: 2, 7: 3, 8: 4}
  G2 = nx.relabel_nodes(G2, mapping)

  print(nx.is_isomorphic(G1, G2))
  ```

5. Calculate the degree of the nodes for both node types in the bipartite adjacency matrix from the figure below. Find the isolated node(s).

  G1 = 2
  G2 = 3
  G3 = 4
  G4 = 2
  G5 = 3
  G6 = 1
  G7 = 0
  G8 = 2
  G9 = 1


6. Given the digraph G = (V, E) where V = {M, N, O, P, Q, R, S} and E ={(M, S), (N, O), (P, R), (N, S), (O, M), (N, Q), (O, M), (P, P), (S, M), (O, N), (S, M), (N, R), (P, M), (M, S)}

  (a) There is a simple path from vertex M to vertex S: M -> S.

  (b) There is a simple cycle involving at least 4 nodes: N -> O -> M -> S -> N.

  (c) The digraph is not strongly connected, as there is no path from vertex P to any other vertex, and no path from vertex Q to any other vertex.

  (d) The degree of vertex N is 3 (outgoing edges to O, S, and Q), and the degree of vertex R is 1 (outgoing edge to P).

  (e) The adjacency list representation of the digraph is:

  M: S
  N: O, S, Q
  O: M, N
  P: R, P, M
  Q:
  R:
  S: M

  (f) The adjacency matrix representation of the digraph is:

    M N O P Q R S
  M 0 0 1 0 0 0 1
  N 0 0 1 0 1 0 1
  O 1 1 0 0 0 0 0
  P 1 0 0 0 0 1 0
  Q 0 0 0 0 0 0 0
  R 0 0 0 1 0 0 0
  S 1 1 0 0 0 0 0

7.Draw the undirected and directed versions of the graph G(V, E), where V = {1, 2, 3, 4, 5, 6} and E = {(2, 5), (6, 1), (5, 3), (2, 3)}.

```ruby
import networkx as nx
import matplotlib.pyplot as plt

V = [1, 2, 3, 4, 5, 6]
E = [(2, 5), (6, 1), (5, 3), (2, 3)]
G = nx.Graph()
G.add_nodes_from(V)
G.add_edges_from(E)

pos = nx.spring_layout(G)
nx.draw_networkx_nodes(G, pos, node_color='lightblue')
nx.draw_networkx_edges(G, pos)
nx.draw_networkx_labels(G, pos)
plt.axis('off')
plt.show()

D = nx.DiGraph()
D.add_nodes_from(V)
D.add_edges_from(E)
pos = nx.spring_layout(D)
nx.draw_networkx_nodes(D, pos, node_color='lightblue')
nx.draw_networkx_edges(D, pos)
nx.draw_networkx_labels(D, pos)
plt.axis('off')
plt.show()
```

8. How many edges does a graph have 3 vertices of degree 3 and one vertex of degree 5?

  Total degree = 3x3 + 5 = 14
  Total edges = Total degree / 2 = 7


9.Mr. A is friend with Mrs. B, but she doesn't like him back. She has a reciprocal friendship with both C and D, but only C considers D a friend. D has also sent friend requests to E, F, G, and H but, so far, only G replied. G also has a reciprocal relationship with A. Draw the corresponding directed graph.


10. Draw the graph from the previous exercise as undirected and weighted, with the weight being 2 if the connection is reciprocal, 1 otherwise.

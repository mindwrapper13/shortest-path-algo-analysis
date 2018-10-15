# Advanced Shortest Path Algorithms

This project implements three advanced shortest path algorithms in Java: Contraction Hierarchies, A-Star, and Bidirectional Dijkstra. The code has been thoroughly tested and verified for performance and accuracy.

## Bidirectional Dijkstra Algorithm
Bidirectional Dijkstra runs two simultaneous searches—one from the start node and one from the goal—stopping when they meet. It optimizes pathfinding by reducing the search space and improving efficiency.

### Algorithm:
1. Build a graph using an adjacency list.
2. Create a reverse graph from the original.
3. Run Dijkstra from the source in the forward graph and from the target in the reverse graph.
4. Alternate between steps in the forward and reverse graphs.
5. Stop when a vertex is processed in both graphs.
6. Calculate the minimum distance by summing distances from source to that vertex and from that vertex to the target.
7. Print the shortest path distance.

## A-Star Algorithm
A* is widely used in pathfinding due to its efficiency and accuracy. It combines the actual distance from the start (g) and an estimated distance to the goal (h), using a heuristic approach to prioritize nodes with the lowest combined cost.

### Algorithm:
1. Pick the node with the lowest f = g + h.
2. g is the distance from the start to the current node.
3. h is a heuristic, such as the Euclidean distance from the current node to the target.
4. Continue until the target is reached or no path exists.

## Contraction Hierarchies Algorithm
Contraction Hierarchies significantly speeds up shortest path searches by precomputing a contracted graph, reducing the number of vertices during the actual search. It's commonly used in advanced routing systems.

### Algorithm:
1. Read input vertices and edges to construct the graph.
2. Preprocess the graph by contracting vertices in order of importance.
3. Use a modified Bidirectional Dijkstra for efficient pathfinding between the source and target.

### Preprocessing Steps:
- **Order by Importance:** Contract the least important vertices first.
- **Contraction Steps:**
  1. Use a priority queue to keep track of vertices by decreasing importance.
  2. Recompute importance during contraction.
  3. Store contracted vertices in increasing order.
  
### Importance Criteria:
- **Edge Difference:** The difference between added shortcuts and original edges.
- **Contracted Neighbors:** Favor vertices with fewer contracted neighbors.
- **Shortcut Cover:** The number of neighbors requiring shortcuts after contraction.

### Modified Bidirectional Dijkstra:
- Use only upward edges between contracted vertices.
- Continue processing until no nodes are left to process in both searches.

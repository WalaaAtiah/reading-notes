# Read 27 - Graphs

## Graphs [source](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/graphs.html)


**A graph is a non-linear data structure that can be looked at as a collection of vertices (or nodes) potentially connected by line segments named edges.**



### Here is some common terminology used when working with Graphs:

1. Vertex - A vertex, also called a “node”, is a data object that can have zero or more adjacent vertices.
   
2. Edge - An edge is a connection between two nodes.
   
3. Neighbor - The neighbors of a node are its adjacent nodes, i.e., are connected via an edge.
   
4. Degree - The degree of a vertex is the number of edges connected to that vertex.


### Directed vs Undirected

**Undirected Graphs**:An Undirected Graph is a graph where each edge is undirected or bi-directional. This means that the undirected graph does not move in any direction.

<img src="https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/UndirectedGraph.PNG" >



**Directed Graphs (Digraph)**:A Directed Graph also called a Digraph is a graph where every edge is directed.

Unlike an undirected graph, a Digraph has direction. Each node is directed at another node with a specific requirement of what node should be referenced next.

<img src="https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/DirectedGraph.PNG" >


### Complete vs Connected vs Disconnected

**Complete Graphs**
A complete graph is when all nodes are connected to all other nodes.

**Connected**
A connected graph is graph that has all of vertices/nodes have at least one edge.

**Disconnected**
A disconnected graph is a graph where some vertices may not have edges.


### Acyclic vs Cyclic

**Acyclic Graph**
An acyclic graph is a directed graph without cycles.

A cycle is when a node can be traversed through and potentially end up back at itself.

**Cyclic Graphs**
A Cyclic graph is a graph that has cycles.

A cycle is defined as a path of a positive length that starts and ends at the same vertex.



### Graph Representation
We represent graphs through:

1. Adjacency Matrix
2. Adjacency List


### Adjacency Matrix
An Adjacency matrix is represented through a 2-dimensional array. If there are n vertices, then we are looking at an n x n Boolean matrix

<img src="https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/AdjMatrix.PNG" >



### Adjacency List
An adjacency list is the most common way to represent graphs.

An adjacency list is a collection of linked lists or array that lists all of the other vertices that are connected.

<img src="https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/AdjList.PNG" >


### Weighted Graphs
A weighted graph is a graph with numbers assigned to its edges. These numbers are called weights. This is what a weighted graph looks like:

<img src="https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/weightGraph.PNG" >

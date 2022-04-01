# Reading Notes 35 -- Graphs

From the [Code Fellows article](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/graphs.html)

Graphs are a non-linear data structure. Graphs are made up of one or more nodes. There are numerous types of graphs that can various characteristics. Often, but not always, the nodes of a graph are connected -- much like a linked list or tree, but other many shapes as well.

- A **Vertex** is another term to describe the nodes of a graph
- An **Edge** is the term used to refer to the connection between two nodes.
- A **Neighbor** is a term to describe a node connected to the one in question.
- A **Degree** describes the number of edges connected to a vertex/node.

## Directionality 

*Undirected* graphs have nodes that do not have a direction. Each node is "dually linked" with its neighbor so there is not a specific directionality to the edges.

*Directed* graphs, or digraphs, do have a direction. Each node is directed at one or more nodes but not necessarily directed back at the node that points to it like an undirected graph. 

## Connections

A *complete* graph is one that each node is connected to all the other nodes in the graph.

A *connected* graph is one that each node has at least one edge. A tree is a type of connected graph.

A *disconnected* graphs is one where one or more nodes do not have edges.

A *cyclic* graph is a directed graph that has cycles in it. It contains a route between two or more nodes that completes a loop, or ends back at the place it started.

A *acyclic* graph is a directed graph that does not have any cycles. A tree is a DAG or directed acyclic graph.

## Representation

Graphs are represented in two main ways:

- *Adjacency Matix*: A two dimensional array the size of the number of vertices. Each row or column of the matrix indicates where that element has a connection.
  - These adjacency matrices can be *sparce* and have few connections or *dense* and have many connections.
- *Adjacency List*: Another more common way to represent a graph is by using a list of elements that contain a sublist of the connections. This could be represented with an array of linked lists or even an array of arrays. Unlike the adjacency matrix each element contains only its connections (not all of the nodes).

## Other

*Weighted graphs* are graphs that have extra information about the edges. Each edge has a number assigned. Instead of just a boolean value in the adjacency matrix to show connections a number can be used for weight. When represented by an adjacency list each element contains a connection as well as a value for the weight.

## Traversals

A *breadth first* traversal is similar to a breadth first traversal of a tree. Using a queue we can enqueue the initial node and then dequeue it. Every time we visit a node we add it to a visited set and then when we dequeue we also enqueue any connections that haven't been previously visited. We continue to do this until the queue is empty.

A *depth first* traversal is somewhat similar to a breadth first traversal of a graph. However instead of queue, a stack is used instead. Again we will need a set to keep track of all the visited nodes. To begin the initial node is added to the stack. Next we peek at the stack and see if the top of the stack has any connections that aren't in our visited set. We pop the stack and push any of the unvisited nodes back onto the stack. Continue this loop until the stack is empty.

# Reading Notes 15 -- Trees

From [Code Fellows Article](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-15/resources/Trees.html)

## Definition and Common Terms

A Tree data structure simulates a tree structure and is represented as a group of linked nodes.

- *Node* The structure that holds each element in the tree
- *Root* The "top" or beginning of the tree.
- *K* The number of children any node can have.
- *Left* A reference to a child node in a binary tree.
- *Right* The other node in a binary tree.
- *Edge* The link between a parent and child node.
- *Leaf* A node without children.
- *Height* The number of edges from root to furthest leaf.

## Traversing

Recursion is the most common way to traverse a tree with the depth first traversal. Depth first has multiple orders.

Queues are the typical way breadth first traversal is done. 

- *Depth First* prioritizing the height of the tree first
  - "Pre-order" root, left, right
  - "In-order" left, root, right
  - "Post-order" left, right, root
- *Breadth First* iterates each level of the tree node-by-node. En-queuing the root and then dequeuing the root. Each dequeue causes that node's children to be enqueued.


## Types

- *Binary Tree* limits child nodes to two per node.
- *K-ary Tree* child nodes up to k.
  - Breadth first can be accomplished with a queue in a similar way to binary trees.

## Efficiency

Inserting a node in the worst case is O(N) and the same for searching for a specific node. The space complexity for inserting (breadth first) will be O(w) where w is the largest width.

## Searches

A binary search tree is a more structured tree where the nodes are organized. Values smaller than the value at the root go on the left and larger values on the right. This organization makes searching a BST quick. The big o for inserting and search is O(h) where h is the height. A balanced tree is log(N) and a completely unbalanced tree it O(N). Space completely is O(1) since no extra space is needed for traversal.

# Reading Notes 05 -- Linked Lists 

## Big O: Analysis of Algorithm Efficiency

From [Code Fellows article](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/big_oh.html)

Big O is used to compare the time complexity and the additional space complexity of a given algorithm. Since the outcome can vary by data Big O refers to the worst case data -- like searching for something that is in the last possible place it could be.

- O(1) is a constant complexity growth, the complexity is not dependent on the input size.
- O(log N) is a binary logarithmic growth, as the algorithm runs the complexity is decreasing.
- O(N) is linear complexity growth and it is directly related to the size of the data.


## Linked Lists

Linked lists are a data structure comprised of elements in linear series referred to as nodes. Each node is an structure or object with properties that hold data and a link to the next node in the series. Doubly linked lists also hold a link to the previous node. In a linked list the terminal node always has a link that points to null. This null link makes it possible to check if you are at the end of the list. The first node in the list is referred to as the head and it needs to be saved in order to know where the beginning of the list starts.

Traversing forwards through a linked list can be preformed by defining a current node and setting it equal to the link to the next node until that next node equals null.

Inserting a node can be accomplished by first traversing to the node just before the insertion point. Setting a new node to also point to this node's link. Then finally by changing this node's link to point to the new node.

- Linked lists are great for adding and removing items quickly
- Linked lists are slow when it comes to searching for a node.
- Dynamic size and change length easily.
- Linked lists are not stored in contiguous memory like arrays, they can be scattered throughout the memory.

Sources:
- [Code Fellows article](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/singly_linked_list.html)
- [Medium article by Vaidehi Joshi Part I](https://medium.com/basecs/whats-a-linked-list-anyway-part-1-d8b7e6508b9d)
- [Medium article by Vaidehi Joshi Part II](https://medium.com/basecs/whats-a-linked-list-anyway-part-2-131d96f71996)



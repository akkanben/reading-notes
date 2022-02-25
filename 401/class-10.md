# Reading Notes 10 -- Stacks and Queues

From [Code Fellows Article](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/stacks_and_queues.html)

## Stacks

A stack is a linear data structure that uses first in last out (FILO) and last in first out (LIFO) structure. Values are added and removed from the "Top" of the stack.

Common methods:

- `push` Add a value to the stack.
- `pop` Return and remove a value from the stack.
- `peek` Return the value at the top of the stack but it remains in place.

Pushing, popping, and peeking values off the stack will be an O(1) time complexity operation because the top of the stack never requires traversal and is a linear operation.


## Queues

A queue is a linear data structure that follows the first in first out (FIFO) and last in last out (LILO) structure. Values enter the queue in the "Rear" and exit from the "Front".

Common methods:

- `enqueue` Add a value to the queue.
- `dequeue` Return and remove a value from the queue.
- `peek` Return the value at the front of the queue but it remains in place.

Just like a stack enqueuing , dequeuing, and peeking values out of the queue will be an O(1) time complexity operation because retrieving the front and the rear never requires traversal and is a linear operation.

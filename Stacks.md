# Stack

- Abstact Data Type
- Uses LIFO structure - Last In, First Out
  - push - Adds an item as the top item on the stack
  - pop - removes the top item on the stack,
  - peek - gets the top item on the stack without popping it.
- Ideal backing structure to implement a Stack is a Linked List.
- So inherits the problems associated with LinkedLists such as Random access.

Good way to envision a stack is a deck of cards, to get the 10th card you need to take 9 cards off the stack in order to get to it.

Stacks are commonly used in programming languages to implement call stacks (Java) or events (JavaScript)

## Time Complexity

- O(1) for push, pop and peek, when using a LinkedList
- If you use an array then push is O(n), because the array nay have been resized.
- If you know hte maximum number of items that will ever be on the stack, an array can be a good choice.
- If memory is tight an array may also be a good choice.
- But LinkedLists are ideal.

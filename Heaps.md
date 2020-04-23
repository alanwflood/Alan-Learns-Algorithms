# Heap

An abstract data type.

Also known as a priority queue.

It implements a set S of elements, each of elements associated with a key.

The idea is that based on a key being a priority, the structure is pushes the highest priority to the top of the queue/tree/array.

Takes the form of a complete binary tree. (Every level is filled but the last so the last node at that level could have 1 or less child nodes)

## Usage in the wild

Why Use Binary Heaps ?

For instant access (O(1) time) to the largest value in the case of a Max Heap or the smallest value in the case of a Min Heap. This just means that we know where the value will be which is in the root of the tree or at the start of the array, depending on which data structure you are using.

Useful for priority queues or schedulers, where the earliest item is desired. A practical application for this may be prioritizing patients at a hospital to work on with the highest priority.

## In detail

Heap can take one of these categories, most heaps fit in a Min or Max category:

**Heap:**
Parent and Children have no upper/lower bounds to compare one another, you've basically got an array of random values at this point, so you lose the advantage of a heap structure.

**Max Heap:**
Every Parent is greater than or equal to each of it's children

**Min Heap:**
Every Parent is less than or equal to each of it's children

**Heapify:** is the process of converting a binary tree into a heap by restructuring the order, this often has to be done after an insertion or deletion. Heapify runs in O(n log n) time. You essentially correct a single violation of the heap property in a subtrees root. (Look at Heapify)

There is also no required ordering between siblings.

To be usable with expect the following methods:

(s is always the structure itself in this context)

Insert(s, x): insert element "x" into set "s"
max(s): return element of "s" with the largest key
extractMax(s): return element of "s" with largest key and remove it from "s" the queue/heap
increment(S, x, k): increase the value of "x"s key to the new value "k"

## Implementing heaps

Heaps can be implemented using an array.

with a tree of stucture you simply go through each level left to right and add them to array table.

Parent(i): array[i] being the index of the node,
LeftChild(i): The formula to get the left child of a node becomes: `2i+1`
RightChild(i): The right child of a node becomes: `2i+2`
ParentOfChild(i): To get a child's parent is `floor((i - 1)/2)`

This implementation shows why we can only use complete binary trees, if the tree is balanced from left to left we'll have null values in the array.

## Heapify

First we compare the new insertion against it's parent,If it's greater (if it's a max heap, less than if a min heap) we swap it with it's parent, else do nothing. We then rinse and repeat until we get to the parent node and we can't swap anymore. Heapify can be done upper (elements above the chosen node), or below (below the chosen node). Heapify takes O(log n) time.

Looking at max heapify:

**Fix Heap Above**
Swap replacement value with parents value, then treat the child as a subtree and repeat until we hit a leaf. This method is always done after insertion.

**Fix heap below**
Swap the replacement value with the larger of its two children

## Insertion

Always add new items to the end of the heap, then we heapify. So insertion is O(log n) time.

## Deleting

Must choose a replacement value

Will take the rightmose value, so that the tree remains complete

Must then run heapify

When the replacement value is greater (less than in a min heap!) than parent, fix heap above, Otherwise fix heap below.

**Fix Heap Above**
Same as insert. Swap replacement value with parents value

**Fix heap below**
Swap the replacement value with the larger of its two children

Rinse and repeat in both cases until the replacement value is in it's correct position.

Will only need to fix upwards or downwards,not both.

## Building the heap

Taking an array and converting it to a heap due to a lot of mathsy stuff takes O(n). Based on implementation, we get it to this time as the mount of each item at each layer in the tree is linear to sort, and we can also exclude heapifying on node values.

To do it:

Heapify only the nodes (for loop over the indices (n/2) - 1 to get just the nodes), in reverse order.
Then you've a heap!

## Sorting - Heap Sort

O(n log n)

Go through each element then heapify the array;

As per the name Heap sort can only be done on a heap structure.

Essentially:

- We know the root has the la

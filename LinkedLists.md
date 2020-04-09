# LinkedLists

Java uses an boatload of classes that implement list interfaces.

Rather than implement your own LinkedList or list based interface, you should probably implement an already provided list implementing class.

## Abstract Data Types

Arrays are not Abstract, they are a concrete data type.

It:

* Doesn't dictate how the data is organized (Arrays for example do, they have to be stored sequentially and be the same data type)
* Dictates the operations you can perform.
* Concrete data structure is usually a concrete class
* Abstract data type is (usually) an interface

## When to use a Linked Lists

Stolen from StackOverflow:

Linked lists are preferable over arrays when:

    you need constant-time insertions/deletions from the list (such as in real-time computing where time predictability is absolutely critical)

    you don't know how many items will be in the list. With arrays, you may need to re-declare and copy memory if the array grows too big

    you don't need random access to any elements

    you want to be able to insert items in the middle of the list (such as a priority queue)

Arrays are preferable when:

    you need indexed/random access to elements

    you know the number of elements in the array ahead of time so that you can allocate the correct amount of memory for the array

    you need speed when iterating through all the elements in sequence. You can use pointer math on the array to access each element, whereas you need to lookup the node based on the pointer for each element in linked list, which may result in page faults which may result in performance hits.

    memory is a concern. Filled arrays take up less memory than linked lists. Each element in the array is just the data. Each linked list node requires the data as well as one (or more) pointers to the ither elements in the linked list.

Performance wise:

Algorithm           ArrayList   LinkedList
seek front            O(1)         O(1)
seek back             O(1)         O(1)
seek to index         O(1)         O(N)
insert at front       O(N)         O(1)
insert at back        O(1)         O(1)
insert after an item  O(N)         O(1)


## Singularly LinkedLists

A single linked list takes the shape of a series of nodes containing a value, and a pointer referencing the next value in the series.

A Linked List could be coded as:

```
class LinkedList {
    private LinkedListNode head
    private int size
}
```

And a Node:

```
class LinkedListNode {
    private T value // Generic value
    private T nextNode // Pointer to the next node
}
```

The final node of a Singular LinkedList is known as the Head of the list, we know it's the head as it's pointer value is null.

Accessing the head of a list is done in O(1) time or constant time, accesing any other member of the list will be O(n) time or linear time complexity.

## Double LinkedList

Similar to a LinkedList instead has a Head and Tail showing next and previous values.

Uses more space per list node than a single LinkedList but has the advantage of having constant time access to the start (Head) and the end (Tail) of the list.

```
class DoubleLinkedListNode {
    public T value // Generic value
    public T prevNode // Pointer to the previous node
    public T nextNode // Pointer to the next node
}
```

## Circular LinkedList

There is also a slight vartiation on the Double Linked List where the previous and next values are never null and just point back to the start or end of the list.

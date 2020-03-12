# Algorithms and Data Structures

## Whats the best data structure?

It depends on:

- What data you want to store
- How you want to store It
- How often you want to access it

## What is an algorithm?

A list of steps in order to do something.

An algorithm is not an implementation, an implementation is the actual code,
the algorithm is the psuedo code to build that implementation.

There can be many algorithms that accomplish the same task
There can be many implementations of the same algorithm.

# Arrays and Big-O Notation

## Big O-Notation

Used to describe time complexity of an algorithm

Most used notations:

Ordered in best to worst:

O(1) = Constant
O(logn) = Logarithmic
O(n) = Linear Time Complexity
O(nlogn) = n log-star n
O(n2) = Quadratic Time Complexity

And in English:

O(1) = As the number of items increase the number of steps stays the same
O(logn) = The number of steps increases but levels off at a point
O(n) = The number of items grows the levels of steps linearly
O(nlogn) = As the number of items grow it multiplies the steps required
O(n2) = As the number of items grow it squares the steps required (Amount of steps multipled by the amount of steps)

## Arrays

Contiguous Block in memory

Every element occupies the same amount of space in memory (References to those elements are whats stored in the array)

If an array starts at the mem address X, the size of each element in the array is Y, the i'th element can be found use the expression: x+i\*y

If the element index is known, the time to retrieve the element will be constant.

### To retrieve an element with an index (In plain english)

1. Multiply the size of the element by its index (Since each element has the same size in an array this is trivial)
2. get the start address of the array
3. Add the start address to the result of the multiplication

Ex (Mathematically):

`int[] myArray = [20, 35, -15, 7]`

Each block is an int so takes 4 bytes
The first mem address of myArray is 12

Mem address of myArray[0] = 12 + (0 \* 4) = 12
Mem address of myArray[1] = 12 + (1 \* 4) = 16
Mem address of myArray[2] = 12 + (2 \* 4) = 20
Mem address of myArray[3] = 12 + (3 \* 4) = 24

So to access any address is: myArray[i] = x + i \* y

---

So what does this mean?

No matter how big the array, it's always the same 3 steps to get data from the array.
So it's Constant time complexity is 0(1), it's steps never change.

### To retrieve without an Index

So in the real world we generally have no idea where in the array the data falls so it's index is unknown.

Search for the index (ie: Filtering results) becomes 0(n)

Because now it becomes:
) Get the address in memory
) Check if it's critera matches
) If it doesn't loop again

So each loop adds additional steps to the process

### To add to a full array

Because an array is a fixed size, to add data to it takes 0(n)

As a new space in memory must be created
) Get the address of the first element in memory
) Add that element to the new array in the same / offset position
) offset the previous address and repeat until all elements are added

Finally add the new elements at the desired position of the new array.

### To add to the end of an array with Space

This is 0(1)

### In summary

Basically for arrays:

If you know the address or it's at the end of the array before you perform an action it's 0(1)

If you need to search for the address before doing something it's 0(n)

Loop = 0(n)
No Loop = 0(1)

# Algorithms and Data Structures

## Whats the best data structure?

It depends on:

- What data you want to store
- How you want to store It
- How often you want to access item

## What is an algorithm?

A list of steps in order to do something.

An algorithm is not an implementation, an implementation is the actual code,
the algorithm is the psuedo code to build that implementation.

There can be many algorithms that accomplish the same task
There can be many implementations of the same algorithm.

## Abstract Data Type

Most types of structures will typically have in some form operations that make them an ADT (Abstract Data Type):

1. Insertion/Deletion
2. Min
3. Successor/Predecessor access per values

An ADT does not have to implement all of these but they are the key properties associated with an ADT.

Consider ADT's as blueprints and the Data Structure as the implementation of said blueprint.

So an ADT which contains insertion, deletion and min properties would be a priority queue, which can be implemented as a data strucutre using a heap, or an AVL tree.

## Models of Computation

There is many different models of computation, which states upperbounds of algorithms.

## Comparision Model:

- All input items are black boxes (ADTs),
- The only operations allowed are comparisons. (<, <=, >, >=, ==)

An implementation can move items around, but it only sorts by using comparison.

Examples are: Merge Sort, Quick Sort, Insertion Sort, BSTs, AVLs, heaps.

Time cost in this model is equal to the number of comparisons done.

## Descision tree

Any comparison algorithm can be viewed as a tree of all possible comparisons and their outcomes, and the resulting answer for any particular n values

### Using a binary tree as the algorithm/structre for searching

| Descision Tree | Algorithm |
|................|...........|
| Internal Node | Binary Descision (comparison) |
| Leaf | Found answer |
| root-to-leaf | algorithm exectution |
| path length | running time |
| height of tree | worse-case runtime |

#### searching lower bound:

- n preprocessed items
- finding a given item among them in comparison model requires ω(log n) in worst case

#### proof

we justify binary search trees are good for this because:

- descion tree is binary and must have >= n leaves, one for each answer
- height >= log n

### Now proving sorting in trees.

#### searching lower bound:

- decision tree is binary, number of leaves >= number of possible answers (n!)
- Height >= log(n!) -> log(n(n - 1)(n -2)....1) -> log n + log(n-1) + .... + log2 + log1

#### proof

we justify binary search trees are good for this because:

- descion tree is binary and must have >= n leaves, one for each answer
- height >= log n

## Linear Time Sorting

Makes the presumption that you're only sorting integers.

Asuume n keys sorting are intergers {0, 1.... k - 1}

Can do a lot more than comparisons.

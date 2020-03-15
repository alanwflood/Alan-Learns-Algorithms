# Sort Algorithms

Let's start learning how to sort arrays

## Bubble Sort

- It's an inplace algorithm
- O(n2) time complexity - quadratic
- It will take 100 steps to sort 10 items (10 \* 10)
- It will take 10000 steps to sort 100 items etc (100 \* 100)
- This algorithm degrades quickly as the number of items to sort grows
- Most Importantly: It's an awful algorithm that is rarely used to sort anything, it's mainly taught as an introduction to computer algorithms

To perform an optimized bubble sort:

create an index to show when the unsorted parition begins (initially this is the length of the array - 1)
) A Reverse Loop runs over the length of the array using the unsortedParitionIndex
)) Inside that loop run another loop over the length of the array against the unsortedParitionIndex
)) Check if array[i] is greater than array[i + 1]
)) If the are swap the values so array[i] takes [i+1]'s place and visa versa
)) Repeat the inner loop
) After the run the highest number should be at the end of the array, so repeat the loop getting each element to it's highest place, increasing the parition size each time

Usually a bubble sort doesn't even use a parition index it just loops over the full array, even after items have been sorted

## Stable vs Unstable sort algorithms

Lets take an example array with two of the same value, but differentiate them I'm going to add a tilde ~ to one of them, but they are the same value!

`int[] myArray = [4, 2, 7, 89, ~7, 23]`

If we sorted this array with an unstable sort algorithm, ~7 will come before the normal 7

In a stable sort ~7 comes after the normal 7

Stable sorts are preferred among other reasons:
if doing multiple sorts on the same data you obviosuly don't want other sorts to clash

## Selection Sort

Like bubble sort, splits the array into 2 partitions (sorted and unsorted)

So to implement:

You need 3 variables

- lastUnsortedIndex: to tell us the size of the unsorted array
- i = entry in the index being compared
- largest = the number of the index of largest entry in the array

The array is traversed and whichever is the largest value it's saved to the "largest" variable,
When value i is equal to lastUnsortedIndex,
the largest value is swapped with the lastUnsortedIndex value,
the lastUnsortedIndex is then reset and decremented by 1
and the loop goes again

And the facts:

- It's an inplace algorithm
- O(n2) time complexity - quadratic
- Doesn't require as much swapping as bubble sort
- Unstable

```
public static void selectionSort(int[] array) {
    // Go through the sorted values from right to left
    for (int lastUnsortedIndex = array.length - 1; lastUnsortedIndex > 0; lastUnsortedIndex--) {
        int largest = 0;
        // Go through the unsorted values left to right, to find the largest value
        for (int i = 0; i <= lastUnsortedIndex; i++) {
            if (array[i] > array[largest]) {
                largest = i;
            }
        }
        // Swap the largest value with the lastUnsortedIndex's value
        swap(array, largest, lastUnsortedIndex);
    }
}
```

## Insertion Sort

Unlike other sorts it grows the sorted partition from left to right.

To set this up we need 3 variables:

- firstUnsortedIndex: To show where the unsorted parition starts (Starts at 1)
- i: index to traverse the sorted array from right to left;
- newElement: the element we want to assign into the sorted array

So this time round we assign the first value on the array to the sorted partition.
From there the first value in the unsorted array is compared against the value in the sorted partition.
If it's greater than the sorted partition value it stays in place, otherwise, the value is assigned the value from the sorted partition, and we move on to the next item.
We loop adding and assigning each value to the correct position

The facts:
It's an inplace algorithm
O(n2) time complexity - quadratic
Stable Algorithm
It can lead to a helluva lot of shifting

```
public static void insertionSort(int[] array) {
    // Loop over the unsorted partition
    for (int unsortedIndex = 1; unsortedIndex < array.length; unsortedIndex++) {
        // Get the new element
        int newElement = array[unsortedIndex];
        // This is the index that newElement will eventually be assigned to
        int i;
        // Loop over the sorted partition from right to left, and compare values
        for (i = unsortedIndex; i > 0 && array[i - 1] > newElement; i--) {
            // Shifting values here
            array[i] = array[i - 1];
        }
        // Assign the new element
        array[i] = newElement;
    }
}
```

## Shell Sort

A Variation of insertion sort

While insertion sort chooses which element to insert using a gap of 1, shell sort starts with a larger gap, as the algorithm runs the gap is reduced.

Goal is to reduce the amount of shifting requred.

So a gap is set between numbers in the array and an insertion sort is done with that gap in mind so:

with array [1, 2, 3, 4, 5, 6, 7, 8]
and gap 3,
we compare the values 1 and 4 with one another,
then 4 and 7, then increment the starting point of the gap and loop again
after a full loop the size of the gap is changed.

Theres multiple scales to change the gap size per loop, the Knuth scale is one such commonly known scale

```
public static void shellSort(int[] array) {
    // Setup up the loop using the gap value to reduce it every loop
    for(int gap = array.length / 2; gap > 0; gap /= 2)
        // Loop over the array using the gap value
        for (int i = gap; i < array.length; i++) {
            // Assign the element to be sorted
            int newElement = array[i];
            // Assign a holder for the index to the traversing
            int j = i;

            // While the index is greater than or equal to the gap value
            // (If it's less we've hit the front of the array)
            // and the value in the array located at the index minus the gap
            // is greater than the element to be moved
            while ((j >= gap) && (array[j - gap] > newElement)) {
                // Shift the value at the current index
                // to that of the last iteration
                array[j] = array[j - gap];
                // Decrement the index by the gap amount so
                // we can compare the next element or break the loop
                j -= gap;
            }

            // Assign the value at j to the sorted element
            array[j] = newElement;
        }
}
```

Shell Sort is very similar to insertion sort apart from the gap, in the end shell sort actually becomes insertion sort for the last iteration when the gap hits 1. But shell sort has already optimized the array for the final run so their's less shifting.

## Recursion

> To understand recursion...
> One must first understand recursion

A method is a recursive method when it calls themselves.

To create a recursive method there has to be a break case unless you want it going forever. (Which is rarely the case)

An example of a recursive function would be to calculate a factorial (A number multipled by itself + 1 \* X amount of times) denoted as Number!

So 4 factorial:
4! = 4 _ 3 _ 2 \* 1

Comparing iterative to recursive functions:

```

    public static int iterativeFactorial(int num) {
        // Safety case
        if (num == 0) return 1;
        int factorial = 1;
        // Iterator
        for (int i = 1; i <= num; i++) factorial *= i;
        // Return (method is only called once)
        return factorial;
    }

    public static int recursiveFactorial(int num) {
        // Break case
        if (num == 0) return 1;
        // Recursion happens here
        return num * recursiveFactorial(num - 1);
    }
```

One thing to look out for in recursive functions is to not overload/blow the stack with recurrsive calls.
A compiler/runtime will assign a set amount of memory to perform calculations, exceeding this memory with recursive function calls can blow the stack.

Usually iterative methods run faster as there is less overhead when doing recursives calls due to memory assignment for each call.

Recursion however can make code simpler than performing multiple lines of iterations

Recursions limitations are also by the very size of the stack itself, say if a recusive method needed to called a trillion times, obviosuly the stack wouldn't be happy.
There is a way around this using Tail Recurrsion, but all the algorithms featured don't use tail recurrsion. (Some languages such as Java don't even support tail recursion)

## Merge Sort

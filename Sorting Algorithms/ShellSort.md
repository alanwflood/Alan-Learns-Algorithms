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


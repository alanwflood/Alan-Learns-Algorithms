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


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


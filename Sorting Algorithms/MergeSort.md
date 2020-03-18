## Merge Sort

A Divide and Conquer Algorithm

Recursive algorithm

Is NOT an in-place algorithm

0(nlogn) - n log-star n, We're repeatedly dividing the array in half during the splitting phase. It's logarithmic.

Is a stable algorithm

If memory is an issue, you'll need to look at another sort algorithm

### Two Phases: Splitting and Merging

We do the sorting in the merging phase,
the splitting is an optimization phse which leads to faster sorting during the merge.

Splitting is logical only!, we keep tabs of the split arrays by using indices not by creating new array instances!
Merging will use temporary arrays large enough to hold all the elements in the arrays we're merging.

Hold on to your butts:

### Splitting Phase 

So start with an unsorted array:

`array [5, -20, 45, 2, -32, 23, 75, 8]`

Divide the array into two arrays, which are unsorted,
the first is called the left, the second is called the right:

`array [left [5, -20, 45, 2], right [-32, 23, 75, 8]]`

Keep splitting the until all the arrays have only one element each
(An array of only one value is technically a sorted array!)

`array [left [[[5], [-20]], [[45], [2]], right [[-32], [23]], [[75], [8]]]]`

Now this leads to:

### Merging Phase

Start by merging every left right pair of sibling arrays into a sorted array,
For example we'll start with the left array, position 0 [5] and position 1 [-20]

`array [left [[[5], [-20]], [[45], [2]], right [[-32], [23]], [[75], [8]]]]`

We create a temporary 2 element array

`tempArray [null, null]`

i becomes 0 (index of the first value in the left array), j becomes 1 (index of the first value in the right array)

`int i = 0; int j = 1`

We compare array[i] to array [j], as -20 (j) is smaller than 5 (i) we copy it to the temp array.

`tempArray [-20, null]`

as the left value was smaller we increment index i by 1 then go again

We compare array[i (1)] to array [j (1)], as (i) is equal to (j) we copy the value to the temp array at that position.

`tempArray [-20, 5]`

this array is then copied back into their positon in the original array

`array [left [[-20, 5], [[45], [2]], right [[-32], [23]], [[75], [8]]]]`

We no longer have 4 arrays on the left side, we have 3, we repeat the above steps using the next array [[45], [2]] on the left side so we get

`array [left [[-20, 5], [2, 45]], right [[-32], [23]], [[75], [8]]]]`

As we're now down to 2 arrays we repeat the above again, creating an array of length 4,

`tempArray [null, null, null, null]`

set i to 0, j to 2, check i is smaller than j, copy,
copy value at i into the temp array as -20 (value at index i) is smaller than 2 (value at index j)
increment i as it's value was copied

`tempArray [-20, null, null, null]`

check i (1) is smaller than j (2), copy j into the temp array as 2 (value at index j) is smaller than 5 (value at index i)
increment j as it's value was copied

`tempArray [-20, 2, null, null]`

check i (1) is smaller than j (3), copy i into the temp array as 5 (value at index i) is smaller than 45 (value at index j)
increment i as it's value was copied

`tempArray [-20, 2, 5, null]`

as i is now 2 we know that the elements in the left array are now sorted, so we can copy the elements from the right array into place

Former: `array [left [[-20, 5], [2, 45]], right [[-32], [23]], [[75], [8]]]]`
Temp:   `tempArray [-20, 2, 5, 45]`

We then copy the temp array back into position
Former: `array [left [-20, 2, 5, 45], right [[-32], [23]], [[75], [8]]]]`

We do the same comparision dance to the right side and then for the left and right array.

Former: `array [left [-20, 2, 5, 45], right [[-32, 23], [8, 75]]]`

In the end we have the sorted array

### What the hell just happened

To Simplify further:

Splitting:

1. Get the start and end of the array
2. Get the midpoint (start + end) / 2
3. Elements 0 to midpoint -1 go into the left array
4. Elements midpoint to end go into the right array
5. Rerun until midpoint == start/end

Merge:

1. Create an temporary array
2. Set the index "i" to be the first index of left array
3. Set the index "j" to be the first index of right array
4. Compare left[i] to right[j]. If: 
    left is smaller: copy to the temp array and increment i by 1
    right is smaller: copy to the temp array and increment j by 1
5. Loop steps 2 - 4 until all elements in the two arrays are processed.
6. Copy the temporary array back to the original input array at the correct positions.
7. Loop 1 - 6 until you're left with a single array

### In Code

```
class MergeSort {
    // This method is just here to remove mutation
    public static int[] sort(int [] input) {
        splitPhase(input, 0, input.length);
        return input;
    }

    private static void splitPhase(int [] input, int start, int end) {
        // If we have a one element array, return the sorted array;
        if (end - start < 2) {
            return;
        }

        int midpoint = (start + end)  / 2;
        // Recursively split the left side of the array
        splitPhase(input, start, midpoint);
        // Recursively split the right side of the array
        splitPhase(input, midpoint, end);
        // Merge the two sides
        mergePhase(input, start, midpoint, end);
    }

    private static void mergePhase(int [] input, int start, int midpoint, int end) {
        // (Optimization:) If the last element in the left array is less than the first element in the right
        // The whole array is already sorted so just return and skip this merge phase
        if (input[midpoint - 1] <= input[midpoint]) {
            return;
        }

        // Else an element in the left array
        // is greater than an element in the right
        // Let's sort them
        int i = start;
        int j = midpoint;
        int tempIndex = 0;
        // Setup new temp array
        int arrayLength = end - start;
        int[] tempArray = new int[arrayLength];

        // If start is less than the midpoint, and the midpoint is less than the end,
        // keep comparing values adding them to the array and incrementing
        while (i < midpoint && j < end) {
            tempArray[tempIndex++] = input[i] <= input[j] ? input[i++] : input[j++];
        }

        // (Optimization) if the left array has been
        // fully moved (i greater than midpoint),
        // we know the right array is sorted,
        // so just copy it over without changing the value's positions.
        System.arraycopy(input, i, input, start + tempIndex, midpoint - i);

        // Copy the values filled in in the temp array
        System.arraycopy(tempArray, 0, input, start, tempIndex);
    }
}
```

A complex sort compared to the others, but because it's done recursively those included optimizations can save on additional calls each cycle



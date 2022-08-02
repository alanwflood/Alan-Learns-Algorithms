## Quick Sort

Another Divide and conquer algorithm

Recursive algorithm

On average:
0(nlogn) - n log-star n (Logarithmic), we're repeatedly paritioning the array into two halves
(it also performs faster than merge sort)

But worst case it can be O(n2) Quadratic

Unstable algorithm

Uses a pivot element to parition the array into two parts

Elements less than pivot, move to it's left
Elements greater than pivot, mote to it's right

Pivot will then be in it's correct sorted position (but the elements in there respective sub arrays may still not be sorted)

Process is now repeated for the left and right array.

Eventually every element has been the pivot so every element will be in its correct sorted position

Similar to merge sort we end paritioning the array into a series of 1-element arrays.

Does this in-place. No additional temp arrays needed (Unlike merge sort)

### So explain how it works:

With array:
`array [20, 35, -15, 7, 55, 1, -22]`

start = 0,
i = start
end = 7,
j = end
pivot = 20 (value at array[start (0)])

So:

Start with --j, and go from right to left, looking for the first element that's less than the pivot element

-22 is less than the pivot element so we assign it to position i, which is 0
j is 6

`array [-22, 35, -15, 7, 55, 1, -22]`

You might be like "What? What about the 20?", it's already saved to the pivot element so it's all good.

Now we go from left to right with i++, looking for the first element that's greater than the pivot.

35 is greater than the pivot, so we assign it to position j (6)
i is 1

`array [-22, 35, -15, 7, 55, 1, 35]`

One key thing to notice is we've not lost any data, because we know we've already moved whatever was at position 6.

By alternating between going from right to left and left to right, we can be sure we won't lose any values! We can't overwrite any positions we haven't handled!

Now after each cycle we check if i and j have crossed each other.

i is 1
j is 6
`if (j < i) return`

So Nope we loop again

Look at --j (5) which is 1, it is less than the pivot, so we move it position i (array[1 (1)])
j is 5

`array [-22, 1, -15, 7, 55, 1, 35]`

Back to left to right Look at i++, -15 is less than 20 so it's skipped, and i is incremented,
then 7 is less than 20 so it's also skipped and i is incremented.
Now we're at 55, which is greater so it goes to position j (5)
i is 4

`array [-22, 1, -15, 7, 55, 55, 35]`

Right to left time, but this time j cross the i boundry to get to position 3 (7)

So we assign the pivot (20) to position i (array[i(4)(55)])

`array [-22, 1, -15, 7, 20, 55, 35]`

We've now set the array in such a way that every value right of the pivot is greater and every value left of the pivot is less so the pivot is in the correct place,

We can not actually split the  array in 3:
    The unsorted left, the pivot and the unsorted right

`array [[-22, 1, -15, 7], 20, [55, 35]]`

We now need to rerun the above steps on the split arrays until the entire array is sorted.

### In Code

```
class QuickSort {
    public static int[] sort(int [] input) {
        return input;
    }

    private static void quickSort(int[] input, int start, int end) {
        // Dealing with one element array so return
        if (end - start < 2)  {
            return;
        }

        int pivotIndex = partition(input, start, end);
        // Get left subarray
        quickSort(input, start, pivotIndex);
        // Get right subarray
        quickSort(input, pivotIndex + 1, end);
    }

    private static int partition(int[] input, int start, int end) {
        // This is using the first element as the pivot
        int pivot = input[start];
        int i = start;
        int j = end;

        // Sort left and right of the pivot now

        // While i/j has not crossed each other
        while (i < j) {
            // Check elements right to left
            while (i < j && input[--j] >= pivot);
            if (i < j) {
                input[i] = input[j];
            }

            // Check elements left to right
            while (i < j && input[++i] <= pivot);
            if (i < j) {
                input[j] = input[i];
            }
        }
        // Insert the pivot
        input [j] = pivot;
        // Return the location of the pivot
        return j;
    }
}
```

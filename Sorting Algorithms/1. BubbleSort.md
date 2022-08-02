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

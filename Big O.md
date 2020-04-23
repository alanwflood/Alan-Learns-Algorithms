# Big O-Notation

Used to describe time complexity of an algorithm

## Most used notations:

Ordered in best to worst:

O(1), constant
O(logn), logarithmic
O(n), linear
O(nlogn), linearithmic
O(n2), quadratic
O(nk), polynomial time
O(2n), exponential
O(n!), factorial


And in English:

O(1) = As the number of items increase the number of steps stays the same
O(logn) = The number of steps increases but levels off at a point (The running time is a logarithm of the input size so it does not increase proportionally, but increases by some amount)
O(n) = The number of items grows the levels of steps linearly (The running time is proportional, as the number of inputs increase, the time also increases.)
O(nlogn) = As the number of items grow it multiplies the steps required (greater than proportionally)
O(n2) = As the number of items grow it squares the steps required (Amount of steps multipled by the amount of steps)

Remember: No matter how big the constant is and how slow the linear increase is, linear will at some point surpass constant time.

## Best Case, Worse Case and Expected Case

3 ways to describe a runtime for an algorithm

From the aspect of a Quick Sort (The sort with the pivot and splitting the array into pairs)

Best Case: If all elements are equal, quick sort will traverse the array only one O(n)
Worse Case: If the pivot is repeatedly the largest element in the array it won't divide the array in half, it'll just shrink the subarray by one element O(n2)
Expected Case: Generally the best case and worse case won't  be happening for the whole iteration so realistically O(n log n) will be the expected case.

## Space Complexity

So Big O also denotes space complexity.

O(1) means no additional space is created.
O(n) denotes creating a normal array.
O(n2) denotes creating a 2 dimensional array.

Stack space also counts so recurssive calls will be O(n) time, however simply calling functions to the stack non-recurssively doesn't count. Those would be O(1)

## Drop the Constants (Dust in the wind)

Big O only describes rate of increase, not the actual time taken. O(n) could run faster than O(1) for specific inputs, for those reasons constants are dropped at run time.

Code with 20 iterations could be considered O(20) compared to 20 iteations over two loops O(20*2)

The only way to measure accurately the performance would be to look at the actual machine code which is created from the code which is a helluva lot more complicated so we just drop the constants and say its O(n);

## When to add vs when to multiply
When would time be O(a + b) vs O(a * b)

* If your algorithm is in the form "do this, then when your done, do that", add the runtimes.
* If your algorithm is in the form "do this for each time you do that", multiply the runtimes.

## What is Log, and what is it representing.

The idea is that an algorithm is O(log n) if instead of scrolling through a structure 1 by 1, you divide the structure in half over and over again and do a constant number of operations for each split. Search algorithms where the answer space keeps getting split are O(log n). 

Example: binary search, where you keep splitting an ordered array in half over and over again until you find the number.

Note: You don't necessarily need to be splitting in even halves.

O (n log n) generally happens when you want to iterate on something, then do a divde and conquer approach afterwards. IE: Quicksort or a comparitve sort (Sorting a string for example)

## Exponants are king

So while we remove constants and log constants, exponents are definitely counted.

If a function was to recurssively call itself twice, we'd at 1 to the exponent for each iteration so it would become O(2n+1 - 1) or without constants O(2n);

The -1 comes from the initial call only being made once, as every other call is done twice.

So when dealing with recursion go by O(branches^depth), ie: with two branches O(2n)

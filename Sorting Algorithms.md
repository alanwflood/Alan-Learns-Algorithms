# Sort Algorithms

Let's start learning how to sort arrays

## Stable vs Unstable sort algorithms

Lets take an example array with two of the same value, but to differentiate them I'm going to add a tilde ~ to one of them, but they are still the same value only difference is their address in memory!

`int[] myArray = [4, 2, 7, 89, ~7, 23]`

If we sorted this array with an unstable sort algorithm, ~7 could come before the normal 7

In a stable sort ~7 always comes after the normal 7

Stable sorts are preferred among other reasons:
if doing multiple sorts on the same data you obviosuly don't want other sorts to clash

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


# Assumption based algorithms

So far all the previously explained algorithms:

* Don't make assumptions about the data (String, Ints, etc.)
* Don't assume that the data is bounded by any properties (IE: not negative, not a float)
* Are based around comparisons

ENTER ASSUMPTION BASED ALGORITHMS!


# Lab 15: Big O

Instead of writing code, in this lab we will find the big-O time complexity of various functions expressed in psuedocode. The functions are taken directly from Chapter 4 in the textbook:

* R-4.16
* R-4.17
* R-4.18
* R-4.19
* R-4.20

For each function, you should:

1. Determine the number of operations performed on each line and write your answer in the right-hand side of the pseudocode. You can assume a line of only "primitive" operations can be counted as a single operation.
2. Find the sum of all operations expressed as a function of _n_.
3. Write the big-O of the function.

## Linear Example

Here is an example:

    Algorithm linearPrefixAverages(A):
        Input: array X of n integers
        Output: array A of prefix averages of X
    A ← new array of n integers
    s ← 0
    for i ← 0 to n − 1 do
        s ← s + X[i]
        A[i] ← s / (i + 1)
    return A

For part 1 you would modify the code as follows. For completeness we include the implicit increment of the `for` loop.

    Algorithm linearPrefixAverages(X, n):
        Input: array X of n integers
        Output: array A of prefix averages of X
    A ← new array of n integers                        n
    s ← 0                                              1
    for i ← 0 to n − 1 do                              n
        s ← s + X[i]                                   1
        A[i] ← s / (i + 1)                             1
        { increment i}                                 1
    return A                                           1

For part 2, sum the operations. Note that the number of iterations of a loop is multiplied across all operations of the loop's body.

    f(n) = n + 1 + n (1 + 1 + 1) + 1
         = 4n + 2

For part 3, find the big-O of f(n):

    O(4n + 2) = O(n)

## Quadratic Example

Here is another example:

    Algorithm quadraticPrefixAverages(X, n):
        Input: array X of n integers
        Output: array A of prefix averages of X
    A ← new array of n integers
    for i ← 0 to n − 1 do
        s ← X[0]
        for j ← 1 to i do
            s ← s + X[i]
        A[i] ← s / (i + 1)
    return A

For part 1 you would modify the code as follows. For completeness we include the implicit increment of the `for` loop.

    Algorithm quadraticPrefixAverages(X, n):
        Input: array X of n integers
        Output: array A of prefix averages of X
    A ← new array of n integers                      n
    for i ← 0 to n − 1 do                            n
        s ← X[0]                                     1
        for j ← 1 to i do                            i
            s ← s + X[i]                             1
            { increment i }                          1
        A[i] ← s / (i + 1)                           1
        { increment i }                              1
    return A                                         1

For part 2, sum the operations. Note that the number of iterations of a loop is multiplied across all operations of the loop's body.

    f(n) = n + n (1 + i (1 + 1) + 1 + 1) + 1
         = n + n (2i + 3) + 1
         = n + 2ni + 3n + 1
         = n + 2 (n(n + 1)/2) + 3n + 1
         = n + n(n + 1) + 3n + 1
         = n + n^2 + n + 3n + 1
         = n^2 + 5n + 1

For part 3, find the big-O of f(n):

O(n^2 + 5n + 1) = O(n^2)

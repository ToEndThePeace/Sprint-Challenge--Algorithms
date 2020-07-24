# Please add your answers to the ***Analysis of  Algorithms*** exercises here

## Exercise I

1. This code block will run linearly, or O(n). The block runs until `a < n^3` . In this problem, since `a` is incremented _linearly_ by `n^2` , the code only needs to run `n` times for `a` to reach `n^3` . Effectively, the while loop condition can be _reduced_ by the increment in a, so that `n * n * n` ( `n^3` ) is reduced by `n * n` down to just `n` .

2. This code block is simpler than it seems at first glance and will run in a nice O(n log n). In the problem we have an initial loop `for i in n` that will contribute a runtime complexity of O(n). Now the inner while loop is what contributes the O(log n). For every run of the for loop, the value of `j` is initialized at `2^0` and loops up to `2^(log n) = n` . When this expression is simplified we get `log n = log n` .

3. Since the function is recursive and our base case is `bunnies == 0` , we can deduce that its runtime complexity is directly correlated to the operations we perform on `bunnies` when we pass it down recursively. Since the value of `bunnies` is decreased _linearly_ on each recursive call ( `bunnies - 1` ), this function clocks in at a simple O(n).

## Exercise II

I propose a solution to this problem using a specialized binary search implementation. Since the order of the building's floors are, as a general rule, sorted from low to high, even though we don't know the value we're searching for, we know that we're looking for a floor `f` that fits the following criteria: `egg_breaks_on(f) and not egg_breaks_on(f - 1)` . The following is pseudocode for my proposed implementation with a runtime complexity of O(log n), assuming the `egg_breaks_on()` function is given and returns a _boolean_:

``` python
def find_floor(n):
    left = 0
    right = n
    while left <= right:
        f = n // 2
        if egg_breaks_on(f):
            if not egg_breaks_on(f - 1):  # we've found our solution
                return f
            else:  # f is LOWER
                right = f - 1
        else:  # egg didn't break
            if egg_breaks_on (f + 1):  # we found a solution
                return f + 1
            else:  # f must be higher
                left = f + 1
```

# Fibonacci

### Brute force

```python
def fib_brute_force(n) -> int:
    """
    Time complexity: O(2^N)
        It's a recursive function, with a branching factor of 2. 
        This means, until arriving to N it performs two calls.        

    Space complexity: O(N)
        In recursive functions, we need to have into account the stack space 
        needed for every call. In this case, it will grow depending on N.        
    """

    if n <= 2:
        return 1
    else:
        return fib(n-1) + fib(n-2)
```

### Memoization

```python
def fib_dynamic(n, index = None) -> int:
    """
    Time complexity: O(N)
        With this approach, we won't make a recursive call if we already passed
        by that value. So, worst case scenario we will go over N iterations.

    Space complexity: O(N)
        For the same reasons, the stack space will depend on N.
    """

    if index is None:
        index = {}

    if n in index.keys():
        return index[n]
    if n <= 2:
        return 1
    else:
        index[n] = fib(n-1, index) + fib(n-2, index)
        return index[n]
```

### Tabulation

```python
def fib_dynamic_tab(n: int) -> int:
    """
    Time complexity: O(N)
        It only interates the array once

    Space complexity: O(N)
        It only requires an array of size N + 1
    """

    table = [0] * (n + 1)
    table[1] = 1

    for i in range(len(table)):
        if (i + 1) < len(table):
            table[i + 1] += table[i]

        if (i + 2) < len(table):
            table[i + 2] += table[i]

    
    return table[-1]
```


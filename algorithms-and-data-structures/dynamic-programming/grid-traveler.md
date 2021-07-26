# Grid Traveler

### Brute force

```python
def grid_traveler_brute_force(m: int, n: int) -> int:
    """
    Time complexity: O(2^(N+M))
        For each recursive call, we will make two calls (one for each type 
        of movement we are allowed to do). And, if we explore the height 
        of the recursive tree it will depend both in M and N. 
        Since we only can move towards one direction at every step, 
        the max height will depend on M+N.
    
    Space complexity: O(N+M)
        Since the max height is N+M, the max size of the stack will be 
        limited by it.
    """

    if m == 1 and n == 1:
        return 1
    elif m == 0 or n == 0:
        return 0
    
    return grid_traveler(m - 1, n) + grid_traveler(m, n - 1)
```

### Memoization

```python
def grid_traveler_dynamic(m: int, n: int, index: dict = {}) -> int:
    """
    Time complexity: O(N*M)
        M can take values { 0..M } and N can take values { 0..N }. 
        Hence there are N*M possible combination to be explored.

    Space complexity: O(N+M)
        The max height is N+M, hence the max size of the stack will be 
        limited by it.
    """

    if index is None:
        index = {}

    if (m,n) in index.keys():
        return index[(m,n)]
    if m == 1 and n == 1:
        return 1
    elif m == 0 or n == 0:
        return 0

    index[(m,n)] = (
        grid_traveler_dynamic(m - 1, n, index) + 
        grid_traveler_dynamic(m, n - 1, index)
    )

    index[(n,m)] = index[(m,n)]

    return index[(m,n)]
```

### Tubulation

#### From down-right to top-left

```python
def grid_traveler_tab(m: int, n: int) -> int:
    """
    Time complexity: O(N*M)
    
    Space complexity: O(N*M)

    6 3 1
    3 2 1
    1 1 1
    """

    table = [[0 for j in range(n)] for i in range(m)]
    table[-1][-1] = 1

    for i in range(m-1, -1, -1):  # right -> left
        for j in range(n-1, -1, -1):  # down -> up
            if (i + 1) < m:
                table[i][j] += table[i+1][j]
            if (j + 1) < n:
                table[i][j] += table[i][j+1]

    
    return table[0][0]
```

#### From top-left to down-right

```python
def grid_traveler_tab(m: int, n: int):
    """
    Time complexity: O(N*M)
    
    Space complexity: O(N*M)
    """

    table = [[0 for j in range(n+1)] for i in range(m+1)]
    table[1][1] = 1
    # print(table)

    for i in range(m+1):  # left -> right
        for j in range(n+1):  # up -> down
            if i+1 <= m:
                table[i+1][j] += table[i][j]
            if j+1 <= n:
                table[i][j+1] += table[i][j]
    
    return table[-1][-1]
```


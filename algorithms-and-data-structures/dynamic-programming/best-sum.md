# Best Sum

###  Brute force

```python
def best_sum_brute(target_sum: int, numbers: list[int]):
    """
    Time complexity: O(N^M * M)
        Time complexity will depend on two factors: 
          - how big is value of target_sum (M)
          - and the number of items in numbers (N).
        In the algorigthm, we explore all the available solutions 
        by iterating the available "numbers" to decrease 
        the value of the target.
        Then, the branching factor will be N and, 
        in the worst scenario, wewill explore these M options 
        up to M times.

        Additionally, for every iteration we copy all the 
        elements of the solution and we add an element.
        This list of elements will be bounded by M given 
        its lenght could be M in the worst case.

    Space complexity: O(M*M) = O(M²)
        The height of the recursion tree will depend on 
        target value. Thus, it will depend on M.
        Also, we are keeping every potencial best 
        solution in every recursion level, with a max length of M.
    """

    if target_sum == 0:
        return []
    if target_sum < 0:
        return None

    best_solution = None

    for number in numbers:
        diff = target_sum - number

        result = best_sum_brute(diff, numbers)
        if result is not None:
            solution = [*result, number]

            if (
                best_solution is None 
                or len(solution) < len(best_solution)
            ):
                best_solution = solution
            
    
    return best_solution
```

### Memoization

```python
def best_sum_memo(
    target_sum: int, 
    numbers: list[int], 
    index: dict = None
) -> list[int]:
    """
    Time complexity: O(N*M*M) = O(N*M²)
        Worst case scenario, it will need to check every 
        combination of every value of N 
        while decreasing M (worst scenario will be by 1).
        Additionally, for every iteration we copy all the 
        elements of the solution and we add an element.
        This list of elements will be bounded by M given 
        its lenght could be M in the worst case.

    Space complexity: O(M*M) = O(M²)
        The height of the recursion tree will depend on 
        target value. Thus, it will depend on M.
        Also, we are keeping every potencial best solution 
        in every recursion level, with a max length of M.
    """

    if index is None:
        index = {}

    if target_sum in index.keys():
        return index[target_sum]

    if target_sum == 0:
        return []
    if target_sum < 0:
        return None

    best_solution = None

    for number in numbers:
        diff = target_sum - number

        result = best_sum_memo(diff, numbers, index)
        if result is not None:
            solution = [*result, number]

            if (
                best_solution is None 
                or len(solution) < len(best_solution)
            ):
                best_solution = solution

    index[target_sum] = best_solution
    return index[target_sum]
```

### Tabulation

```python
def best_sum_tab(
    target_sum: int, 
    numbers: list[int]
) -> list[int]:
    """
    Time complexity: O(N*M*M)

    Space complexity: O(M²)
    """

    table = [None] * (target_sum + 1)
    table[0] = []
    
    for i in range(target_sum + 1):

        if table[i] is not None:
            for number in numbers:

                index = i + number
                if (
                    index <= target_sum
                    and (
                        table[index] is None 
                        or len(table[i]) + 1 <= len(table[index])
                    )
                ):

                    table[index] = [*table[i], number]
    
    return table[-1]
```


# Can Sum

### Brute force

```python
def can_sum_brute(target: int, numbers: list[int]) -> bool:
    """
    Time complexity: O(N^M)
        Time complexity will depend on two factors: 
          - how big is value of target (M)
          - and the number of items in numbers (N).
        In the algorigthm, we explore all the available solutions by iterating 
        the available "numbers" to decrease the value of the target.
        Then, the branching factor will be N and, in the worst scenario, 
        we will explore these M options up to M times.

    Space complexity: O(M)
        The height of the recursion tree will depend on target value. 
        Thus, it will depend on M.
    """

    if target == 0:
        return True
    if target < 0:
        return False

    for number in numbers:
        current = target - number        
        result = can_sum_brute(current, numbers)
        if result:
            return result

    return False
```

### Memoization

```python
from typing import Optional

def can_sum_memo(
    target: int, 
    numbers: list[int], 
    index: Optional[dict] = None
) -> bool:
    """
    Time complexity: O(N*M)
        Worst case scenario, it will need to check every combination of 
        every value of N  while decreasing M (worst scenario will be by 1).

    Space complexity: O(M)
        The height of the recursion tree will depend on target value. 
        Thus, it will depend on M.
    """

    if index is None:
        index = {}

    if target in memo.keys():
        return index[target]

    if target == 0:
        return True
    if target < 0:
        return False

    for number in numbers:
        current = target - number
        result = can_sum_memo(current, numbers, memo)
        if result:
            index[target] = result
            return index[target]

    index[target] = False
    return False
```

### Tabulation

```python
def can_sum_tab(target_sum: int, numbers: list[int]) -> bool:
    """
    Time complexity: O(N*M)

    Space complexity: O(M)
    """

    table = [False] * (target_sum + 1)
    table[0] = True

    for i in range(target_sum + 1):
        for number in numbers:
            index = i + number
            if index <= target_sum:
                table[index] = (
                    table[index] if table[index] else table[i]
                )
    
    return table[-1]
```


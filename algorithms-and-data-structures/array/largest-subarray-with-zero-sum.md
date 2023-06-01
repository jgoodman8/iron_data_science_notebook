# Largest subarray with zero sum

Given an array arr\[] of length **N**, find the length of the longest sub-array with a sum equal to 0.

**Examples:**

> **Input:** arr\[] = {15, -2, 2, -8, 1, 7, 10, 23}\
> **Output:** 5\
> **Explanation:** The longest sub-array with elements summing up-to 0 is {-2, 2, -8, 1, 7}
>
> **Input:** arr\[] = {1, 2, 3}\
> **Output:** 0\
> **Explanation:** There is no subarray with 0 sum

```python
def zero_sum(a: List[int]) -> int:
    """
    Space complexity: O(1)
    Computational complexity: O(N³) -> two nested loops + sum operator
    """
    
    solution = 0
    for i in range(len(a)):        
        for j in range(i+1, len(a)):
            partial_sum = sum(a[i:j])
            
            if partial_sum == 0 and (j - i) > solution:
                solution = j - i
                
    return solution
```

```python
def zero_sum(a: List[int]) -> int:
    """
    Space complexity: O(1)
    Computational complexity: O(N²)
    """
    
    solution = 0
    for i in range(len(a)):
        partial_sum = a[i]
        
        for j in range(i+1, len(a)):
            partial_sum += a[j]
            
            if partial_sum == 0 and (j - i) > solution:
                solution = j - i
                
    return solution
        
```

```python
def zero_sum(a):
    """
    Space complexity: O(N)
    Computational complexity: O(N)
    """
    
    max_length = 0
    sub_arr_sum = 0

    hash_map = {}  # index of the last position of the sum
    # key = sum

    for i in range(len(a)):
        sub_arr_sum += a[i]

        if a[i] == 0 and max_length == 0:
            max_length = 1

        if sub_arr_sum == 0:
            max_length = i + 1

        if sub_arr_sum in hash_map:
            # when you see a repeated sum, you can assume the 
            # delta between both positions sums zero.
            max_length = max(max_length, i - hash_map[sub_arr_sum])
        else:
            hash_map[sub_arr_sum] = i

    return max_length
```

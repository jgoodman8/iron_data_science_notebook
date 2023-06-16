# Climbing Stairs

{% embed url="https://leetcode.com/problems/climbing-stairs/" %}

**Brute force:**

```python
def climb_stairs(n):
    """
    time: O(2^n)
    space: O(n)
    """
    if n <=2:
        return n

    return  climb_stairs_2(n-1) + climb_stairs_2(n-2)
```

**Tabulation:**

```python
def climb_stairs(n):
    """
    time: O(n)
    complexity: O(n)
    """
    if n <=2:
        return n

    s = [0] * (n+1)
    s[1] = 1
    s[2] = 2
    for i in range(3, n + 1):
        s[i] = s[i-2] + s[i-1]
    
    return s[n]
```

**Tabulation with better memory usage:**

```python
def climb_stairs(n):
    """
    time: O(n)
    complexity: O(1)
    """
    if n <=2:
        return n

    s1 = 1
    s2 = 2
    for i in range(3, n + 1):
        s = s2 + s1
        s1 = s2
        s2 = s
    
    return s2
```

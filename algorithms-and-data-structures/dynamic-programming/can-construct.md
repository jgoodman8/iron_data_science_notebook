# Can Construct

###  Brute force

```python
def can_construct_brute(
    target: str, 
    word_bank: list[str]
) -> bool:
    """
    N = len(work_bank)
    M = len(target)

    Time complexity: O(N^M * M)
        We are removing words for the target in every iteration. 
        In the worst scenario, we will remove then up to M times. 
        And, we have N branches to explore at every iteration.
        As well, in every iteration we copy and remove 
        some characters the target (depending on M).

    Space complexity: O(M*M) = O(M²)
        It will make up to M recursive calls. And for every call, 
        it will store the suffix 
        of the target.
    """

    if target == "":
        return True

    for word in word_bank:
        if word in target and target.index(word) == 0:
            diff = target.removeprefix(word)
            if can_construct(diff, word_bank):
                return True

    return False
```

### Memoization

```python
def can_construct_memo(
    target: str, 
    word_bank: list[str], 
    index: dict = None
) -> bool:
    """
    N = len(work_bank)
    M = len(target)

    Time complexity: O(N*M²)
        Worst case scenario, it will need to check every 
        combination of every value of N while decreasing M 
        (worst scenario will be by 1 character every time).
        As well, in every iteration we copy and remove some 
        characters the target (depending on M).

    Space complexity: O(M*M) = O(M²)
        It will make up to M recursive calls. And for every call, 
        it will store the suffix of the target.
    """

    if index is None:
        index = {}
    
    if target in index.keys():
        return index[target]

    if target == "":
        return True

    for word in word_bank:
        if word in target and target.index(word) == 0:
            diff = target.removeprefix(word)
            if can_construct_memo(diff, word_bank, index):
                index[target] = True
                return True

    index[target] = False
    return False
```

### Tabulation

```python
def can_construct_tab(target: str, word_bank: list[str]) -> bool:
    """
    Time complexity: O(M*N*M)
    Space complexity: O(M)
    """

    table = [False] * (len(target) + 1)
    table[0] = True

    for i in range(len(table)):
        if table[i] == True:
            for word in word_bank:
                substring = target[i:]
                if (
                    word in substring 
                    and substring.index(word) == 0
                ):
                    table[i + len(word)] = True

    return table[-1]
```


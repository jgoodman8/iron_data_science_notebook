# Count Construct

###  Brute force

```python
def count_construct_brute(
    target: str, 
    word_bank: list[str]
) -> int:
    """
    N = length of word_bank
    M = length of target

    Time complexity: O(N^M * M)
        Worst case scenario, it will need to check every 
        combination of every value of N while decreasing M 
        (worst scenario will be by 1 character every time).
        As well, in every iteration we copy and remove some 
        characters the target (depending on M).

    Spacial complexity: O(M*M)
        It will make up to M recursive calls. And for every call, 
        it will store the suffix of the target.
    """


    if target == '':
        return 1
    
    counter = 0
    for word in word_bank:
        if word in target and target.index(word) == 0:
            suffix = target.removeprefix(word)

            counter += count_construct_brute(suffix, word_bank)

    return counter
```

### Memoization

```python
def count_construct_memo(
    target: str, 
    word_bank: list[str], 
    index: dict = None
) -> int:
    """
    N = length of word_bank
    M = length of target

    Time complexity: O(N*M * M)
        Worst case scenario, it will need to check every 
        combination of every value of N while decreasing M 
        (worst scenario will be by 1 character every time).
        As well, in every iteration we copy and remove some 
        characters the target (depending on M).

    Spacial complexity: O(M*M)
        It will make up to M recursive calls. And for every call, 
        it will store the suffix of the target.
    """
    if index is None:
        index = {}

    if target in index.keys():
        return index[target]

    if target == '':
        return 1
    
    counter = 0
    for word in word_bank:
        if word in target and target.index(word) == 0:
            suffix = target.removeprefix(word)

            counter += count_construct_memo(
                         suffix, 
                         word_bank, 
                         index
                       )

    index[target] = counter
    return counter
```

### Tabulation

```python
def count_construct_table(
    target: str, 
    word_bank: list[str]
) -> int:
    """
    Time complexity: O(M*N*M)
    Space complexity: O(M)
    """

    table = [0] * (len(target) + 1)
    table[0] = 1

    for i in range(len(table)):
        if table[i] > 0:
            for word in word_bank:
                substring = target[i:]
                if (
                    word in substring 
                    and substring.index(word) == 0
                ):
                    table[i + len(word)] += table[i]

    return table[-1]
```


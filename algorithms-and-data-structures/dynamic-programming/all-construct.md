# All Construct

###  Brute force

```python
def all_construct_brute(
    target: str, 
    word_bank: list[str]
) -> list[list[str]]:
    """
    N = length of word_bank
    M = length of target

    Time complexity: O(N^M * M*M)
        Worst case scenario, it will need to check every 
        combination of every value of N while decreasing M 
        (worst scenario will be by 1 character every time).
        As well, in every iteration we copy and remove some 
        characters the target (depending on M).

    Spacial complexity: O(M*M*M)
        It will make up to M recursive calls. And for every call, 
        it will store the suffix of the target.
    """


    if target == '':
        return [[]]
    
    all_solutions = []

    for word in word_bank:
        if word in target and target.index(word) == 0:
            suffix = target.removeprefix(word)

            previous_solutions = all_construct_brute(
                                    suffix, 
                                    word_bank
                                )

            current_solutions = list(map(
                                        lambda way: [word, *way], 
                                        previous_solutions
                                ))
            
            all_solutions = [*all_solutions, *current_solutions]

    return all_solutions
```

### Memoization

```python
def all_construct_memo(
    target: str, 
    word_bank: list[str], 
    index: dict = None
) -> list[list[str]]:
    """
    N = length of word_bank
    M = length of target

    Time complexity: O(N*M * M*M)
        Worst case scenario, it will need to check every ç
        combination of every value of N while decreasing M 
        (worst scenario will be by 1 character every time).
        As well, in every iteration we copy and remove 
        some characters the target (depending on M).

    Spacial complexity: O(M*M*M)
        It will make up to M recursive calls. And for every call, 
        it will store the suffix of the target.
    """
    if index is None:
        index = {}

    if target in index.keys():
        return index[target]

    if target == '':
        return [[]]
    
    all_solutions = []

    for word in word_bank:
        if word in target and target.index(word) == 0:
            suffix = target.removeprefix(word)

            previous_solutions = all_construct_memo(
                                    suffix, 
                                    word_bank, 
                                    index
                                 )

            current_solutions = list(map(
                                    lambda way: [word, *way], 
                                    previous_solutions
                                ))
            
            all_solutions = [*all_solutions, *current_solutions]

    index[target] = all_solutions
    return index[target]
```

### Tabulation

```python
def all_construct_table(
    target: str, 
    word_bank: list[str]
) -> int:
    """
    Time complexity: ~O(N^M)
    Space complexity: ~O(N^M)
    """

    table = [[]] * (len(target) + 1)
    table[0] = [[]]

    for i in range(len(table)):
        if len(table[i]) > 0:
            for word in word_bank:
                substring = target[i:]
                if (
                    word in substring 
                    and substring.index(word) == 0
                ):
                    new_solutions = list(
                        map(lambda sub_array: [*sub_array, word], 
                            table[i]))
                    table[i + len(word)] = [
                        *new_solutions,
                        *table[i + len(word)]
                    ]

    return table[-1]
```


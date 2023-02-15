# Rank word combination

```python
"""
Consider a "word" as any sequence of capital letters A-Z (not limited to just "dictionary words").
For any word with at least two different letters, there are other words composed of the same letters but in a different order
(for instance, STATIONARILY/ANTIROYALIST/AAIILNORSTTY).

We can then assign a number to every word, based on where it falls in an alphabetically sorted list of all words made up of the same group of letters.

Given a word, return its number.
Your function should be able to accept any word 25 letters or less in length (possibly with some letters repeated).

Sample words, with their rank:
ABAB = 2
AAAB = 1
BAAA = 4

"""

from itertools import permutations


def list_position(word: str):
    """
    time complexity: O(!n)
    """
    word_perms = set(["".join(perm) for perm in permutations(list(word))])

    word_perms = list(sorted(word_perms))

    return word_perms.index(word) + 1

# 1. Findout which unique characters we have (sorted)
# 2. Iterate our string
# 3. In each iteration, fix current char and compute perm
# return result

# BCA  

(3 - 0 - 1)! = 2 -> 2 * (1 ) = 2

(2 - 1)

def list_position(word: str):

    sorted_word = sorted(word)

    hashmap = {c: i for i, c in enumerate(sorted_word)}

    position = 0
    for i, char in enumerate(word):
        index_in_sorted = hashmap[char]

        position += math.factorial((len(word) - i - 1)) * index_in_sorted
        hashmap.pop(char)

        # position += math.factorial((len(word) - i - 1)) * index_in_sorted
        # hashmap.pop(char)

    return position

def list_position(word):
    """
    Given a word
    1. Get total num of permutations
    2. take the first letter
        2i. How many permutations have happened before this?
    3. Take the second letter.
        i. How many permutations before this?
    4. ...
    """
    count = 0
    while len(word):
        # get unique letters and num permutations
        char_set = set(word)

        # get number of permutations and deal with duplicates
        num_permutations = factorial(len(word))
        for ch in char_set:
            num_permutations /= factorial(word.count(ch))

        # start with the first letter
        # iterate through the set of unique chars
        # if the first letter comes after the char, we add on the num permutation that have passed
        first_ch = word[0]
        for ch in char_set:
            if ch < first_ch:
                count += num_permutations / len(word) * word.count(ch)

        word = word[1:]

    return count + 1


# testing code
words_and_solutions = {
    "ABC": 1,  # 
    "BCA": 4,  # ABC, ACB, BAC all before
    "CBA": 6,  # ABC, ACB, BAC, BCA, CAB
    "AAAB": 1,
    "ABAB": 2,  # AABB, ABAB, ABBA, BAAB, BABA, BBAA
    "BAAA": 4,
    "QUESTION": 24572,
    "BOOKKEEPER": 10743
    }
for word, solution in words_and_solutions.items():
    output = list_position(word=word)
    if output != solution:
        print(f"ERROR: {word} ({output}!={solution})")
    else:
        print(f"Correct: {word} ({output}=={solution})")
```

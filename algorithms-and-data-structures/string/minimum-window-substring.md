# Minimum Window Substring

[https://leetcode.com/problems/minimum-window-substring](https://leetcode.com/problems/minimum-window-substring)

* Time: O(M+N) -> once over "t" and once over "s"
* Space: O(M) -> based on the size of a hashmap with letters of "t" as keys

```python
from collections import defaultdict

class Solution:

    def minWindow(self, s: str, t: str) -> str:    
        if t == "":
            return ""

        result = None
        target_index = defaultdict(int)
        window = defaultdict(int)

        # M = len(t) => O(M)
        for char in t:
            target_index[char] += 1

        current, missing = 0, len(target_index)

        start = 0

        # N = len(s) => O(N)
        for end in range(len(s)):
            char = s[end]
            window[char] += 1

            # When all repetitions of a char are in the window
            if char in target_index and window[char] == target_index[char]:
                current += 1

            while current == missing:
                if result is None or (end - start + 1) < len(result):
                    result = s[start:end+1]

                window[s[start]] -= 1
                if s[start] in target_index and window[s[start]] < target_index[s[start]]:
                    current -= 1

                start += 1

        return result if result is not None else ""
```

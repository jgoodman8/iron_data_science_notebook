# Longest Repeating Character Replacement

[https://leetcode.com/problems/longest-repeating-character-replacement/](https://leetcode.com/problems/longest-repeating-character-replacement/)

**Solution in O(N)**

```python
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:        
        index = defaultdict(int)
        start = 0
        end = 0
        
        res = 0
        cur_max = 0
        
        for end in range(len(s)):
            index[s[end]] += 1
            cur_max = max(cur_max, index[s[end]])
            
            while (end - start + 1) - cur_max > k:
                index[s[start]] -= 1
                start += 1
            
            res = max(res, end - start + 1)
                        
        return res
```

**Solution for replacing multiple characters**

```python
class Solution:
    # O(N) time
    # O(1) space

    def characterReplacement(self, s: str, k: int) -> int:
        index = defaultdict(int)
        sub_str = ""
        max_sum = 0
        
        for char in s:
            
            if self.can_add_char(char, index, k):
                sub_str += char
                index[char] += 1
                max_sum = max(max_sum, len(sub_str))
            
            else:
                if char in sub_str:
                    new_start = sub_str.index(char)
                    sub_str = sub_str[new_start+1:]
                else:
                    sub_str = ""
                sub_str += char
                
                index = defaultdict(
                        int, 
                        {
                            val: sub_str.count(val) for val in set(sub_str)
                        }
                    )
        
        return max_sum
    
    
    def can_add_char(self, char: str, index: Dict, k: int) -> bool:
        
        if len(index) == 0:
            return True
        
        elif len(index) == 1:
            return char in index.keys() if k == 0 else True
        
        elif len(index) == 2 and char not in index.keys():
            return False
        
        else:
            min_key, min_val = min(index.items(), key=lambda val: val[1])
            return False if min_key == char and min_val == k else True
```

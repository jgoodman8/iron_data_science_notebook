# Longest Substring Without Repeating Characters

[https://leetcode.com/problems/longest-substring-without-repeating-characters/](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        return self.lengthOfLongestSubstringN(s)
    
    def lengthOfLongestSubstringN(self, s: str) -> int:
        max_len = 0
        chars = ""
        
        for char in s:
            if char not in chars:
                chars += char            
                max_len = max(max_len, len(chars))
            else:
                index = chars.index(char)
                chars = chars[index+1:]
                chars += char

        return max_len
    
    def lengthOfLongestSubstringArrayN(self, s: str) -> int:
        max_len = 0
        chars = []
        
        for char in s:
            if char not in chars:
                chars.append(char)
                
                if len(chars) > max_len:
                    max_len = len(chars)                
            else:
                index = chars.index(char)
                chars = chars[index+1:]
                chars.append(char)

        return max_len
            
        
    def lengthOfLongestSubstringNLogN(self, s: str) -> int:
        if len(s) == 0:
            return 0
        
        max_size = 1
        head = 0
        tail = 0
        sol = s[0]
        
        while head + 1 < len(s):
            if s[head+1] not in sol:
                head += 1
                sol = s[tail:head+1]
                
                if max_size < len(sol):
                    max_size = len(sol)
                                
            elif tail < head:
                tail += 1
                sol = s[tail:head+1]
                
            else:
                head += 1
                tail += 1
                
        return max_size

```

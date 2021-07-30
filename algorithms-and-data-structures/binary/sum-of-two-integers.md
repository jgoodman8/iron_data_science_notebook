# Sum of Two Integers

[https://leetcode.com/problems/sum-of-two-integers](https://leetcode.com/problems/sum-of-two-integers/submissions/)

{% hint style="warning" %}
Not working with negative values. 

TODO: Check how to deal with negative binary operations in Python
{% endhint %}

```text
class Solution:
    def getSum(self, a: int, b: int) -> int:
        
        while b != 0:            
            carry = a&b
            a = a^b            
            b = carry<<1
            print(b)
            
        return a
```




# Two Sum

{% hint style="info" %}
[https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)
{% endhint %}

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        return self.twoSumOpti(nums, target)

    def twoSumBruteForce(self, nums: List[int], target: int) -> List[int]:
        """
        Iterate through all the numbers and check if there is a number which 
        is equal to the difference of (target - num)
        
        Time complexity: O(N^3)
            The main loop takes O(N) time. Then, on every iteration we check 
            if the difference is within the rest of the array. 
            And, if so, we get the index for that item.
        
        Space complexity: O(1)
            Any variable is stored and there aren't any recursive call.
        """
        
        for i, num in enumerate(nums):
            difference = target - num
            
            if difference in nums[i+1:]:
                complementary_index = nums[i+1:].index(difference) + i+1
                return [i, complementary_index]
    
    def twoSumBruteForceIterating(self, nums: List[int], target: int) -> List[int]:
        """
        Iterate through all the numbers and check if there is a number which 
        is equal to the difference of (target - num)
        
        Time complexity: O(N^2)
            The main loop takes O(N) time. Then, on every iteration we look 
            for the diff in the remaining array.
        
        Space complexity: O(1)
            Any variable is stored and there aren't any recursive call.
        """
        
        for i in range(len(nums)):
            for j in range(i+1, len(nums)):
                if nums[i] + nums[j] == target:
                    return [i, j]
    
    def twoSumLookup(self, nums: List[int], target: int) -> List[int]:
        """
        Store all the indexes for every number until you find a complementary 
        already stored in the lookup.
        
        Time complexity: O(N)
            Iterating only once over the array.
        Space complexity: O(N)
            Worst case scenary, we store all the items of the array 
            in the hashmap.
        """
        
        lookup = {}
        
        for i, num in enumerate(nums):
            difference = target - num
            
            if difference in lookup:
                return [i, lookup[difference]]
            
            lookup[num] = i
        
        return []

```


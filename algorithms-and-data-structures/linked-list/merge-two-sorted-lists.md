# Merge Two Sorted Lists

[https://leetcode.com/problems/merge-two-sorted-lists/](https://leetcode.com/problems/merge-two-sorted-lists/)

[https://www.geeksforgeeks.org/merge-two-sorted-linked-lists/](https://www.geeksforgeeks.org/merge-two-sorted-linked-lists/)

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(
        self, 
        l1: Optional[ListNode], 
        l2: Optional[ListNode]
    ) -> Optional[ListNode]:
        return self.mergeTwoListsRecursive(l1, l2)
        
    def mergeTwoListsRecursive(
        self, 
        l1: Optional[ListNode], 
        l2: Optional[ListNode]
    ) -> Optional[ListNode]:
        """
        Time: O(N)
        Space: O(1) from variables + O(N) from stack calls => O(N)
        """
        
        merged = None
        curr = None
        
        if l1 is None:
            return l2
        elif l2 is None:
            return l1
        elif l1.val <= l2.val:
            curr = l1
            merged = self.mergeTwoListsRecursive(l1.next, l2)
        else:
            curr = l2
            merged = self.mergeTwoListsRecursive(l1, l2.next)
            
        curr.next = merged
        
        return curr
        
        
    def mergeTwoListsIterate(
        self, 
        l1: Optional[ListNode], 
        l2: Optional[ListNode]
    ) -> Optional[ListNode]:
        """
        Time: O(N)
        Space: O(1)
        """
        
        head = curr = ListNode(-float("inf"))
        
        while l1 or l2:
            if l2 is None:
                curr.next = l1
                l1 = l1.next
            elif l1 is None:
                curr.next = l2
                l2 = l2.next
                            
            elif l1.val <= l2.val:
                curr.next = l1
                l1 = l1.next
            else:
                curr.next = l2
                l2 = l2.next          
            
            curr = curr.next
            
        return head.next
```


# Reverse Linked List

[https://leetcode.com/problems/reverse-linked-list](https://leetcode.com/problems/reverse-linked-list)

[https://www.geeksforgeeks.org/reverse-a-linked-list/](https://www.geeksforgeeks.org/reverse-a-linked-list/)

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        return self.reverseListStack(head)
    
    def reverseListStack(self, head: Optional[ListNode]) -> Optional[ListNode]:
        """
        Time: O(N) + O(N) = O(N)
        Space: O(N)
        """
        
        if head is None:
            return head
        
        stack = []
        current = head
        while current != None:
            stack.append(current)
            current = current.next        
        
        head = current = stack.pop()  # set the top of the stack as the head
        while len(stack) > 0:  # iterate until stack is empty
            current.next = stack.pop()  # point next to top of the stack
            current = current.next  # move to next
        
        current.next = None
        return head
    
    def reverseListRecursiveWithFlags(
        self, 
        head: Optional[ListNode]
    ) -> Optional[ListNode]:
        """
        Time: O(N)
        Space: O(1) variables + O(N) stack calls = O(N)
        """
        
        if head is None:
            return None

        return self.util_reverseListRecursiveWithFlags(curr=head, prev=None)
    
    def util_reverseListRecursiveWithFlags(
        self, 
        curr: Optional[ListNode], 
        prev: Optional[ListNode]
    ) -> Optional[ListNode]:
        
        if curr.next is None:  # if end of recursion
            curr.next = prev  # set prev as next node of the last node
            
            return curr
        
        next_ = curr.next  # temporal store of next node
        curr.next = prev  # point next node to previous
        
        return self.util_reverseListRecursiveWithFlags(next_, curr)
    
    def reverseListRecursive(
        self, 
        head: Optional[ListNode]
    ) -> Optional[ListNode]:
        """
        Time: O(N)
        Space: O(1) variables + O(N) stack calls = O(N)
        """
        
        if head is None or head.next is None:
            return head

        rest = self.reverseListRecursive(head.next)
        
        head.next.next = head
        head.next = None    
        
        return rest
        
    def reverseListIterate(self, head: Optional[ListNode]) -> Optional[ListNode]:
        """
        Time: O(N)
        Space: O(1)
        """
        
        previous = None # set the previous as NULL
        current = head  # set the initial head as the current one
        while current != None:
            next_ = current.next  # save next node
            current.next = previous  # point to prev node or None (in 1st iter)
            previous = current  # move one position the previous flag
            current = next_  # set the saved next as the current
        
        return previous
```


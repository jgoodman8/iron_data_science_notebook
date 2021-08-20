# Detect cycle

[https://leetcode.com/problems/linked-list-cycle/](https://leetcode.com/problems/linked-list-cycle/)

[https://www.geeksforgeeks.org/detect-loop-in-a-linked-list/](https://www.geeksforgeeks.org/detect-loop-in-a-linked-list/)

```python
class Solution:
    def hasCycle(self, head: ListNode) -> bool:
        return self.hasCycleEditingNodes(head)
    
    def hasCycleWithSet(self, head: ListNode) -> bool:
        """
        Time: O(N) -> iterates all the list
        Space: O(N) -> needs to store all the list in the set
        """
        
        nodes = set()
        
        while head is not None:
            if head in nodes:
                return True
                
            nodes.add(head)
            head = head.next
            
        return False
            
    def hasCycleEditingNodes(self, head: ListNode) -> bool:
        """
        Time: O(N) -> iterates all the list
        Space: O(1) -> flags are added inplace
        """
        
        while head is not None:
            if hasattr(head, 'visited') and head.visited:
                return True            
            
            head.visited = True
            head = head.next
            
        return False
        
    def hasCycleFloyd(self, head: ListNode) -> bool:
        """
        Time: O(N) -> iterates all the list
        Space: O(1) -> no extra space required (just two pointers)
        """
        
        slow = fast = head
        
        while slow and fast and fast.next:            
            
            slow = slow.next            
            fast = fast.next.next
            
            if slow == fast:
                return True
            
        return False
```


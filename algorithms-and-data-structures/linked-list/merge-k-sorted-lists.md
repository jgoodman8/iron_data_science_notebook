# Merge k Sorted Lists

[https://leetcode.com/problems/merge-k-sorted-lists](https://leetcode.com/problems/merge-k-sorted-lists)

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    """
    k = num of lists
    N = total number of nodes
    """
    
    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        return self.mergeKListsDivideAnConquer(lists)

    def mergeKListsDivideAnConquer(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        """
        Time: O(N*log_2(k)) -> iterates the N nodes log_2(k) times
        Space: O(N) -> N stack calls
        """
        
        filtered_list = list(filter(lambda item: item is not None, lists))
        
        if len(filtered_list) == 0:
            return None
        
        return self.helper_mergeKListsDivideAnConquer(filtered_list)
    
    def helper_mergeKListsDivideAnConquer(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        if len(lists) == 1:
            return lists[0]
        
        if len(lists) % 2 != 0:
            middle = int(len(lists) / 2)
            return self.mergeTwoListsRecursive(
                l1=self.mergeTwoListsRecursive(
                    l1=self.helper_mergeKListsDivideAnConquer(lists[:middle]), 
                    l2=self.helper_mergeKListsDivideAnConquer(lists[middle+1:])
                ),
                l2=lists[middle]
            )
        
        middle = int(len(lists) / 2)
        print(middle)

        return self.mergeTwoListsRecursive(
            l1=self.helper_mergeKListsDivideAnConquer(lists[:middle]), 
            l2=self.helper_mergeKListsDivideAnConquer(lists[middle:])
        )

    
    def mergeKListsTwoByTwo(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        """
        Time: O(N*k) -> iterates the N nodes for the k lists
        Space: O(N) -> N stack calls
        """
        
        if len(lists) == 0:
            return None
        
        ordered = ListNode(-float("inf"))
        for l in lists:
            if l is not None:
                ordered = self.mergeTwoListsRecursive(l, ordered)
            
        return ordered.next
            
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
    
    def mergeKListsCompareOneByOne(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        """
        Time: O(N*k) -> find the smallest node for the k list until all N nodes are visited
        Space: O(1) from variables + O(N) from stack calls => O(N)
        """
        
        
        node, index = self.findMinNode(lists)
        if node is None:
            return None
        
        merged = self.mergeKListsRecursive(lists[:index] + [node.next] +  lists[index+1:])
        
        node.next = merged
        
        return node
    
    def findMinNode(self, lists: List[Optional[ListNode]]) -> Tuple[ListNode, int]:
        values = list(map(lambda node: node.val if node else None, lists))
        not_none_values = list(filter(lambda item: item is not None, values))
        
        if len(not_none_values) == 0:
            return None, -1
        
        min_value = min(not_none_values)
        min_index = values.index(min_value)
        
        return lists[min_index], min_index
```


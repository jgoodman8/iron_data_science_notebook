# Same Tree

 [https://leetcode.com/problems/same-tree/](https://leetcode.com/problems/same-tree/)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
        return self.isSameRecursiveEqual(p, q)
        
    def isSameTreeDoubleIteration(self, p: TreeNode, q: TreeNode) -> bool:
        """
        Time complexity: O(N) since each node is visited exactly once.

        Space complexity: O(log(N)) in the best case of completely balanced 
        tree and O(N) in the worst case of completely unbalanced tree, 
        to keep a deque.
        """
        
        left_values = []
        right_values = []
        
        self._extract_node_values_from_tree(p, left_values)    
        self._extract_node_values_from_tree(q, right_values)
        
        return left_values == right_values    
    
    def _extract_node_values_from_tree(self, node: TreeNode, values):        
        if node is None: 
            values.append(None)
            return
        
        values.append(node.val)
        self._extract_node_values_from_tree(node.left, values)
        self._extract_node_values_from_tree(node.right, values)                
        
    def isSameRecursiveEqual(self, p: TreeNode, q: TreeNode) -> bool:
        """
        Time complexity: O(N), where N is a number of nodes in the tree, 
        since one visits each node exactly once.

        Space complexity: O(log(N)) in the best case of completely balanced 
        tree and O(N) in the worst case of completely unbalanced tree, 
        to keep a recursion stack.
        """
        
        if p is None and q is None:
            return True
        elif p is None or q is None:
            return False
        
        return (
            p.val == q.val 
            and self.isSameRecursiveEqual(p.left, q.left) 
            and self.isSameRecursiveEqual(p.right, q.right)
        )
    
        
    

```


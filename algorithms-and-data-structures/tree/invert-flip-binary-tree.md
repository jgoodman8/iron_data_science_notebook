# Invert/Flip Binary Tree

 [https://leetcode.com/problems/invert-binary-tree/](https://leetcode.com/problems/invert-binary-tree/)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    
    def invertTree(self, root: TreeNode) -> TreeNode:
        return self.invertTreeIterative(root)
    
    def invertTreeRecursive(self, root: TreeNode) -> TreeNode:
        """
        Since each node in the tree is visited only once, the time complexity 
        is O(n), where n is the number of nodes in the tree. 
        We cannot do better than that, since at the very least we have to 
        visit each node to invert it.
        
        Because of recursion, O(h) function calls will be placed on the stack 
        in the worst case, where h is the height of the tree. 
        Because h ∈ O(n), the space complexity is O(n).
        """
        
        if root is None:
            return root
        
        right = self.invertTree(root.left)
        left = self.invertTree(root.right)
        
        root.left = right
        root.right = left
        
        return root
    
    def invertTreeIterative(self, root: TreeNode) -> TreeNode:
        """
        Since each node in the tree is visited/added to the queue only once, 
        the time complexity is O(n), where nn is the number of nodes in the tree.

        Space complexity is O(n), since in the worst case, the queue will 
        contain all nodes in one level of the binary tree. 
        For a full binary tree, the leaf level has ceil(n/2) = O(n) leaves.
        """        
        
        if root is None:
            return None
        
        queue = [root]        
        while len(queue) != 0:
            current = queue.pop(0)
            
            temp_node = current.left
            current.left = current.right
            current.right = temp_node
            
            if current.left is not None:
                queue.append(current.left)
            
            if current.right is not None:
                queue.append(current.right)

        return root
```


# Maximum Depth of Binary Tree

[https://leetcode.com/problems/maximum-depth-of-binary-tree/](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        return self.maxDepthBFT(root)        
        
    def maxDepthDFT(self, root: TreeNode) -> int:
        """
        Depth First Traversals - Preorder Traversal
        
        Time complexity: O(N)
        Space complexity: O(N)
        """
            
        if root is None:
            return 0
        elif root.left is None and root.right is None:
            return 1        
        elif root.right is None:
            return self.maxDepth(root.left) + 1
        elif root.left is None:
            return self.maxDepth(root.right) + 1
        
        return max(self.maxDepthDFT(root.left), self.maxDepthDFT(root.right)) + 1
            
        
    def maxDepthBFT(self, root: TreeNode) -> int:
        """
        Depth First Traversals - Preorder Traversal
        
        Time complexity: O(N)
        Space complexity: O(N)
        """
        
        
        if root is None:
            return 0
        
        height = 0
        queue = [root]
        
        while len(queue) != 0:
            height += 1
            level_nodes = [*queue]
            queue = []        
            
            for level_node in level_nodes:
                if level_node.left is not None:
                    queue.append(level_node.left)
                if level_node.right is not None:
                    queue.append(level_node.right)
                    
        return height
```


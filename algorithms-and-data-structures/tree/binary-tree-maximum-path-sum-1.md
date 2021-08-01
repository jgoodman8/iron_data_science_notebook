# Binary Tree Maximum Path Sum

[https://leetcode.com/problems/binary-tree-maximum-path-sum/](https://leetcode.com/problems/binary-tree-maximum-path-sum/)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    
    def maxPathSum(self, root: TreeNode) -> int:
        return self.maxPathSumIterative(root)        
    
    def maxPathSumSimpleLogic(self, root: TreeNode) -> int:
        """
        Time Complexity: O(N)
        Space Complexity: O(N)
        """        
        
        self.current_max = float("-inf")                
        
        res = self._compute_dfs_max(root)
        
        return self.current_max
    
    
    def _compute_dfs_max(self, root: TreeNode) -> int:
        if root is None:
            return 0
        
        left_max = self._compute_dfs_max(root.left)
        right_max = self._compute_dfs_max(root.right)
        
        self.current_max = max(self.current_max, left_max + right_max + root.val)
        
        return max(0, root.val + max(left_max, right_max))
        
        
    def maxPathSumBruteForce(self, root: TreeNode) -> int:
        """
        Overcomplicated solution: it stores all the possible paths
        
        Time Complexity: ~O(N^N)
            For each iteration, it iterates all the stored paths and it stores 
            a new copy of the paths when adding the new paths.
        
        Space Complexity: ~O(N²)
            It has to stor an N*N array with all the allowed paths.
        """
    
        if root is None:
            return None
        
        paths = []
        
        queue = [root]
        while len(queue) != 0:
            
            current = queue.pop(0)
            paths.append([current])
            
            if current.left is not None:
                queue.append(current.left)
                new_paths = []
                for path in paths:
                    if path[0] == current:
                        new_paths.append([current.left, *path])
                    elif path[-1] == current:
                        new_paths.append([*path, current.left])
                        
                paths = [*paths, *new_paths]
            
            if current.right is not None:
                queue.append(current.right)
                
                new_paths = []
                for path in paths:
                    if path[0] == current:
                        new_paths.append([current.right, *path])
                    elif path[-1] == current:
                        new_paths.append([*path, current.right])
                
                paths = [*paths, *new_paths]

        return max(
            list(
                map(lambda path: sum(map(lambda node: node.val, path)), 
                paths)
            )
        )
```


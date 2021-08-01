# Binary Tree Paths

[https://leetcode.com/problems/binary-tree-paths](https://leetcode.com/problems/binary-tree-paths)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    
    def binaryTreePaths(self, root: TreeNode) -> List[str]:
        return self.binaryTreePathsRecursiveStr(root)
        
    def binaryTreePathsRecursiveStr(self, root: TreeNode) -> List[str]:
        """
        Time complexity: O(N²)
            The tree nodes are iterated, it means complexity has order N. Then,
            for every iteration the array is iterated to add 
            the current node value.
        
        Space complexity: O(N)
            Stack calls for N calls
        """
        
        if root is None:
            return []
        
        if root.left is None and root.right is None:
            return [str(root.val)]        
        
        left_solutions = self.binaryTreePathsRecursiveStr(root.left)        
        right_solutions = self.binaryTreePathsRecursiveStr(root.right)                
        
        solutions = left_solutions +  right_solutions
        
        return list(map(lambda solution: f"{root.val}->{solution}", solutions))
        
    def binaryTreePathsRecursive(self, root: TreeNode) -> List[str]:
        
        solutions = self._get_recursive_solutions(root)
        
        return list(map(lambda solution: "->".join(map(str, solution)), solutions))
            
        
    def _get_recursive_solutions(self, root: TreeNode) -> List[List[int]]:
        if root is None:
            return []
        
        if root.left is None and root.right is None:
            return [[root.val]]
        
        left_solutions = self._get_recursive_solutions(root.left)            
        left_solutions = list(
            map(lambda solution: [root.val, *solution], left_solutions)
        )
        
        right_solutions = self._get_recursive_solutions(root.right)
        right_solutions = list(
            map(lambda solution: [root.val, *solution], right_solutions)
        )        
        
        return [*left_solutions, *right_solutions]
```


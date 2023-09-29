# Set Matrix Zeroes

[https://leetcode.com/problems/set-matrix-zeroes/](https://leetcode.com/problems/set-matrix-zeroes/)

```python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        self.setZerosOpti(matrix)
        
    def setZerosAdditionalMemory(self, matrix: List[List[int]]) -> None:
        """
        Time Complexity: O(M×N) where M and N are the number of rows 
        and columns respectively

        Space Complexity: O(M+N)
            One array to store zeros in the horizontal axis and another one
            to store the ones from the vertical array.
        """        
        
        horizontal_zeros = []
        vertical_zeros = []
        
        for i, row in enumerate(matrix):
            for j, value in enumerate(row):
                if value == 0:                    
                    horizontal_zeros.append(i)
                    vertical_zeros.append(j)

        
        for i, row in enumerate(matrix):
            for j, value in enumerate(row):
                if i in horizontal_zeros or j in vertical_zeros:
                    matrix[i][j] = 0

        
    def setZerosAdditionalTime(self, matrix: List[List[int]]) -> None:
        """
        Time Complexity: O(M²×N²)
        
        Space Complexity: O(1)
        """
        
        for i, row in enumerate(matrix):
            for j, value in enumerate(row):
                if value == 0:                    
                    print(f"{i}, {j}")
                    # set zeros in row
                    for k, item in enumerate(row):
                        matrix[i][k] = "*" if matrix[i][k] != 0 else 0
                    
                    # set zeros in column
                    for r in matrix:
                        r[j] = "*" if r[j] != 0 else 0
                        
        for i, row in enumerate(matrix):
            for j, value in enumerate(row):
                if value == "*":
                    matrix[i][j] = 0
                    
    def setZerosOpti(self, matrix: List[List[int]]) -> None:    
        """
        Time Complexity: O(M×N)
        
        Space Complexity: O(1)
        """
        
        first_col = False
        num_rows = len(matrix)
        num_cols = len(matrix[0])
        for i in range(num_rows):
            # Since first cell for both first row and first column is the same 
            # i.e. matrix[0][0]
            # We can use an additional variable for either the first row/column.
            # For this solution we are using an additional variable for the first             
            # column and using matrix[0][0] for the first row.
            if matrix[i][0] == 0:
                first_col = True
            for j in range(1, num_cols):
                # If an element is zero, we set the first element of the 
                # corresponding row and column to 0
                if matrix[i][j]  == 0:
                    matrix[0][j] = 0
                    matrix[i][0] = 0
        
        # Iterate over the array once again and using the first row 
        # and first column, update the elements.
        for i in range(num_rows-1 , -1, -1):
            for j in range(num_cols-1, 0, -1):
                if not matrix[i][0] or not matrix[0][j]:
                    matrix[i][j] = 0
            if first_col:
                matrix[i][0] = 0
```

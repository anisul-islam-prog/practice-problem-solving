# Problem Statement
You are given a matrix of integers where every row and column are sorted in ascending order. Your task is to find the row that contains a specific `target` value. If the `target` value doesn't exist, return `None`.

The expected time complexity is _**`O(n+m)`**_, where `n` is the number of rows and `m` is the number of columns.

# Solution
```python
def find_row_with_target(matrix: list[list[int]], target: int) -> int | None:
    rows = len(matrix)
    if rows == 0:
        return None
    cols = len(matrix[0])
    if cols == 0:
        return None

    i = 0
    j = cols - 1

    while i < rows and j >= 0:
        if matrix[i][j] == target:
            return i
        elif matrix[i][j] > target:
            j -= 1
        else:
            i += 1

    return None
    
    pass
```

# Tests
```python
import unittest
from typing import List, Union
from solution import find_row_with_target


class TestSolution(unittest.TestCase):
    def test1(self):
        self.assertEqual(find_row_with_target([
            [1, 4, 7, 11],
            [2, 5, 8, 12],
            [3, 6, 9, 16]
        ], 9), 2)
        
    def test2(self):
        self.assertEqual(find_row_with_target([
            [-5, -3, 0, 3],
            [-2, 2, 7, 10]
        ], -5), 0)
        
    def test3(self):
        self.assertEqual(find_row_with_target([
            [1, 2, 3],
            [4, 5, 6],
            [7, 8, 9]
        ], 5), 1)
        
    def test4(self):
        self.assertEqual(find_row_with_target([[100]], 100), 0)

    def test5(self):
        self.assertEqual(find_row_with_target([
            [1],
            [2],
            [3],
            [4],
            [5]
        ], 3), 2)
        
    def test6(self):
        self.assertIsNone(find_row_with_target([
            [1, 2, 3, 4, 5]
        ], 10))
        
    def test7(self):
        self.assertEqual(find_row_with_target([
            [-1000, -500],
            [-300, 10],
            [20, 1000]
        ], -300), 1)
        
    def test8(self):
        self.assertEqual(find_row_with_target([
            [1, 1, 1, 1],
            [2, 2, 2, 2],
            [3, 3, 3, 3]
        ], 2), 1)

    def test9(self):
        self.assertIsNone(find_row_with_target([
            [1, 4, 7, 11],
            [14, 15, 16, 20],
            [22, 23, 24, 30]
        ], 25))
        
    def test10(self):
        self.assertIsNone(find_row_with_target([
            [10, 20, 30],
            [40, 50, 60],
            [70, 80, 90]
        ], 35))
        
    def test11(self):
        self.assertIsNone(find_row_with_target([
            [-10, -5, 0, 5],
            [10, 15, 20, 25]
        ], 6))

if __name__ == '__main__':
    unittest.main()
```
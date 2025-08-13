# Problem Statement
You are given a square matrix of `n x n` size. Your task is to write a Python function that indicates whether the matrix is a **Toeplitz matrix**

In a **Toeplitz matrix**, each descending diagonal (from left to right) is constant. That is, elements in each descending diagonal are the exact same.

For example, if the given matrix is:
```Plain text
6 7 8
4 6 7
1 4 6
```
Your function should return **True** because all diagonals that run from the top-left to the bottom-right (↘ direction) are constant:

`[1], [4, 4], [6, 6, 6], [7, 7], [8]`
(Each of these diagonals goes from upper-left towards lower-right.)

# Solution
```python
from typing import List


def is_toeplitz(matrix: List[List[int]]) -> bool:
   n = len(matrix[0])
   for col in range(n - 1):
      for row in range(n - 1):
         if matrix[row][col] != matrix[row + 1][col + 1]:
            return False
   return True
   pass
```

# Tests
```python
import unittest
from solution import is_toeplitz

class TestIsToeplitz(unittest.TestCase):

    def test_case_1(self):
        matrix = [[6, 7, 8], [4, 6, 7], [1, 4, 6]]
        self.assertEqual(is_toeplitz(matrix), True)

    def test_case_2(self):
        matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
        self.assertEqual(is_toeplitz(matrix), False)

    def test_case_3(self):
        matrix = [[1, 7], [5, 1]]
        self.assertEqual(is_toeplitz(matrix), True)

    def test_case_4(self):
        matrix = [[9]]
        self.assertEqual(is_toeplitz(matrix), True)

    def test_case_5(self):
        matrix = [[1, 5, 9], [6, 1, 5], [11, 6, 1]]
        self.assertEqual(is_toeplitz(matrix), True)

    def test_case_6(self):
        matrix = [[1, 2, 1], [0, 1, 2], [3, 0, 1]]
        self.assertEqual(is_toeplitz(matrix), True)

    def test_case_7(self):
        matrix = [[-4, -9, -4], [-3, -4, -9], [-2, -3, -4]]
        self.assertEqual(is_toeplitz(matrix), True)

    def test_case_8(self):
        matrix = [[1, 2, 1], [2, 1, 2], [3, 2, 1]]
        self.assertEqual(is_toeplitz(matrix), True)
    
    def test_case_9(self):
        matrix = [[3, 3, 3], [3, 1, 3], [3, 3, 3]]
        self.assertEqual(is_toeplitz(matrix), False)
    
    def test_case_10(self):
        matrix = [[4, 4, 4, 4], [1, 4, 4, 4], [4, 1, 4, 4], [4, 4, 0, 4]]
        self.assertEqual(is_toeplitz(matrix), False)
    
    def test_case_11(self):
        matrix = [[5, 5], [5, 4]]
        self.assertEqual(is_toeplitz(matrix), False)
    
    def test_case_12(self):
        matrix = [[10, 9], [8, 10]]
        self.assertEqual(is_toeplitz(matrix), True)
    
    def test_case_13(self):
        matrix = [[7, 7, 7], [7, 7, 0], [7, 0, 7]]
        self.assertEqual(is_toeplitz(matrix), False)


if __name__ == '__main__':
    unittest.main()
```
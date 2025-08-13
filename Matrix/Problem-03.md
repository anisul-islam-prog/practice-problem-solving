# Problem Statement
Given a square matrix `grid` of integers, your task is to find the minimum and maximum values at the secondary diagonal. The secondary diagonal starts at the top right corner and ends at the bottom left corner.

Return a list of two elements where the first element is the minimum value, and the second is the maximum value that you have found in the diagonal. If the square matrix is empty, return `[None, None]`.

The time complexity of the solution should not exceed _**O(n)**_, where `n` is the length of the row (or column) in the grid.

# Solution
```python
def solution(grid):
    n = len(grid)
    if n == 0:
        return [None, None]
    # the top-right value as min and max value
    min_val = max_val = grid[0][n - 1]

    for row in range(1, n):
        col = n - 1 - row
        val = grid[row][col]
        min_val = min(min_val, val)
        max_val = max(max_val, val)

    return [min_val, max_val]
    pass

```

# Tests
```python
import unittest
from solution import solution

class TestsSolution(unittest.TestCase):

    def test1(self):
        grid = [[5, 1, 9, 11], [2, 4, 8, 10], [13, 3, 6, 7], [15, 14, 12, 16]]
        self.assertEqual(solution(grid), [3, 15])

    def test2(self):
        grid = [[-5, -1, -9, -11], [-2, -4, -8, -10], [-13, -3, -6, -7], [-15, -14, -12, -16]]
        self.assertEqual(solution(grid), [-15, -3])

    def test3(self):
        self.assertEqual(solution([[0]]), [0, 0])

    def test4(self):
        grid = [[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12], [13, 14, 15, 16]]
        self.assertEqual(solution(grid), [4, 13])

    def test5(self):
        grid = [[1, 1, 1, 1], [1, 1, 1, 1], [1, 1, 1, 1], [1, 1, 1, 1]]
        self.assertEqual(solution(grid), [1, 1])

    def test6(self):
        grid = [[-1, -2, -3, -4], [-5, -6, -7, -8], [-9, -10, -11, -12], [-13, -14, -15, -16]]
        self.assertEqual(solution(grid), [-13, -4])

    def test7(self):
        self.assertEqual(solution([]), [None, None])


if __name__ == '__main__':
    unittest.main()
```
# Problem Statement
The task is to write a recursive function `solution(n)` that takes an integer `n` as an input and returns a list of integers from `n` to `1`, inclusive, in decreasing order. Make sure to use recursion in this task.

For example, for `n = 5`, the output should be `[5, 4, 3, 2, 1]`.

# Solution
```python
def solution(n):
    if n == 1:
        return [1]
    else:
        return [n] + solution(n - 1)
    pass
```

# Tests
```python
import unittest
from solution import solution


class SolutionTests(unittest.TestCase):
    def test1(self):
        self.assertEqual(solution(5), [5, 4, 3, 2, 1])

    def test2(self):
        self.assertEqual(solution(1), [1])

    def test3(self):
        self.assertEqual(solution(10), [10, 9, 8, 7, 6, 5, 4, 3, 2, 1])

    def test4(self):
        self.assertEqual(solution(50), [50, 49, 48, 47, 46, 45, 44, 43, 42, 41, 40, 39, 38, 37, 36, 35, 34, 33, 32, 31, 30, 29, 28, 27, 26, 25, 24, 23, 22, 21, 20, 19, 18, 17, 16, 15, 14, 13, 12, 11, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1])

    def test5(self):
        self.assertEqual(solution(100), [100, 99, 98, 97, 96, 95, 94, 93, 92, 91, 90, 89, 88, 87, 86, 85, 84, 83, 82, 81, 80, 79, 78, 77, 76, 75, 74, 73, 72, 71, 70, 69, 68, 67, 66, 65, 64, 63, 62, 61, 60, 59, 58, 57, 56, 55, 54, 53, 52, 51, 50, 49, 48, 47, 46, 45, 44, 43, 42, 41, 40, 39, 38, 37, 36, 35, 34, 33, 32, 31, 30, 29, 28, 27, 26, 25, 24, 23, 22, 21, 20, 19, 18, 17, 16, 15, 14, 13, 12, 11, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1])

    def test6(self):
        self.assertEqual(solution(75), [75, 74, 73, 72, 71, 70, 69, 68, 67, 66, 65, 64, 63, 62, 61, 60, 59, 58, 57, 56, 55, 54, 53, 52, 51, 50, 49, 48, 47, 46, 45, 44, 43, 42, 41, 40, 39, 38, 37, 36, 35, 34, 33, 32, 31, 30, 29, 28, 27, 26, 25, 24, 23, 22, 21, 20, 19, 18, 17, 16, 15, 14, 13, 12, 11, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1])

    def test7(self):
        self.assertEqual(solution(64), [64, 63, 62, 61, 60, 59, 58, 57, 56, 55, 54, 53, 52, 51, 50, 49, 48, 47, 46, 45, 44, 43, 42, 41, 40, 39, 38, 37, 36, 35, 34, 33, 32, 31, 30, 29, 28, 27, 26, 25, 24, 23, 22, 21, 20, 19, 18, 17, 16, 15, 14, 13, 12, 11, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1])

    def test8(self):
        self.assertEqual(solution(21), [21, 20, 19, 18, 17, 16, 15, 14, 13, 12, 11, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1])

    def test9(self):
        self.assertEqual(solution(8), [8, 7, 6, 5, 4, 3, 2, 1])

    def test10(self):
        self.assertEqual(solution(33), [33, 32, 31, 30, 29, 28, 27, 26, 25, 24, 23, 22, 21, 20, 19, 18, 17, 16, 15, 14, 13, 12, 11, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1])

if __name__ == '__main__':
    unittest.main()
```
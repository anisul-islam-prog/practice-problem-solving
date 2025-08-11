## Problem Statement:
You are given a list of n integers. Your task is to find the zero-based index of the first occurrence of this specific value in the list. If the provided value isn't found in the list at all, return `-1` instead.

In this task, you must implement the solution without using any built-in functions or methods. Specifically, the use of the Python `index()` method of a list is not allowed in your solution

## Solution:
```python
def solution(lst, val):
    for i in range(len(lst)):
        if lst[i] == val:
            return i
    return -1
    pass
```
## Tests:
```python
import unittest
from solution import solution

class SolutionTests(unittest.TestCase):
    def test_1(self):
        self.assertEqual(solution([1, 2, 3, 4, 5], 5), 4)

    def test_2(self):
        self.assertEqual(solution([1, 2, 3, 4, 5], 1), 0)

    def test_3(self):
        self.assertEqual(solution([1, 2, 3, 4], 10), -1)

    def test_4(self):
        self.assertEqual(solution([1, 2, 3, 4], 2), 1)

    def test_5(self):
        self.assertEqual(solution([1], 1), 0)

    def test_6(self):
        self.assertEqual(solution([1, 2, 2, 2, 2], 2), 1)

    def test_7(self):
        self.assertEqual(solution([-1, -2, -3, -4, -5], -1), 0)

    def test_8(self):
        self.assertEqual(solution([-1, -2, -3, -4, -5], -10), -1)

if __name__ == '__main__':
    unittest.main()
```
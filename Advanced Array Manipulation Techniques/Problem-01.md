# Problem Statement
You are given an array of `n` integers. Your task is to reverse the array without using any additional lists or the built-in `reversed()` function.

Amend the array in-place and return the array. In-place here means you are not allowed to use any additional lists in your solution.

# Solution
```python
def solution(arr):
    n = len(arr)
    for i in range(n // 2):
        # Swap elements using indexing
        arr[i], arr[n - 1 - i] = arr[n - 1 - i], arr[i]
    return arr
    pass

```

# Tests
```python
import unittest
from solution import solution

class SolutionTests(unittest.TestCase):

    def test1(self):
        self.assertEqual(solution([7, 2, 6, 3, 8, 9, 1]), [1, 9, 8, 3, 6, 2, 7])

    def test2(self):
        self.assertEqual(solution([8, 9]), [9, 8])

    def test3(self):
        self.assertEqual(solution([1]), [1])

    def test4(self):
        self.assertEqual(solution([3, 2, 6, 4, 7, 9, 1]), [1, 9, 7, 4, 6, 2, 3])

    def test5(self):
        self.assertEqual(solution([5, 4, 3, 2, 1]), [1, 2, 3, 4, 5])

    def test6(self):
        self.assertEqual(solution([100, 200, 300, 400, 500, 600]), [600, 500, 400, 300, 200, 100])

    def test7(self):
        self.assertEqual(solution([0, 0, 0, 0, 0, 0, 0]), [0, 0, 0, 0, 0, 0, 0])

    def test8(self):
        self.assertEqual(solution([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]), [10, 9, 8, 7, 6, 5, 4, 3, 2, 1])

    def test9(self):
        self.assertEqual(solution([10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 120, 130]), [130, 120, 110, 100, 90, 80, 70, 60, 50, 40, 30, 20, 10])
        
    def test10(self):
        self.assertEqual(solution([1, 3, 5, 7, 9, 11]), [11, 9, 7, 5, 3, 1])

    def test11(self):
        self.assertEqual(solution([2, 4, 6, 8, 10, 12]), [12, 10, 8, 6, 4, 2])

    def test12(self):
        self.assertEqual(solution([100, 99, 98, 97, 96]), [96, 97, 98, 99, 100])

    def test13(self):
        self.assertEqual(solution([100, 75, 50, 25, 0]), [0, 25, 50, 75, 100])

    def test14(self):
        self.assertEqual(solution([-100, -200, -300, -400, -500]), [-500, -400, -300, -200, -100])

    def test15(self):
        self.assertEqual(solution([0, -1, -2, -3, -4, -5, -6]), [-6, -5, -4, -3, -2, -1, 0])

    def test16(self):
        self.assertEqual(solution([1, -2, 3, -4, 5, -6, 7]), [7, -6, 5, -4, 3, -2, 1])


if __name__ == '__main__':
    unittest.main()
```
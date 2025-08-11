# Problem Statement
You are given a list of n integers. The goal of this task is to return the reversed list of integers without using any built-in Python functions or methods related to reversing a list.

# Solution
```python
def solution(numbers):
    reversedNumbers = []
    for i in range(len(numbers) - 1, -1, -1):
        reversedNumbers.append(numbers[i])
    return reversedNumbers
    pass
```

# Tests
```python
import unittest
from solution import solution

class TestSolution(unittest.TestCase):
    def test1(self):
        self.assertEqual(solution([1, 2, 3, 4, 5]), [5, 4, 3, 2, 1])

    def test2(self):
        self.assertEqual(solution([1]), [1])

    def test3(self):
        self.assertEqual(solution([5, 4, 3, 2, 1]), [1, 2, 3, 4, 5])

    def test4(self):
        self.assertEqual(solution([-7, 9, 8, 4]), [4, 8, 9, -7])

    def test5(self):
        self.assertEqual(solution([1000, -1000, 0]), [0, -1000, 1000]) 

    def test6(self):
        self.assertEqual(solution([0, 0, 0, 0, 0]), [0, 0, 0, 0, 0])

    def test7(self):
        self.assertEqual(solution([3498, 323, 54398, -202, 92387, 2397, 913, -123, -439438]), [-439438, -123, 913, 2397, 92387, -202, 54398, 323, 3498])
    
    def test8(self):
        self.assertEqual(solution([]), [])
    
    def test9(self):
        self.assertEqual(solution(list(range(1, 101))), list(range(100, 0, -1)))


if __name__ == '__main__':
    unittest.main()
```
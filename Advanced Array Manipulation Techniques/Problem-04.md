# Problem Statement
You have been given an array of `n` integers. Your task is to write a function that reverses the array in groups of `k` size, and if the last group has fewer than `k` elements, reverse all of them. Return the newly organized array after the groups have been reversed.

For example, given the array `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]` and `k = 3`, the output should be: `[3, 2, 1, 6, 5, 4, 9, 8, 7, 10]`. The first three elements are reversed to get `[3, 2, 1]`, the next three become `[6, 5, 4]`, the following three are `[9, 8, 7]`, and the final one remains `[10]` as there are fewer than `k` elements remaining.

# Solution
```python
def solution(numbers, k):
    result = []
    for i in range(0, len(numbers), k):
        group = numbers[i:i + k]
        result.extend(group[::-1])
    return result
    pass
```

# Tests
```python
import unittest
from solution import solution

class SolutionTests(unittest.TestCase):
    def test1(self):
        self.assertEqual(solution([1, 2, 3, 4, 5, 6, 7], 3), [3, 2, 1, 6, 5, 4, 7])

    def test2(self):
        self.assertEqual(solution([1], 1), [1])

    def test3(self):
        self.assertEqual(solution([2, 3], 2), [3, 2])

    def test4(self):
        self.assertEqual(solution([10, 20, 30, 40, 50, 60, 70], 5), [50, 40, 30, 20, 10, 70, 60])

    def test5(self):
        self.assertEqual(solution([-7, -6, -5, -4, -3, -2, -1], 4), [-4, -5, -6, -7, -1, -2, -3])

    def test6(self):
        self.assertEqual(solution([10, 20, 30, 40, 50, 60, 70], 10), [70, 60, 50, 40, 30, 20, 10])

    def test7(self):
        self.assertEqual(solution([-100, 100, -100, 100, -100], 2), [100, -100, 100, -100, -100])

    def test8(self):
        self.assertEqual(solution([1, 2, 3, 4, 5, 6, 7, 8, 9, 10], 7), [7, 6, 5, 4, 3, 2, 1, 10, 9, 8])

    def test9(self):
        self.assertEqual(solution([1, 2, 3, 4, 5, 6], 1), [1, 2, 3, 4, 5, 6])


if __name__ == '__main__':
    unittest.main()
```
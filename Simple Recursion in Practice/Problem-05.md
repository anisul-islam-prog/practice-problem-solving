# Problem Statement
You are given a number `n`. Write a function that accepts this number as an argument and utilizes recursion to find the _Fibonacci_ number at the index `n`. You solution should have a complexity of _**O(n)**_.

A `Fibonacci` sequence is a sequence of numbers where each number is the sum of the two preceding ones, usually starting with `0` and `1`. Thus, the sequence starts `0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, ....`

For instance, if `n = 3`, the function should return `2`, and if `n = 10`, your function should return `55`, which is the 10th number in the _Fibonacci_ sequence.

Using an iterative approach to solve this problem is not allowed; you are required to solve it using recursion. Make sure to optimize your solution to have a complexity of _**O(n)**_.

# Solution
```python
def fibonacci(n: int, memo={}) -> int:
    if n in memo:
        return memo[n]
    if n == 0:
        return 0
    if n == 1:
        return 1
    memo[n] = fibonacci(n - 1) + fibonacci(n - 2)
    return memo[n]
    
    pass
```
## Notes
Base Cases: fibonacci(0) = 0, fibonacci(1) = 1

Recursive Case: fibonacci(n) = fibonacci(n-1) + fibonacci(n-2)

Memoization: Store results in a dictionary `memo` to avoid recomputation

# Tests
```python
import unittest
from solution import solution

class TestFibonacci(unittest.TestCase):

    def test1(self):
        self.assertEqual(fibonacci(0), 0)

    def test2(self):
        self.assertEqual(fibonacci(1), 1)

    def test3(self):
        self.assertEqual(fibonacci(2), 1)

    def test4(self):
        self.assertEqual(fibonacci(10), 55)

    def test5(self):
        self.assertEqual(fibonacci(20), 6765)

    def test6(self):
        self.assertEqual(fibonacci(30), 832040)

    def test7(self):
        self.assertEqual(fibonacci(50), 12586269025)

if __name__ == '__main__':
    unittest.main()
```
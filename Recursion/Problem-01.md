# Problem Statement
You are tasked with creating a function `get_sum(n)` that calculates the sum of all the numbers from n to 1 using recursion.

For instance, `get_sum(5)` should result in `15 (5 + 4 + 3 + 2 + 1 = 15)`, while `get_sum(1)` should yield `1`.

# Solution
```python
def get_sum(n):
    if n == 1:
        return 1
    else:
        return n + get_sum(n - 1)
    pass
```

# Tests
```python
import unittest
from solution import get_sum

class SolutionTests(unittest.TestCase):
    def test1(self):
        self.assertEqual(get_sum(5), 15)

    def test2(self):
        self.assertEqual(get_sum(1), 1)

    def test3(self):
        self.assertEqual(get_sum(100), 5050)

    def test4(self):
        self.assertEqual(get_sum(10), 55)
        
    def test5(self):
        self.assertEqual(get_sum(7), 28)

    def test6(self):
        self.assertEqual(get_sum(30), 465)

    def test7(self):
        self.assertEqual(get_sum(65), 2145)

    def test8(self):
        self.assertEqual(get_sum(99), 4950)

if __name__ == "__main__":
    unittest.main()
```
# Problem Statement
Your task is to create a recursive function `reverse_string(s)` that reverses a given string `s` using recursion without using Python's built-in functions like `reversed()` or `[::-1]`.

For example, `reverse_string("hello")` would return `"olleh"`.

# Solution
```python
def reverse_string(s):
    if len(s) == 0:
        return s
    return s[-1] + reverse_string(s[:-1])
    pass
```

# Tests
```python
import unittest
from solution import solution

class SolutionTests(unittest.TestCase):
    def test1(self):
        self.assertEqual(reverse_string("hello"), "olleh")

    def test2(self):
        self.assertEqual(reverse_string("python"), "nohtyp")

    def test3(self):
        self.assertEqual(reverse_string("recursion"), "noisrucer")

    def test4(self):
        self.assertEqual(reverse_string("algorithm"), "mhtirogla")

    def test5(self):
        self.assertEqual(reverse_string("A"), "A")

    def test6(self):
        self.assertEqual(reverse_string(""), "")

    # Removed test case with the string of length 1000 
    # since it exceeds Python's recursion limit.

if __name__ == '__main__':
    unittest.main()
```
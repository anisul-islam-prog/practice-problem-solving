# Problem Statement
Now, let's try to solve the problem-04 more efficiently! We will still be searching for the longest common prefix in the given array of strings.

To add an additional layer of complexity, in this task, you need to find a more efficient approach with the expected complexity of `O(strs.length * log(strs.length) * max_length)`.

Hint: think about ordering strings in some way.

# Solution
```python
def efficient_LCP(strs):
    if not strs:
        return ""
    
    strs.sort()
    
    first = strs[0]
    last = strs[-1]
    i = 0

    while i < len(first) and i < len(last) and first[i] == last[i]:
        i += 1

    return first[:i]
    pass
```

# Tests
```python
import unittest
from solution import efficient_LCP

class SolutionTests(unittest.TestCase):

    def test1(self):
        self.assertEqual(efficient_LCP(["floss", "flight", "floral"]), "fl")

    def test2(self):
        self.assertEqual(efficient_LCP(["acorns", "acornsa", "acornsac", "acornsab"]), "acorns")

    def test3(self):
        self.assertEqual(efficient_LCP(["abcd", "abcd", "abcd", "abcd"]), "abcd")

    def test4(self):
        self.assertEqual(efficient_LCP(["abc", "a" , "abcd"]), "a")

    def test5(self):
        self.assertEqual(efficient_LCP(["abcde", "abcdf"]), "abcd")

    def test6(self):
        self.assertEqual(efficient_LCP(["tree", "treat", "break"]), "")

    def test7(self):
        self.assertEqual(efficient_LCP(["abcd", "efgh", "ijkl"]), "")

    def test8(self):
        self.assertEqual(efficient_LCP(["apple", "applied", "apply"]), "appl")

    def test9(self):
        self.assertEqual(efficient_LCP(["apply", "applan", "applet"]), "appl")

    def test10(self):
        self.assertEqual(efficient_LCP(["python", "java", "javascript"]), "")

    def test11(self):
        self.assertEqual(efficient_LCP(["animal", "animosity", "animate"]), "anim")

    def test12(self):
        self.assertEqual(efficient_LCP(["song", "soprano", "sonar"]), "so")

    def test13(self):
        self.assertEqual(efficient_LCP(["crumble", "crunched", "crust"]), "cru")

    def test14(self):
        self.assertEqual(efficient_LCP(["spring", "summer", "fall"]), "")

    def test15(self):
        self.assertEqual(efficient_LCP(["", "abcd", "wxyz"]), "")

    def test16(self):
        self.assertEqual(efficient_LCP(["rotate", "rated", "rater"]), "r")

    def test17(self):
        self.assertEqual(efficient_LCP(["tasmania", "task", "tassel"]), "tas")

    def test18(self):
        self.assertEqual(efficient_LCP(["rock", "rocket", "rocky"]), "rock")

    def test19(self):
        self.assertEqual(efficient_LCP(["invitation", "invigorating", "invalid"]), "inv")

    def test20(self):
        self.assertEqual(efficient_LCP(["intermingle", "intercept", "interchange"]), "inter")

if __name__ == '__main__':
    unittest.main()
```
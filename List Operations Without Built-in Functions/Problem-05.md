# Problem Statement
You are provided with two lists of integers, `listA` and `listB`. Your task is to determine if listB is a contiguous sublist of `listA`. You need to return `True` if `listB` is a contiguous sublist of `listA`, and `False` otherwise.

A sublist is defined as a subset of consecutive elements within a list. For instance, `[2, 3]` is a sublist of `[1, 2, 3, 4]` but not a sublist of `[1, 3, 2, 4]`.

Note that you are not allowed to use any built-in Python functions for this task except for the `len()` function to get the length of a list. All other operations should be executed with basic Python programming constructs.

# Solution
```python
def solution(listA, listB):

    for i in range(len(listA)):
        if listA[i] == listB[0]:
            s = 0
            for j in range(len(listB)):
                # check if subset is greater then the end of size of listA
                if i + j >= len(listA):
                    break
                if listA[i + j] == listB[j]:
                    s += 1
                    continue
                else:
                    break
            if s == len(listB):
                return True
    return False        
    pass
```

# Tests
```python
import unittest
from solution import solution

class SolutionTests(unittest.TestCase):
    def test1(self):
        self.assertEqual(solution([1, 2, 3, 4, 5], [2, 3, 4]), True)

    def test2(self):
        self.assertEqual(solution([1, -1, 3, -2, 3, 2, 5], [3, 2]), True)

    def test3(self):
        self.assertEqual(solution([-9, -8, -7, -6], [-8, -7]), True)
        
    def test4(self):
        self.assertEqual(solution([1, 2, 2, 3, 2, 4, 5], [2, 2, 3]), True)
        
    def test5(self):
        self.assertEqual(solution([5, 4, 3, 2, 1], [3, 2, 1]), True)
        
    def test6(self):
        self.assertEqual(solution([-1, -2, -3, -4, -5], [-2, -3, -4]), True)
        
    def test7(self):
        self.assertEqual(solution([-5, 9, -5], [-5]), True)

    def test8(self):
        self.assertEqual(solution([1, 2, 3, 4, 5], [3, 4, 6]), False)

    def test9(self):
        self.assertEqual(solution([1, -1, 3, -2, 3, 2, 5], [2, 3]), False)

    def test10(self):
        self.assertEqual(solution([-9, -8, -7, -6], [-7, -7]), False)
        
    def test11(self):
        self.assertEqual(solution([1, 2, 2, 3, 2, 4, 5], [2, 3, 3]), False)
        
    def test12(self):
        self.assertEqual(solution([5, 4, 3, 2, 1], [1, 3, 2]), False)
        
    def test13(self):
        self.assertEqual(solution([-1, -2, -3, -4, -5], [-3, -2, -4]), False)
        
    def test14(self):
        self.assertEqual(solution([-5, 9, -5], [5]), False)


if __name__ == '__main__':
    unittest.main()
```
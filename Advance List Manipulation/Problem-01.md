# Problem Statement
You are provided with two input lists that contain `n` and `m` integers, respectively. Both lists are sorted in non-decreasing order — i.e., every element is either equal to or larger than the preceding one.

Your task is to return a new list that results from merging the two input lists so that the final output list is also in non-decreasing order. It should contain all the elements of the two lists, maintaining their order within the lists.

Your solution should not use the built-in sort function of Python but should instead use a technique similar to the one used in the lesson. The expected time complexity is **__`O(n+m)`__**.

For instance, if the two input lists are `[1, 3, 5, 7, 9]` and `[2, 2, 3, 4, 6, 6]`, your function should return `[1, 2, 2, 3, 3, 4, 5, 6, 6, 7, 9]`.

# Solution
```python
def solution(l1, l2):
    i = j = 0
    merged = []
    
    while i < len(l1) and j < len(l2):
        if l1[i] <= l2[j]:
            merged.append(l1[i])
            i += 1
        else:
            merged.append(l2[j])
            j += 1
    merged.extend(l1[i:])
    merged.extend(l2[j:])
    
    return merged
    pass
```

# Tests
```python
import unittest
from solution import solution


class SolutionTests(unittest.TestCase):
    
    def test1(self):
        self.assertEqual(
            solution([1, 3, 5, 7, 9], [2, 2, 3, 4, 6, 6]),
            [1, 2, 2, 3, 3, 4, 5, 6, 6, 7, 9]
        )
        
    def test2(self):
        self.assertEqual(
            solution([-100, 0, 50, 100], [-75, -50, -25]),
            [-100, -75, -50, -25, 0, 50, 100]
        )
        
    def test3(self):
        self.assertEqual(
            solution([1, 2, 3], [4, 5, 6]),
            [1, 2, 3, 4, 5, 6]
        )

    def test4(self):
        self.assertEqual(
            solution([1, 2, 3], [1, 2, 3]),
            [1, 1, 2, 2, 3, 3]
        )

    def test5(self):
        self.assertEqual(
            solution([-1000, -900, -800, -700], [-200, -100]),
            [-1000, -900, -800, -700, -200, -100]
        )

    def test6(self):
        self.assertEqual(
            solution([100, 200, 300], [400, 500, 600, 700]),
            [100, 200, 300, 400, 500, 600, 700]
        )

    def test7(self):
        self.assertEqual(
            solution([-1000], [1000]),
            [-1000, 1000]
        )

    def test8(self):
        self.assertEqual(
            solution([1], [1, 2, 3, 4, 5]),
            [1, 1, 2, 3, 4, 5]
        )

if __name__ == '__main__':
    unittest.main()
```
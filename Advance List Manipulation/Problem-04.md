# Problem Statement
Imagine you are given two sorted lists of integers, `list1` and `list2`. Your task is to write a Python function that will return a new sorted list that comprises elements from `list1` and `list2`, but without any common elements in both lists. This new list must also be sorted in ascending order.

For instance, if you are given `list1 = [2, 5, 7, 10]` and `list2 = [1, 5, 9]`, your function `remove_common_elements([2, 5, 7, 10], [1, 5, 9])` should return `[1, 2, 7, 9, 10]` because 5 is a common element in both lists and should be removed.

# Solution
```python
def remove_common_elements(list1, list2):
    cleanedList1 = [n for n in list1 if n not in list2]
    cleanedList2 = [n for n in list2 if n not in list1]
    cleaned = cleanedList1 + cleanedList2
    return sorted(cleaned)
    pass
```

# Tests
```python
import unittest
from solution import remove_common_elements

class TestSolution(unittest.TestCase):
    def test1(self):
        res = remove_common_elements([2, 5, 7, 10], [1, 5, 9])
        self.assertEqual(res, [1, 2, 7, 9, 10])

    def test2(self):
        res = remove_common_elements([1, 2, 3], [4, 5, 6])
        self.assertEqual(res, [1, 2, 3, 4, 5, 6])

    def test3(self):
        res = remove_common_elements([1, 2, 3], [1, 2, 3])
        self.assertEqual(res, [])

    def test4(self):
        res = remove_common_elements([], [-1, 0, 1])
        self.assertEqual(res, [-1, 0, 1])

    def test5(self):
        res = remove_common_elements([1, 2, 3], [2, 3, 4])
        self.assertEqual(res, [1, 4])

    def test6(self):
        res = remove_common_elements([-3, -2, -1], [1, 2, 3])
        self.assertEqual(res, [-3, -2, -1, 1, 2, 3])

    def test7(self):
        res = remove_common_elements([-3, -2, -1, 0], [0, 1, 2, 3])
        self.assertEqual(res, [-3, -2, -1, 1, 2, 3])

    def test8(self):
        res = remove_common_elements([-3, -1], [-2, -1])
        self.assertEqual(res, [-3, -2])

    def test9(self):
        res = remove_common_elements([1, 2, 3, 4, 5, 6, 7], [2, 4, 6])
        self.assertEqual(res, [1, 3, 5, 7])
    
    def test10(self):
        res = remove_common_elements([1, 3, 5, 7], [2, 4, 6, 8, 10, 12])
        self.assertEqual(res, [1, 2, 3, 4, 5, 6, 7, 8, 10, 12])
    
    def test11(self):
        res = remove_common_elements([2, 4, 6, 8, 10, 12], [1, 3, 5, 7])
        self.assertEqual(res, [1, 2, 3, 4, 5, 6, 7, 8, 10, 12])
    
    def test12(self):
        res = remove_common_elements([10, 20, 30], [5, 15, 20, 25])
        self.assertEqual(res, [5, 10, 15, 25, 30])

if __name__ == '__main__':
    unittest.main()
```
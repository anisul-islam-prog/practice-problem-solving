# Problem Statement
You are given a list of n integers. Write a Python function that sorts this list using the QuickSort algorithm. Your function should take the list as input and return a sorted list in ascending order without using any built-in sorting functions.

For instance, if the provided list is `[3, 6, 8, 10, 1, 2, 1]`, the function should return `[1, 1, 2, 3, 6, 8, 10]`.

The task requires an efficient solution, and the maximum expected time complexity is _`O(nlogn)`_.

# Solution
```python
def quicksort_custom(arr):
    # Base case: arrays with 0 or 1 element are already sorted
    n = len(arr)
    if n <= 1:
        return arr
    # Step 1: Choose pivot: (commonly the last element)
    pivot = arr[-1]
    left = []
    right = []
    equal = []

    # Step 2: Partition
    for num in arr:
        if num < pivot:
            left.append(num)
        if num > pivot:
            right.append(num)
        if num == pivot:
            equal.append(num)
    # Step 3: Recursively sort and combine
    return quicksort_custom(left) + equal + quicksort_custom(right)
    pass
```

# Tests
```python
import unittest
from solution import quicksort_custom

class SolutionTests(unittest.TestCase):
    
    def test1(self):
        self.assertEqual(quicksort_custom([3, 6, 8, 10, 1, 2, 1]), [1, 1, 2, 3, 6, 8, 10])

    def test2(self):
        self.assertEqual(quicksort_custom([5, 4, 3, 2, 1]), [1, 2, 3, 4, 5])

    def test3(self):
        self.assertEqual(quicksort_custom([7, 8, 4, 2]), [2, 4, 7, 8])

    def test4(self):
        self.assertEqual(quicksort_custom([]), [])

    def test5(self):
        self.assertEqual(quicksort_custom([-1, 2, -3]), [-3, -1, 2])

    def test6(self):
        self.assertEqual(quicksort_custom([10] * 50), [10] * 50)

    def test7(self):
        self.assertEqual(quicksort_custom([-10, 5] * 50), [-10] * 50 + [5] * 50)

    def test8(self):
        self.assertEqual(quicksort_custom([15, 10, 45, 25, 36, 12, 27]), [10, 12, 15, 25, 27, 36, 45])

    def test9(self):
        self.assertEqual(quicksort_custom(list(range(-50, 50))), list(range(-50, 50)))

    def test10(self):
        self.assertEqual(quicksort_custom(list(range(-100, 1)) + list(range(100, 0, -1))), list(range(-100, 101)))

    def test11(self):
        self.assertEqual(quicksort_custom([1, 4, 2, 8, 5, 7]), [1, 2, 4, 5, 7, 8])

    def test12(self):
        self.assertEqual(quicksort_custom([1, 10, 2, 9, 3, 8]), [1, 2, 3, 8, 9, 10])

    def test13(self):
        self.assertEqual(quicksort_custom([6, 5, 3, 1, 8, 7, 2, 4]), [1, 2, 3, 4, 5, 6, 7, 8])

    def test14(self):
        self.assertEqual(quicksort_custom(list(range(-500, 500, 3)) + list(range(500, -500, -3))), sorted(list(range(-500, 500, 3)) + list(range(500, -500, -3))))


if __name__ == '__main__':
    unittest.main()
```
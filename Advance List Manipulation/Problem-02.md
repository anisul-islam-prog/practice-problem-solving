# Problem Statement
You are given two sorted lists, each containing `n` integers. Your task is to merge these two lists into a new list such that:

The resulting list is sorted in descending order.
If there are duplicate elements in the two lists, they should be merged so that each duplicate appears only once in the final list.
For instance, if you are given two lists, `[1, 2, 3, 4, 5]` and `[3, 4, 5, 6, 7]`, your function should return `[7, 6, 5, 4, 3, 2, 1]` as the merged list.

# Solution
```python
def merge_sorted_lists_descending_unique(l1, l2):
    # Step 1: Merge and remove duplicates
    merged_set = set(l1) | set(l2)

    # Step 2: Sort in descending order
    return sorted(merged_set, reverse=True)
    pass
```

# Tests
```python
import unittest
import unittest
from solution import merge_sorted_lists_descending_unique

class SolutionTests(unittest.TestCase):

    def test1(self):
        self.assertEqual(merge_sorted_lists_descending_unique([1, 2, 3, 4, 5], [2, 3, 5, 6, 10]), [10, 6, 5, 4, 3, 2, 1])

    def test2(self):
        self.assertEqual(merge_sorted_lists_descending_unique([2, 4, 8], [1, 3, 7, 8]), [8, 7, 4, 3, 2, 1])

    def test3(self):
        self.assertEqual(merge_sorted_lists_descending_unique([-6, -2, 1, 3], [1, 5, 6, 7, 10]), [10, 7, 6, 5, 3, 1, -2, -6])

    def test4(self):
        self.assertEqual(merge_sorted_lists_descending_unique([-100, -50, 0, 50, 100], [-200, -100, 0, 100, 200]), [200, 100, 50, 0, -50, -100, -200])

    def test5(self):
        self.assertEqual(merge_sorted_lists_descending_unique([1], [1]), [1])

    def test6(self):
        self.assertEqual(merge_sorted_lists_descending_unique([10, 20, 30], [-30, -20, -10]), [30, 20, 10, -10, -20, -30])

    def test7(self):
        self.assertEqual(merge_sorted_lists_descending_unique([100, 200, 300, 400, 500], [100, 200, 300, 400, 500]), [500, 400, 300, 200, 100])

    def test8(self):
        self.assertEqual(merge_sorted_lists_descending_unique([-10**6, -500, 0, 500, 10**6], [-10**6, -500, 0, 500, 10**6]), [10**6, 500, 0, -500, -10**6])

    def test9(self):
        self.assertEqual(merge_sorted_lists_descending_unique([1, 2, 3, 4, 5], [6, 7, 8, 9, 10]), [10, 9, 8, 7, 6, 5, 4, 3, 2, 1])

    def test10(self):
        self.assertEqual(merge_sorted_lists_descending_unique([-10, -9, -8, -7, -6], [-5, -4, -3, -2, -1]), [-1, -2, -3, -4, -5, -6, -7, -8, -9, -10])

    def test11(self):
        self.assertEqual(merge_sorted_lists_descending_unique([i for i in range(1, 1001)], [i for i in range(500, 1501)]), [i for i in range(1500, 0, -1)])

    def test12(self):
        self.assertEqual(merge_sorted_lists_descending_unique([1]*500, [2]*500), [2, 1])

    def test13(self):
        self.assertEqual(merge_sorted_lists_descending_unique(list(range(-500, 1)), list(range(1, 501))), list(range(500, -501, -1)))

    def test14(self):
        self.assertEqual(merge_sorted_lists_descending_unique(list(range(-1000, 0)), list(range(-1000, 0))), [i for i in range(-1, -1001, -1)])

    def test15(self):
        self.assertEqual(merge_sorted_lists_descending_unique([i**2 for i in range(32)], [i**2 for i in range(32, 64)]), [i**2 for i in range(63, -1, -1)])

    def test16(self):
        self.assertEqual(merge_sorted_lists_descending_unique([int(i/2) for i in range(200)], [int(i/2) for i in range(200, 400)]), [i for i in range(199, -1, -1)])

    def test17(self):
        self.assertEqual(merge_sorted_lists_descending_unique([5]*1000, [10]*1000), [10, 5])

    def test18(self):
        self.assertEqual(merge_sorted_lists_descending_unique([i for i in range(1000)], [i - 500 for i in range(1000)]), [i for i in range(999, -501, -1)])

    def test19(self):
        self.assertEqual(merge_sorted_lists_descending_unique([0, 1, 1, 1, 2, 2, 3], [1, 2, 4, 4, 5]), [5, 4, 3, 2, 1, 0])


if __name__ == '__main__':
    unittest.main()
```
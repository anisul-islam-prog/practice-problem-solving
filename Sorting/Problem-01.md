# Problem Statement
You are given an array of integers, and your task is to sort the array using the Selection Sort method, wherein the smallest integer is selected from the array and swapped with the first position. This process is repeated until the array is sorted.

For example, given an array `[3, 1, 2, 4, 5]`, your function should return `[1, 2, 3, 4, 5]`.

The expected time complexity is **__`O(n^2)`__**.

# Solution
```python
def selection_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(i + 1, n):
            if arr[j] < arr[i]:
                # temp = arr[i]
                # arr[i] = arr[j]
                # arr[j] = temp
                arr[i], arr[j] = arr[j], arr[i]
    return arr
    pass
```

# Tests
```python
import unittest
from solution import selection_sort

class SelectionSortTest(unittest.TestCase):
    def test_case_1(self):
        self.assertEqual(selection_sort([3, 1, 2, 4, 5]), [1, 2, 3, 4, 5])

    def test_case_2(self):
        self.assertEqual(selection_sort([5, 4, 3, 2, 1]), [1, 2, 3, 4, 5])

    def test_case_3(self):
        self.assertEqual(selection_sort([1, 1, 1, 1, 1]), [1, 1, 1, 1, 1])

    def test_case_4(self):
        self.assertEqual(selection_sort([1, 7, 5, 2, 3, 9, 4]), [1, 2, 3, 4, 5, 7, 9])

    def test_case_5(self):
        self.assertEqual(selection_sort([10, -5, 2, 4, -1]), [-5, -1, 2, 4, 10])

    def test_case_6(self):
        self.assertEqual(selection_sort([1]), [1])

    def test_case_7(self):
        self.assertEqual(selection_sort([-4, -5, -1, -2, -3]), [-5, -4, -3, -2, -1])

    def test_case_8(self):
        self.assertEqual(selection_sort([50, 40, 10, 20, 30]), [10, 20, 30, 40, 50])

    def test_case_9(self):
        self.assertEqual(selection_sort([340, 29, 45, 10, 230]), [10, 29, 45, 230, 340])

    def test_case_10(self):
        self.assertEqual(selection_sort([10, 20, 10, 10, 20]), [10, 10, 10, 20, 20])

    def test_case_11(self):
        self.assertEqual(selection_sort([-18, -5, 0, 4, 6]), [-18, -5, 0, 4, 6])

    def test_case_12(self):
        self.assertEqual(selection_sort([0, -1, -2, -3, -4]), [-4, -3, -2, -1, 0])

    def test_case_13(self):
        self.assertEqual(selection_sort([-10, -9, -8, -7, -6]), [-10, -9, -8, -7, -6])

    def test_case_14(self):
        self.assertEqual(selection_sort([20, 19, 18, 17, 16]), [16, 17, 18, 19, 20])

    def test_case_15(self):
        self.assertEqual(selection_sort([100, -10, 200, -20, 300]), [-20, -10, 100, 200, 300])

    def test_case_16(self):
        self.assertEqual(selection_sort([500, 400, 300, 200, 100]), [100, 200, 300, 400, 500])

    def test_case_17(self):
        self.assertEqual(selection_sort([-500, -400, -300, -200, -100]), [-500, -400, -300, -200, -100]) 

    def test_case_18(self):
        self.assertEqual(selection_sort([]), [])

if __name__ == '__main__':
    unittest.main()
```
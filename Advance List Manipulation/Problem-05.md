# Problem Statement
You work with large data sets in Python, and typically, the data arrive sorted within individual batches but not across all batches. You are given `n` lists, where each list is sorted in ascending order. The function should return a single list consisting of all elements from all lists, sorted in ascending order.

The time complexity of your solution should be **__`O(n⋅m)`__**, where `n` is the total number of lists and m is the maximum length of any list.

Your solution is not allowed to use built-in functions like `sorted`, `sort`, or additional libraries like `heapq`.

# Solution
```python
def merge_n_sorted_lists(arr: list[list[int]]) -> list[int]:
    n = len(arr)
    cols = [0] * n  # Track current column index in each list
    
    result = []

    while True:
        min_val = float('inf')
        rowNoOf_min_val = -1

        # Find the smallest current element across all arr
        for i in range(n):
            
            row = arr[i]
            if cols[i] < len(row):
                val = row[cols[i]]
            
                if val < min_val:
            
                    min_val = val
                    rowNoOf_min_val = i

        if rowNoOf_min_val == -1:
            break  # All arr are exhausted

        result.append(min_val)
        cols[rowNoOf_min_val] += 1

    return result

    pass
```

# Tests
```python
import unittest
from solution import merge_n_sorted_lists

class TestSolution(unittest.TestCase):
    def test_1(self):
        self.assertEqual(merge_n_sorted_lists([[1, 5, 9], [2, 3, 10], [4, 6, 8]]), [1, 2, 3, 4, 5, 6, 8, 9, 10])

    def test_2(self):
        self.assertEqual(merge_n_sorted_lists([[-3, 10, 27], [32, 50, 78], [98, 100, 110]]), [-3, 10, 27, 32, 50, 78, 98, 100, 110])

    def test_3(self):
        self.assertEqual(merge_n_sorted_lists([[12, 15, 17, 20], [3, 7, 8, 10], [2, 9, 11, 30]]), [2, 3, 7, 8, 9, 10, 11, 12, 15, 17, 20, 30])

    def test_4(self):
        self.assertEqual(merge_n_sorted_lists([[111, 125, 143, 145], [39, 128, 150, 160], [58, 130, 166, 198]]), [39, 58, 111, 125, 128, 130, 143, 145, 150, 160, 166, 198])

    def test_5(self):
        self.assertEqual(merge_n_sorted_lists([[-5], [-4], [-3], [-2], [-1]]), [-5, -4, -3, -2, -1])

    def test_6(self):
        self.assertEqual(merge_n_sorted_lists([[], [], [-3, -2, -1]]), [-3, -2, -1])

    def test_7(self):
        self.assertEqual(merge_n_sorted_lists([[1], [2], [3], [4], [5]]), [1, 2, 3, 4, 5])

    def test_8(self):
        self.assertEqual(merge_n_sorted_lists([[10, 20, 30], [15, 25], [23, 24, 35]]), [10, 15, 20, 23, 24, 25, 30, 35])

    def test_9(self):
        self.assertEqual(merge_n_sorted_lists([[-45, -40, -35], [-36, -32, -22], [-18, -9, -3]]), [-45, -40, -36, -35, -32, -22, -18, -9, -3])

    def test_10(self):
        self.assertEqual(merge_n_sorted_lists([[100, 200, 300, 400], [150, 250], [500, 600, 700]]), [100, 150, 200, 250, 300, 400, 500, 600, 700])

    def test_11(self):
        self.assertEqual(merge_n_sorted_lists([[3, 5, 7, 9], [2, 4, 6, 8, 10]]), [2, 3, 4, 5, 6, 7, 8, 9, 10])

    def test_12(self):
        self.assertEqual(merge_n_sorted_lists([[-1000, 0, 1000], [-500, 0, 500], [-50, 0, 50]]), [-1000, -500, -50, 0, 0, 0, 50, 500, 1000])

    def test_13(self):
        self.assertEqual(merge_n_sorted_lists([[13, 26, 39], [14, 28, 42], [15, 30, 45]]), [13, 14, 15, 26, 28, 30, 39, 42, 45])

if __name__ == '__main__':
    unittest.main()
```
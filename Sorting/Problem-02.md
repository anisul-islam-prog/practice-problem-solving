# Problem Statement
You need to implement the Insertion Sort algorithm. Given a list of `n` integers, the algorithm must sort the elements of this list in increasing order using Insertion Sort.

The Insertion Sort algorithm iterates over an index from left to right. As the index moves to the right, it "inserts" the element at the index into the correct location in the "already sorted" portion of the list on the left.

# Solution
```python
def insertion_sort(arr):
    
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
    return arr
    pass
```

# Tests
```python
import unittest
from solution import insertion_sort


class SolutionTests(unittest.TestCase):
    def test1(self):
        self.assertEqual(insertion_sort([5, 2, 4, 6, 1, 3]), [1, 2, 3, 4, 5, 6])

    def test2(self):
        self.assertEqual(insertion_sort([4, 3, 2, 1]), [1, 2, 3, 4])

    def test3(self):
        self.assertEqual(insertion_sort([0, 0, 0, 0]), [0, 0, 0, 0])

    def test4(self):
        self.assertEqual(insertion_sort([-50, -75, -25, -100]), [-100, -75, -50, -25])

    def test5(self):
        self.assertEqual(insertion_sort([-1, -2, -3, -4, -5, -6]), [-6, -5, -4, -3, -2, -1])

    def test6(self):
        self.assertEqual(insertion_sort([450, 325, 765, 985, 254, 754, 908, 623]), [254, 325, 450, 623, 754, 765, 908, 985])

    def test7(self):
        self.assertEqual(insertion_sort([1]), [1])

    def test8(self):
        self.assertEqual(insertion_sort([2, 1]), [1, 2])

    def test9(self):
        self.assertEqual(insertion_sort([-1000, 1000, 0]), [-1000, 0, 1000])

    def test10(self):
        self.assertEqual(insertion_sort([234, 678, 348, 987, 432, 764, 985, 543, 456, 654, 890, 10]), [10, 234, 348, 432, 456, 543, 654, 678, 764, 890, 985, 987])

    def test11(self):
        self.assertEqual(insertion_sort([1000, 999, 998, 997, 996, 995, 994, 993]), [993, 994, 995, 996, 997, 998, 999, 1000])

    def test12(self):
        self.assertEqual(insertion_sort([1000, -1000, 1000, -1000, 1000]), [-1000, -1000, 1000, 1000, 1000])

    def test13(self):
        self.assertEqual(insertion_sort([5, 2, 4, 6, 1, 2, 5, 6, 4, 7, 8, 9, 0, 3, 2, 1]), [0, 1, 1, 2, 2, 2, 3, 4, 4, 5, 5, 6, 6, 7, 8, 9])

    def test14(self):
        self.assertEqual(insertion_sort([]), [])


if __name__ == '__main__':
    unittest.main()
```
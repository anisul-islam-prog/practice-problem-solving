# Problem Statement
You are given a list of `n` integers. Your task is to implement a merge sort function to sort this list in ascending order and return the sorted list.

Please note that while Python has built-in sorting functionality, the purpose of this task is to practice implementing basic sorting algorithms, so you are not allowed to use Python's built-in sort function. Instead, implement the merge sort algorithm.

For example, if the input to your function is `[10, 3, 2, 8, -1, 5, 1]`, your function should return `[-1, 1, 2, 3, 5, 8, 10]`.

# Solution
```python
def merge(left, right):
    sorted_list = []
    i = j = 0
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            sorted_list.append(left[i])
            i += 1
        else:
            sorted_list.append(right[j])
            j += 1
    sorted_list.extend(left[i:])
    sorted_list.extend(right[j:])
    return sorted_list


def merge_sort(lst):
    if len(lst) <= 1:
        return lst
    
    mid = len(lst) // 2
    left = merge_sort(lst[:mid])
    right = merge_sort(lst[mid:])
    
    return merge(left, right)
    
    pass
```

# Tests
```python
import unittest
from solution import merge_sort

class SolutionTests(unittest.TestCase):

    def test1(self):
        input = [10, 3, 2, 8, -1, 5, 1]
        output = [-1, 1, 2, 3, 5, 8, 10]
        self.assertEqual(merge_sort(input), output)

    def test2(self):
        input = [100, -50, 200, -150, 50, -100]
        output = [-150, -100, -50, 50, 100, 200]
        self.assertEqual(merge_sort(input), output)

    def test3(self):
        input = [50]*500
        output = [50]*500
        self.assertEqual(merge_sort(input), output)
  
    def test4(self):
        input = [-1000, -999, -998, 998, 999, 1000]
        output = [-1000, -999, -998, 998, 999, 1000]
        self.assertEqual(merge_sort(input), output)

    def test5(self):
        input = list(range(100, -101, -1))
        output = list(range(-100, 101))
        self.assertEqual(merge_sort(input), output)

    def test6(self):
        input = [1]
        output = [1]
        self.assertEqual(merge_sort(input), output)

    def test7(self):
        input = [-1, -1, -1, 1, 1, 1]
        output = [-1, -1, -1, 1, 1, 1]
        self.assertEqual(merge_sort(input), output)

    def test8(self):
        input = [5, 4, 3, 2, 1]
        output = [1, 2, 3, 4, 5]
        self.assertEqual(merge_sort(input), output)

    def test9(self):
        input = [0, 0, 0, 0, 0]
        output = [0, 0, 0, 0, 0]
        self.assertEqual(merge_sort(input), output)

    def test10(self):
        input = [2, 3, 6, 2, 7, 3, 9]
        output = [2, 2, 3, 3, 6, 7, 9]
        self.assertEqual(merge_sort(input), output)

    def test11(self):
        input = []
        output = []
        self.assertEqual(merge_sort(input), output)


if __name__ == '__main__':
    unittest.main()
```
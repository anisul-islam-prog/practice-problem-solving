# Problem Statement
In this problem, you are given a list of `n` integers. Additionally, you are given an integer `shift`, which represents the number of positions each element in the list should be moved.

Your task is to create a Python function that should ***shift every element in the list*** to the right (for a positive `shift`) or to the left (for a negative `shift`) by `shift` positions. The shift should be ***circular*** — the last element should be moved to the start of the list if `shift` is positive, and vice versa.

Please implement this without the usage of any built-in functions of Python to shift, sort, or move items in the list. Your solution’s efficiency should be 
`O(n)`.

# Solution
```python
def shift_list_elements(ls, shift):
    n = len(ls)
    shift = shift % n
    result = [0] * n
    for i in range(n):
        newIndex = (i + shift) % n
        result[newIndex] = ls[i]
    return result
    pass
```


# Tests
```python
import unittest
from solution import shift_list_elements

class TestSolution(unittest.TestCase):
    def test_case_1(self):
        self.assertEqual(shift_list_elements([1, 2, 3, 4, 5], 2), [4, 5, 1, 2, 3])

    def test_case_2(self):
        self.assertEqual(shift_list_elements([1, 2, 3, 4, 5], -1), [2, 3, 4, 5, 1])

    def test_case_3(self):
        self.assertEqual(shift_list_elements([8, 20, -3, 23, 32, -4, 7], 3), [32, -4, 7, 8, 20, -3, 23])

    def test_case_4(self):
        self.assertEqual(shift_list_elements([-3], 100), [-3])

    def test_case_5(self):
        self.assertEqual(shift_list_elements([3, 2, 12, 123, 53, 23, 123, -432], 5), [123, 53, 23, 123, -432, 3, 2, 12])

    def test_case_6(self):
        self.assertEqual(shift_list_elements([1, 2, 3, 4, 5], 0), [1, 2, 3, 4, 5])

    def test_case_7(self):
        self.assertEqual(shift_list_elements([1, 1, 1, 1, 1, 1], 2), [1, 1, 1, 1, 1, 1])

    def test_case_8(self):
        self.assertEqual(shift_list_elements([1, 2, 3, 4, 5, 6, 7, 8, 9, 10], 1000), [1, 2, 3, 4, 5, 6, 7, 8, 9, 10])

    def test_case_9(self):
        self.assertEqual(shift_list_elements([-1000, -999, -998, -997, -996], -1000), [-1000, -999, -998, -997, -996])

if __name__ == "__main__":
    unittest.main()
```
# Problem Statement
You are given a list of `n` integers and a number `k`. Your task is to shuffle the array in such a way that, starting from the first element, every `k`-th element moves to the end of the array.

For instance, if `nums = [1, 2, 3, 4, 5, 6, 7, 8]` and `k = 3`, the output should be `[1, 2, 4, 5, 7, 8, 3, 6]`. Here, the 3rd element `3` and the 6th element `6` (every 3rd element starting from the first) are moved to the end of the array.

# Solution
```python
def shuffle_array(nums, k):
    moved = nums[k - 1::k]
    result = [n for i, n in enumerate(nums) if (i + 1) % k != 0]
    return result + moved
    pass

```

# Tests
```python
import unittest
from solution import shuffle_array

class ShuffleArrayTest(unittest.TestCase):
    def test_1(self):
        self.assertEqual(shuffle_array([1, 2, 3, 4, 5, 6, 7, 8], 3), [1, 2, 4, 5, 7, 8, 3, 6])

    def test_2(self):
        self.assertEqual(shuffle_array([1, 2, 3, 4, 5, 6, 7, 8], 1), [1, 2, 3, 4, 5, 6, 7, 8])

    def test_3(self):
        self.assertEqual(shuffle_array([1, 2, 3, 4], 2), [1, 3, 2, 4])

    def test_4(self):
        self.assertEqual(shuffle_array([1, 2, 3, 4, 5, 6], 4), [1, 2, 3, 5, 6, 4])

    def test_5(self):
        self.assertEqual(shuffle_array([7, 8, 9, 10, 11, 12, 13, 14, 15], 5), [7, 8, 9, 10, 12, 13, 14, 15, 11])

    def test_6(self):
        self.assertEqual(shuffle_array([-10, -9, -8, -7, -6, -5, -4, -3], 2), [-10, -8, -6, -4, -9, -7, -5, -3])

    def test_7(self):
        self.assertEqual(shuffle_array([10, 20, 30, 40, 50], 10), [10, 20, 30, 40, 50])

    def test_8(self):
        self.assertEqual(shuffle_array([199, 299, 399, 499, 599, 699, 799], 3), [199, 299, 499, 599, 799, 399, 699])

    def test_9(self):
        self.assertEqual(shuffle_array([100, 200, 300, 400, 500, 600, 700, 800, 900], 9), [100, 200, 300, 400, 500, 600, 700, 800, 900])

    def test_10(self):
        self.assertEqual(shuffle_array([766, 243, -12, 24, 0, 41], 2), [766, -12, 0, 243, 24, 41])

    def test_11(self):
        self.assertEqual(shuffle_array([12, -14, 20, 22, 28, -36, 45, 90], 7), [12, -14, 20, 22, 28, -36, 90, 45])


if __name__ == '__main__':
    unittest.main()
```
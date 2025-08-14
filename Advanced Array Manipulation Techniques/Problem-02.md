# Problem Statement
You are provided with an array of `n` integers and a number `k`. Your task is to perform an anti-clockwise rotation (toward the front) of the array by `k` positions. The rotation should be done in place, which means you have to directly manipulate the input array without creating a new one. Note that `k` might be bigger than the array length.

For example, if the input array is `[1, 2, 3, 4, 5, 6, 7]`, and `k = 3`, then after the operation, the input array should look like `[4, 5, 6, 7, 1, 2, 3]`

# Solution
```python
from typing import List


def anti_rotate_array(nums: List[int], k: int) -> None:
    k %= len(nums)
    if k == 0:
        return nums
    # nums[:] instead of nums to solve the case of copy by reference
    nums[:] = nums[k:] + nums[:k]
    return nums
    pass

```

# Tests
```python
import unittest
from typing import List

# Import the solution function
from solution import anti_rotate_array

class SolutionTests(unittest.TestCase):
    def execute_test(self, test_id: int, arr: List[int], k: int, expected: List[int]):
        anti_rotate_array(arr, k)
        self.assertEqual(arr, expected, f'Test {test_id} failed')

    def test1(self):
        self.execute_test(1, [1, 2, 3, 4, 5, 6, 7], 3, [4, 5, 6, 7, 1, 2, 3])
        
    def test2(self):
        self.execute_test(2, [1, 2, 3], 3, [1, 2, 3])
    
    def test3(self):
        self.execute_test(3, [4, 3], 2, [4, 3])
    
    def test4(self):
        self.execute_test(4, [1, 3, 5, 6, 8, 2, 4, 9], 5, [2, 4, 9, 1, 3, 5, 6, 8])
    
    def test5(self):
        self.execute_test(5, [1]*200, 199, [1]*200)

    def test6(self):
        self.execute_test(6, [56, 78, 34, 12], 0, [56, 78, 34, 12])

    def test7(self):
        self.execute_test(7, [46, 92, -38, 71, -72, 13, 59], 205, [-38, 71, -72, 13, 59, 46, 92])


if __name__ == '__main__':
    unittest.main()
```
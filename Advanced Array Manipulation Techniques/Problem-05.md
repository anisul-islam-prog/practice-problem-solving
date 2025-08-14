# Problem Statement
You are given an array of `n` integers. Write a function that rearranges the array so that the middle half of the elements (considering the left and right quarters have been eliminated) move to the beginning of the array. The remaining elements, the left and right quarters, should move to the end of the array. If `n` is not divisible by `4`, include the extra elements in the middle half.

Specifically:

Divide the array into four quarters.
Move the second and third quarters to the front.
Move the first and fourth quarters to the back.
The function should modify the array in place.

For example, if the input array is `[1, 2, 3, 4, 5, 6, 7, 8]`, your function should rearrange the array to `[3, 4, 5, 6, 1, 2, 7, 8]`.

The solution should have a time complexity of _**`O(n)`**_.

# Solution
```python
def rearrange_array(nums):
    n = len(nums)
    if n == 0:
        return nums
        
    k = len(nums) // 4
    midStart = k
    midEnd = n - k
    
    q2nd_q3rd = nums[midStart:midEnd]
    q1st_q4th = nums[:midStart] + nums[midEnd:]
     
    nums[:] = q2nd_q3rd + q1st_q4th
    return nums
    pass
```

# Tests
```python
import unittest
from solution import rearrange_array

class SolutionTests(unittest.TestCase):
    def test1(self):
        arr = [1, 2, 3, 4]
        rearrange_array(arr)
        self.assertEqual(arr, [2, 3, 1, 4])

    def test2(self):
        arr = [9, 7, 5, 1, 2, 3, 4]
        rearrange_array(arr)
        self.assertEqual(arr, [7, 5, 1, 2, 3, 9, 4])

    def test3(self):
        arr = [1, 2, 3, 4, 6, 7, 9, 11]
        rearrange_array(arr)
        self.assertEqual(arr, [3, 4, 6, 7, 1, 2, 9, 11])

    def test4(self):
        arr = [-100, -50, 0, 50, 100]
        rearrange_array(arr)
        self.assertEqual(arr, [-50, 0, 50, -100, 100])

    def test5(self):
        arr = [5, 10, 15, 20, 25, 30]
        rearrange_array(arr)
        self.assertEqual(arr, [10, 15, 20, 25, 5, 30])

    def test6(self):
        arr = [1, 1, 1, 1, 2, 2, 2, 2]
        rearrange_array(arr)
        self.assertEqual(arr, [1, 1, 2, 2, 1, 1, 2, 2])

    def test7(self):
        arr = [123, 456, 789, 101112, 131415, 161718, 192021, 222324]
        rearrange_array(arr)
        self.assertEqual(arr, [789, 101112, 131415, 161718, 123, 456, 192021, 222324])

    def test8(self):
        arr = [100, 200, 300, 400, 500, 600, 700, 800]
        rearrange_array(arr)
        self.assertEqual(arr, [300, 400, 500, 600, 100, 200, 700, 800])

    def test9(self):
        arr = [-1, -2, -3, -4, -5, -6, -7, -8]
        rearrange_array(arr)
        self.assertEqual(arr, [-3, -4, -5, -6, -1, -2, -7, -8])

    def test10(self):
        arr = [1000, 2000, 3, 4000, 5000, 6000, 7000, 8000]
        rearrange_array(arr)
        self.assertEqual(arr, [3, 4000, 5000, 6000, 1000, 2000, 7000, 8000])

    def test11(self):
        arr = [1, 1, 1, 1, 2, 3, 4, 5]
        rearrange_array(arr)
        self.assertEqual(arr, [1, 1, 2, 3, 1, 1, 4, 5])

    def test12(self):
        arr = [12, 23, 34, 45, 56, 67, 78, 89]
        rearrange_array(arr)
        self.assertEqual(arr, [34, 45, 56, 67, 12, 23, 78, 89])

    def test13(self):
        arr = [1, 3, 5, 7, 9, 2, 4, 6, 8]
        rearrange_array(arr)
        self.assertEqual(arr, [5, 7, 9, 2, 4, 1, 3, 6, 8])

    def test14(self):
        arr = [-9, -7, -5, -3, -1, 0, 1, 3, 5, 7, 9]
        rearrange_array(arr)
        self.assertEqual(arr, [-5, -3, -1, 0, 1, 3, 5, -9, -7, 7, 9])

    def test15(self):
        arr = [1, 2, 3, 4, 5, 6]
        rearrange_array(arr)
        self.assertEqual(arr, [2, 3, 4, 5, 1, 6])

    def test16(self):
        arr = [-6, -5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5, 6]
        rearrange_array(arr)
        self.assertEqual(arr, [-3, -2, -1, 0, 1, 2, 3, -6, -5, -4, 4, 5, 6])

    def test17(self):
        arr = [100, 200, 300, 400, 500, 600, 700, 800, 900]
        rearrange_array(arr)
        self.assertEqual(arr, [300, 400, 500, 600, 700, 100, 200, 800, 900])

    def test18(self):
        arr = [11, 12, 13, 14, 15, 16]
        rearrange_array(arr)
        self.assertEqual(arr, [12, 13, 14, 15, 11, 16])

    def test19(self):
        arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
        rearrange_array(arr)
        self.assertEqual(arr, [3, 4, 5, 6, 7, 8, 1, 2, 9, 10])


if __name__ == '__main__':
    unittest.main()
```
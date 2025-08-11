# Problem Statement
You are given an array of `n` integers. Your task is to return the number of **unique** elements in the array — an element is **unique** if it appears only once in the array. You cannot use any built-in Python functions to achieve this.

For example, `count_unique_elements([1, 2, 3, 2, 4]) = 3`, as there are four unique elements in the list `- 1, 3,` and `4.`

# Solution
```python
def count_unique_elements(lst):
    notUnique = []
    uniqueCount = 0
    
    for i in lst:
        c = 0
        for j in lst:
            # check if already checked
            if i in notUnique:
                break
            if i == j:
                c += 1
        if c == 1:
            uniqueCount += 1
        else:
            notUnique.append(i)
    
    return uniqueCount
    
    pass
```
# Tests
```python
import unittest
from solution import count_unique_elements

class SolutionTests(unittest.TestCase):
    def test1(self):
        self.assertEqual(count_unique_elements([1, 2, 3, 2, 4]), 3)
        
    def test2(self):
        self.assertEqual(count_unique_elements([1, 1]), 0)

    def test3(self):
        self.assertEqual(count_unique_elements([1, 2]), 2)

    def test4(self):
        self.assertEqual(count_unique_elements([1, 2, 3, 3, 3, 4, 4, 4, 4]), 2)
        
    def test5(self):
        self.assertEqual(count_unique_elements([1, 1, 1, 2, 2, 2]), 0)

    def test6(self):
        self.assertEqual(count_unique_elements([-1000, -1000, -1000, 1000, 1000, 1000]), 0)
        
    def test7(self):
        self.assertEqual(count_unique_elements([i for i in range(1, 201)]), 200)
        
    def test8(self):
        self.assertEqual(count_unique_elements([i for i in range(-1000, 1000)]), 2000)
        
    def test9(self):
        self.assertEqual(count_unique_elements([1000, 1000, 1000, 1000, 1000, -1000, -1000, -1000]), 0)
        
    def test10(self):
        self.assertEqual(count_unique_elements([100, 200, 300, 400, 500, 600, 700, 800, 900, 1000]), 10)

    def test11(self):
        self.assertEqual(count_unique_elements([]), 0)

if __name__ == '__main__':
    unittest.main()
```
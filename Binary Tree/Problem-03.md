# Problem Statement
Imagine we are given a binary tree in which each node contains an integer. Your task is to write a Python function that traverses this binary tree and returns the second smallest value among all the tree nodes. If there's no second smallest number (for example, if all the values in the tree are the same, or if there's only one node in the tree), the function should return None.

You are not allowed to use sort() or any other built-in sorting methods in your solution. You should use Binary Tree Traversal techniques, which we have discussed in the lesson.

Expected complexity is _`O(n)`_, where `n` is the number of vertices in the binary tree. The expected additional memory is *`O(1)`*.

# Solution
```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right


def second_minimum_in_tree(root):
    second_min = [None]
    min_val = [root.val]
    
    def dfs(treeNode):
        if not treeNode:
            return
        val = treeNode.val
        if val < min_val[0]:
            second_min[0] = min_val[0]
            min_val[0] = val
        if val > min_val[0]:
            if second_min[0] is None or val < second_min[0]:
                second_min[0] = val
        dfs(treeNode.left)
        dfs(treeNode.right)
    
    dfs(root)
    return second_min[0]
    
    pass
```

# Tests
```python
import unittest
from solution import second_minimum_in_tree, TreeNode

class SecondMinimumInTreeTests(unittest.TestCase):
    def test1(self):
        root = TreeNode(2, TreeNode(1), TreeNode(3))
        self.assertEqual(second_minimum_in_tree(root), 2)

    def test2(self):
        root = TreeNode(1, TreeNode(1), TreeNode(1))
        self.assertEqual(second_minimum_in_tree(root), None)

    def test3(self):
        root = TreeNode(1, None, TreeNode(2))
        self.assertEqual(second_minimum_in_tree(root), 2)

    def test4(self):
        root = TreeNode(2, TreeNode(1), None)
        self.assertEqual(second_minimum_in_tree(root), 2)

    def test5(self):
        root = TreeNode(0, None, TreeNode(-1))
        self.assertEqual(second_minimum_in_tree(root), 0)

    def test6(self):
        root = TreeNode(-10**9, TreeNode(10**9))
        self.assertEqual(second_minimum_in_tree(root), 10**9)

    def test7(self):
        root = TreeNode(2)
        self.assertEqual(second_minimum_in_tree(root), None)

    def test8(self):
        root = TreeNode(3, TreeNode(2, TreeNode(1)))
        self.assertEqual(second_minimum_in_tree(root), 2)        

if __name__ == '__main__':
    unittest.main()
```
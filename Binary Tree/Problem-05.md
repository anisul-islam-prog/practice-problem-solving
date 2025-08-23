# Problem Statement
Your task is to implement a function `is_binary_search_tree(root)` that takes the root of a binary tree as input and returns a Boolean, indicating whether the input tree is a binary search tree. In a binary search tree, for each node, its value is greater than or equal to the values of all nodes in its left subtree and less than or equal to the values of all nodes in its right subtree. It's guaranteed that all node values are distinct.

The expected time complexity of your solution is _`O(n)`_, where `n` is the number of nodes in the binary tree. Make sure to implement the solution that goes through every tree's node **only once**.

# Solution
```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right


def is_binary_search_tree(root: TreeNode) -> bool:
    
    def validate(treeNode, min_val, max_val):
        if not treeNode:
            return True
        if not (min_val < treeNode.val < max_val):
            return False
        return (validate(treeNode.left, min_val, treeNode.val) and validate(treeNode.right, treeNode.val, max_val))
    return validate(root, float('-inf'), float('inf'))
    pass
```

# Tests
```python
import unittest
from solution import TreeNode, is_binary_search_tree

class TestSolution(unittest.TestCase):
    def test1(self):
        root = TreeNode(2, TreeNode(1), TreeNode(3))
        self.assertEqual(is_binary_search_tree(root), True)

    def test2(self):
        root = TreeNode(1, TreeNode(2), TreeNode(3))
        self.assertEqual(is_binary_search_tree(root), False)

    def test3(self):
        root = TreeNode(8, TreeNode(3, TreeNode(1), TreeNode(6)), TreeNode(10, None, TreeNode(14)))
        self.assertEqual(is_binary_search_tree(root), True)

    def test4(self):
        root = TreeNode(10, TreeNode(5), TreeNode(15, TreeNode(6), TreeNode(20)))
        self.assertEqual(is_binary_search_tree(root), False)

    def test5(self):
        root = TreeNode(30, TreeNode(20, TreeNode(10), TreeNode(25)), TreeNode(40))
        self.assertEqual(is_binary_search_tree(root), True)

    def test6(self):
        root = TreeNode(-1)
        self.assertEqual(is_binary_search_tree(root), True)

    def test7(self):
        root = None
        self.assertEqual(is_binary_search_tree(root), True)

    def test8(self):
        root = TreeNode(20, TreeNode(10, TreeNode(5), TreeNode(15)), TreeNode(30))
        self.assertEqual(is_binary_search_tree(root), True)

    def test9(self):
        root = TreeNode(3, TreeNode(1), TreeNode(5, TreeNode(4), TreeNode(6)))
        self.assertEqual(is_binary_search_tree(root), True)

    def test10(self):
        root = TreeNode(3, TreeNode(1), TreeNode(4, TreeNode(5)))
        self.assertEqual(is_binary_search_tree(root), False)

if __name__ == '__main__':
    unittest.main()
```
# Problem Statement
In this task, you need to implement the Preorder traversal algorithm for a binary tree in Python.

In the Preorder traversal method, each node is processed before (pre) either of its sub-trees. This means the processing order is `Root`, `Left`, and `Right`.

For example, for the binary tree defined like this:

```Python
root = TreeNode(1, TreeNode(2, TreeNode
(4), TreeNode(5)), TreeNode(3))
```
the output should be `preorder_traversal(root) = [1, 2, 4, 5, 3]`.

# Solution
```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right


def preorder_traversal(root):
    return [root.val] + preorder_traversal(root.left) + preorder_traversal(root.right) if root else []
    pass
```

# Tests
```python
import unittest
from solution import TreeNode, preorder_traversal

class TestSolution(unittest.TestCase):

    def test1(self):
        root = TreeNode(1)
        expected_output = [1]
        self.assertEqual(preorder_traversal(root), expected_output)

    def test2(self):
        root = TreeNode(7, TreeNode(1), TreeNode(2))
        expected_output = [7, 1, 2]
        self.assertEqual(preorder_traversal(root), expected_output)

    def test3(self):
        root = TreeNode(-1, None, TreeNode(1))
        expected_output = [-1, 1]
        self.assertEqual(preorder_traversal(root), expected_output)

    def test4(self):
        root = TreeNode(5, TreeNode(9, TreeNode(1), TreeNode(2)), TreeNode(-3, TreeNode(3), TreeNode(4)))
        expected_output = [5, 9, 1, 2, -3, 3, 4]
        self.assertEqual(preorder_traversal(root), expected_output)

    def test5(self):
        n10, n11, n12 = TreeNode(10), TreeNode(11), TreeNode(12)
        root = TreeNode(0,
                        TreeNode(-1,
                                 TreeNode(-2,
                                          TreeNode(-3, n10, n11),
                                          TreeNode(9)),
                                 TreeNode(8)),
                        n12)
        expected_output = [0, -1, -2, -3, 10, 11, 9, 8, 12]
        self.assertEqual(preorder_traversal(root), expected_output)

if __name__ == '__main__':
    unittest.main()
```
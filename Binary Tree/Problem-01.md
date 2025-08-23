# Problem Statement
Binary trees are frequently used due to their efficiency in many operations compared to other data structures. However, inspecting or manipulating nodes in a binary tree requires an understanding of tree traversal methods.

Your task is to implement a recursive function called `postorder_traversal` that visits all the nodes of a binary tree in *postorder* (`left`, `right`, `root`) traversal order.

For example, if the binary tree you traverse is defined as:

```Python
root = TreeNode(1, TreeNode(4, TreeNode(6), TreeNode(7)), TreeNode(3, TreeNode(8), TreeNode(2)))
```
calling your function `postorder_traversal(root)` should `return [6, 7, 4, 8, 2, 3, 1]`. If the tree is empty, your function should `return` an empty list.

# Solution
```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right


def postorder_traversal(root):
    return postorder_traversal(root.left) + postorder_traversal(root.right) + [root.val] if root else []
    pass
```

# Tests
```python
import unittest
from solution import TreeNode, postorder_traversal

class TestPostorderTraversal(unittest.TestCase):
    def test1(self):
        root = TreeNode(1, TreeNode(4, TreeNode(6), TreeNode(7)), TreeNode(3, TreeNode(8), TreeNode(2)))
        self.assertEqual(postorder_traversal(root), [6, 7, 4, 8, 2, 3, 1])
 
    def test2(self):
        root = TreeNode(1)
        self.assertEqual(postorder_traversal(root), [1])

    def test3(self):
        root = TreeNode(2, TreeNode(1), TreeNode(3))
        self.assertEqual(postorder_traversal(root), [1, 3, 2])

    def test4(self):
        root = TreeNode(5, TreeNode(3, TreeNode(2), TreeNode(4)), TreeNode(7, TreeNode(6), TreeNode(8)))
        self.assertEqual(postorder_traversal(root), [2, 4, 3, 6, 8, 7, 5])

    def test5(self):
        root = TreeNode(10, TreeNode(5, TreeNode (3), TreeNode(7)), TreeNode(15, TreeNode(12), TreeNode(20)))
        self.assertEqual(postorder_traversal(root), [3, 7, 5, 12, 20, 15, 10])

    def test6(self):
        root = TreeNode(-10, TreeNode(-15), TreeNode(-5, TreeNode(-7), TreeNode(-3)))
        self.assertEqual(postorder_traversal(root), [-15, -7, -3, -5, -10])

    def test7(self):
        root = TreeNode(1, None, TreeNode(2, None, TreeNode(3, None, TreeNode(4, None, TreeNode(5)))))
        self.assertEqual(postorder_traversal(root), [5, 4, 3, 2, 1])

    def test8(self):
        root = TreeNode(1, TreeNode(2, TreeNode(4, TreeNode(8)), TreeNode(5)), TreeNode(3, TreeNode(6), TreeNode(7)))
        self.assertEqual(postorder_traversal(root), [8, 4, 5, 2, 6, 7, 3, 1])

    def test9(self):
        root = None
        self.assertEqual(postorder_traversal(root), [])

if __name__ == '__main__':
    unittest.main()
```
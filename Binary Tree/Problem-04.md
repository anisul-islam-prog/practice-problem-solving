# Problem Statement
Cosmo
Just now
Read message aloud
Given a binary tree, write a function in Python to reverse the given binary tree. This means that for every node in the binary tree, you have to swap its left and right child nodes.

For example, for the following binary tree

```python
# Original tree
#      4
#     / \
#    2   5
#   / \
#  1   3
```
the output should be

```python
# After reversing
#      4
#     / \
#    5   2
#       / \
#      3   1
```
The time complexity for your function should be linear, i.e., _`O(n)`_, where `n` is the number of nodes in the binary tree.

# Solution
```python
class TreeNode:
    def __init__(self, value=0, left=None, right=None):
        self.value = value
        self.left = left
        self.right = right


def reverse_tree(root):
    # Base case
    if not root:
        return
    # Swap
    root.left, root.right = root.right, root.left
    reverse_tree(root.left)
    reverse_tree(root.right)
    return root
    pass
```

# Tests
```python
import unittest
from solution import TreeNode, reverse_tree

def construct_tree(values, index=0):
    if index < len(values):
        if values[index] is not None:
            node = TreeNode(value=values[index])
            node.left = construct_tree(values, 2*index + 1)
            node.right = construct_tree(values, 2*index + 2)
            return node
    return None

def inorder_traversal(root):
    return inorder_traversal(root.left) + [root.value] + inorder_traversal(root.right) if root else []

class TestReverseTree(unittest.TestCase):

    def test_case_1(self):
        tree = construct_tree([1, 2, 5, 3, 4])
        self.assertEqual(inorder_traversal(reverse_tree(tree)), [5, 1, 4, 2, 3])

    def test_case_2(self):
        tree = construct_tree([7, 3, 5, 2, 6, 9])
        self.assertEqual(inorder_traversal(reverse_tree(tree)), [5, 9, 7, 6, 3, 2])

    def test_case_3(self):
        tree = construct_tree([1])
        self.assertEqual(inorder_traversal(reverse_tree(tree)), [1])

    def test_case_4(self):
        tree = construct_tree([3, 9])
        self.assertEqual(inorder_traversal(reverse_tree(tree)), [3, 9])

    def test_case_5(self):
        tree = construct_tree([-7, -8, -5])
        self.assertEqual(inorder_traversal(reverse_tree(tree)), [-5, -7, -8])

    def test_case_6(self):
        tree = construct_tree([0])
        self.assertEqual(inorder_traversal(reverse_tree(tree)), [0])

    def test_case_7(self):
        tree = construct_tree([4, None, 2, None, 1])
        self.assertEqual(inorder_traversal(reverse_tree(tree)), [2, 4])

    def test_case_8(self):
        tree = construct_tree([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15])
        self.assertEqual(inorder_traversal(reverse_tree(tree)), [15, 7, 14, 3, 13, 6, 12, 1, 11, 5, 10, 2, 9, 4, 8])

    def test_case_9(self):
        tree = construct_tree([15, 14, 13, 12, 11, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1])
        self.assertEqual(inorder_traversal(reverse_tree(tree)), [1, 9, 2, 13, 3, 10, 4, 15, 5, 11, 6, 14, 7, 12, 8])

if __name__ == '__main__':
    unittest.main()
```
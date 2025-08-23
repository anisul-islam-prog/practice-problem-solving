# Problem Statement
Your task is to write a function, `remove_duplicates(head)`. This function takes the head of a linked list as a parameter. The function should remove all duplicate nodes from an unsorted linked list and return the head of the updated linked list. The order of the remaining nodes in the list should be the same as in the original.

In other words, if a linked list has duplicate values, all occurrences of such values, except for their first occurrence, must be deleted from the list. For instance, for the given linked list `1 -> 3 -> 2 -> 3 -> 2 -> 3 -> 4 -> 5 -> 5 -> 5` you should return `1 -> 3 -> 2 -> 4 -> 5`

# Solution
```python
def remove_duplicates(head):
    if not head or not head.next:
        return head
    uniqueSet = set()
    dummy = ListNode(0)
    dummy.next = head
    current = head
    prev = dummy
    while current:
        if current.val in uniqueSet:
            prev.next = current.next
        else:
            uniqueSet.add(current.val)
            prev = current
        current = current.next
    return dummy.next
    pass
```

# Tests
```python
import unittest
from solution import ListNode, remove_duplicates

# function to convert a linked list to Python list
def linked_list_to_list(node):
    result = []
    while node is not None:
        result.append(node.val)
        node = node.next
    return result

# function to create and return a linked list from a Python list
def get_linked_list(values):
    head = ListNode(values[0])
    current_node = head
    for val in values[1:]:
        current_node.next = ListNode(val)
        current_node = current_node.next
    return head

class SolutionTests(unittest.TestCase):
    def compare(self, arr1, arr2):
        self.assertEqual(linked_list_to_list(remove_duplicates(get_linked_list(arr1))), arr2)

    def test1(self):
        self.compare([1, 2, 2, 3, 3, 4, 5, 5, 5], [1, 2, 3, 4, 5])

    def test2(self):
        self.compare([1, 1, 1, 1], [1])

    def test3(self):
        self.compare([-1, -1, 2, 2, 3, 3], [-1, 2, 3])

    def test4(self):
        self.compare([-5, -5, -5, -4, -4, -4, -3, -3], [-5, -4, -3])

    def test5(self):
        self.compare([1000, 100, 10, 1, 1, 10, 100, 1000], [1000, 100, 10, 1])

    def test6(self):
        self.compare([34, 35, 35, 36, 37, 37, 37, 38, 39, 39], [34, 35, 36, 37, 38, 39])

    def test7(self):
        self.compare([0, 0, 0], [0])

    def test8(self):
        self.compare([100, 100, 200, 200, 300, 300, 400, 400], [100, 200, 300, 400])

    def test9(self):
        self.compare([1, -1, 2, -2, 3, -3, 4, -4, 5, -5], [1, -1, 2, -2, 3, -3, 4, -4, 5, -5])

    def test10(self):
        self.compare([10, 20, 10, 30, 20, 40, 30], [10, 20, 30, 40])

    def test11(self):
        self.compare([5, 15, 25, 5, 35, 25, 45], [5, 15, 25, 35, 45])

    def test12(self):
        self.compare([7, 8, 9, 8, 10, 9, 11], [7, 8, 9, 10, 11])

    def test13(self):
        self.compare([1, 4, 5, 4, 1, 6, 5], [1, 4, 5, 6])

    def test14(self):
        self.compare([0, 2, 4, 2, 6, 4, 8, 6], [0, 2, 4, 6, 8])

    def test15(self):
        self.compare([9, 7, 5, 3, 7, 1, 9], [9, 7, 5, 3, 1])

    def test16(self):
        self.compare([100, 200, 300, 100, 400, 300, 500, 200], [100, 200, 300, 400, 500])

    def test17(self):
        self.compare([50, 60, 70, 80, 90, 60, 70], [50, 60, 70, 80, 90])

    def test18(self):
        self.compare([21, 31, 41, 21, 51, 31, 61, 41], [21, 31, 41, 51, 61])

    def test19(self):
        self.compare([13, 23, 33, 13, 43, 23, 53], [13, 23, 33, 43, 53])

    def test20(self):
        self.compare([89, 78, 89, 67, 56, 45, 67], [89, 78, 67, 56, 45])

if __name__ == '__main__':
    unittest.main()
```
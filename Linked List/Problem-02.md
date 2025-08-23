# Problem Statement
You are given a singly linked list and two indices, `start` and `end` (both indices are 0-based). Write a Python function `swap_linked_list_nodes(head: ListNode, start: int, end: int) -> ListNode` that swaps the nodes of the linked list at these two provided indices. The function should return the head node of the modified linked list. When swapping, you should only change the next property of a node, not the actual node values. It is guaranteed that `start <= end`.

For example, consider the linked list `17 -> 2 -> 13 -> 4 -> 51 -> 22 -> 33 -> 84 -> 5` and you are given `start = 2` and `end = 6`. The resulting linked list after swapping nodes at indices `2` and `6` would be:
```text
17 -> 2 -> 33 -> 4 -> 51 -> 22 -> 13 -> 84 -> 5 
# 13 and 33 swapped
```
The expected time complexity of your solution should be _`O(n)`_, where `n` is the length of the linked list.

# Solution
```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val     # Holds the value or data of the node
        self.next = next  # Points to the next node in the linked list; default is None


def swap_linked_list_nodes(head, start, end):
    
    # No need to swap if indices are the same
    if start == end:
        return head
    
    # Copy the head in dummy to use later
    dummy = ListNode(0)
    dummy.next = head
    
    # Step 1: Locate nodes and their previous nodes
    startNode = endNode = None
    prevStart = prevEnd = None
    
    i = 0
    current = head
    while current:
        if i == start - 1:
            prevStart = current
        if i == start:
            startNode = current
        if i == end - 1:
            prevEnd = current
        if i == end:
            endNode = current
            break
        current = current.next
        i += 1
    # Step 2: Handle adjacent case
    if startNode.next == endNode:
        prevStart.next = endNode
        startNode.next = endNode.next
        endNode.next = startNode
    else:
        # Step 5: if start is the head
        if prevStart:
            prevStart.next = endNode
        else:
            dummy.next = endNode
        if prevEnd:
            prevEnd.next = startNode
        # Step 4: General case
        startNode.next, endNode.next = endNode.next, startNode.next
        
    return dummy.next
    
    pass
```

# Tests
```python
import unittest
from solution import swap_linked_list_nodes, ListNode

def create_linked_list_from_array(arr):
    dummy = current = ListNode(0)
    for val in arr:
        current.next = ListNode(val)
        current = current.next
    return dummy.next

def extract_linked_list_values(head):
    values = []
    while head is not None:
        values.append(head.val)
        head = head.next
    return values

class SwapLinkedListNodesTest(unittest.TestCase):
    def test_1(self):
        head = create_linked_list_from_array([1, 2, 3, 4, 5])
        self.assertEqual(extract_linked_list_values(swap_linked_list_nodes(head, 0, 4)), [5, 2, 3, 4, 1])

    def test_2(self):
        head = create_linked_list_from_array([5, 4, 3, 2, 1])
        self.assertEqual(extract_linked_list_values(swap_linked_list_nodes(head, 1, 3)), [5, 2, 3, 4, 1])

    def test_3(self):
        head = create_linked_list_from_array([1, 2, 3, 4, 5, 6, 7, 8, 9])
        self.assertEqual(extract_linked_list_values(swap_linked_list_nodes(head, 0, 8)), [9, 2, 3, 4, 5, 6, 7, 8, 1])

    def test_4(self):
        head = create_linked_list_from_array([1, 2, 3, 4, 5, 6, 7, 8, 9])
        self.assertEqual(extract_linked_list_values(swap_linked_list_nodes(head, 3, 5)), [1, 2, 3, 6, 5, 4, 7, 8, 9])

    def test_5(self):
        head = create_linked_list_from_array([1, 2, 3])
        self.assertEqual(extract_linked_list_values(swap_linked_list_nodes(head, 0, 2)), [3, 2, 1])

    def test_6(self):
        head = create_linked_list_from_array([1, 2, 3])
        self.assertEqual(extract_linked_list_values(swap_linked_list_nodes(head, 1, 1)), [1, 2, 3])

    def test_7(self):
        head = create_linked_list_from_array([-9, -8, -7, -6, -5, -4, -3, -2, -1, 0])
        self.assertEqual(extract_linked_list_values(swap_linked_list_nodes(head, 0, 9)), [0, -8, -7, -6, -5, -4, -3, -2, -1, -9])

    def test_8(self):
        head = create_linked_list_from_array([2])
        self.assertEqual(extract_linked_list_values(swap_linked_list_nodes(head, 0, 0)), [2])

    def test_9(self):
        head = create_linked_list_from_array([-5, 0, 5])
        self.assertEqual(extract_linked_list_values(swap_linked_list_nodes(head, 0, 2)), [5, 0, -5])

    def test_10(self):
        head = create_linked_list_from_array(list(range(1, 101)))
        self.assertEqual(extract_linked_list_values(swap_linked_list_nodes(head, 0, 99)), [100] + list(range(2, 100)) + [1])

    def test_11(self):
        head = create_linked_list_from_array(list(range(1, 101)))
        self.assertEqual(extract_linked_list_values(swap_linked_list_nodes(head, 50, 50)), list(range(1, 101)))



if __name__ == '__main__':
    unittest.main()
```
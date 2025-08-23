# Problem Statement
You are given a singly linked list and an integer `k`. Your task is to write a Python function, `rotate_right(linked_list, k)`, which rotates the linked list to the right by `k` places. Note that `k` might be `0` or greater than the length of the linked list.

Your function should take the last `k` nodes from the end of the list and move them to the start of the list, maintaining their original order. After the rotation, return the head of the resulting linked list.

For instance, if the linked list is `1 -> 2 -> 3 -> 4 -> 5` and `k = 2`, after the rotation, it should become `4 -> 5 -> 1 -> 2 -> 3`.

The expected time complexity for your solution is *`O(n)`*.

# Solution
```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next


def rotate_right(head: ListNode, k: int) -> ListNode:
    if not head or not head.next or k == 0:
        return head
    dummy = ListNode(0)
    dummy.next = head
    
    # Step-01: Find length of linkedlist
    length = 1
    tail = head
    
    while tail.next:
        length += 1
        tail = tail.next
    
    # Step-02: Normalize k
    k = k % length
    if k == length or k == 0:
        return head
    
    # Step-03: Find the new head
    new_tail = head
    for _ in range(length - k - 1):
        new_tail = new_tail.next
    
    # Step-04: Reconnect the link of tail to head
    new_head = new_tail.next
    new_tail.next = None
    tail.next = head
    
    return new_head
    
    pass
```

# Tests
```python
import unittest
from solution import ListNode, rotate_right


class Tests(unittest.TestCase):
    
    # Helper function to construct ListNode objects from list.
    def construct_list_node(self, lst):
        current_node = ListNode(lst[-1])
        for val in lst[-2::-1]:
            current_node = ListNode(val, current_node)
        return current_node

    # Helper function to convert ListNode objects to list.
    def convert_to_list(self, head):
        arr = []
        current = head
        while current:
            arr.append(current.val)
            current = current.next
        return arr

    def test1(self):
        head = self.construct_list_node([1, 2, 3, 4, 5])
        result_head = rotate_right(head, 2)
        self.assertEqual(self.convert_to_list(result_head), [4, 5, 1, 2, 3])

    def test2(self):
        head = self.construct_list_node([1])
        result_head = rotate_right(head, 0)
        self.assertEqual(self.convert_to_list(result_head), [1])

    def test3(self):
        head = self.construct_list_node([1, 2])
        result_head = rotate_right(head, 1)
        self.assertEqual(self.convert_to_list(result_head), [2, 1])

    def test4(self):
        head = self.construct_list_node([1, 2, 3])
        result_head = rotate_right(head, 2)
        self.assertEqual(self.convert_to_list(result_head), [2, 3, 1])
        
    def test5(self):
        head = self.construct_list_node([1, 2, 3, 4])
        result_head = rotate_right(head, 3)
        self.assertEqual(self.convert_to_list(result_head), [2, 3, 4, 1])

    def test6(self):
        head = self.construct_list_node([1, 2, 3, 4, 5])
        result_head = rotate_right(head, 4)
        self.assertEqual(self.convert_to_list(result_head), [2, 3, 4, 5, 1])

    def test7(self):
        head = self.construct_list_node([1, 2, 3, 4, 5])
        result_head = rotate_right(head, 5)
        self.assertEqual(self.convert_to_list(result_head), [1, 2, 3, 4, 5])

    def test8(self):
        head = self.construct_list_node([1, 2, 3, 4, 5])
        result_head = rotate_right(head, 6)
        self.assertEqual(self.convert_to_list(result_head), [5, 1, 2, 3, 4])

    def test9(self):
        head = self.construct_list_node([1, 2, 3, 4, 5])
        result_head = rotate_right(head, 7)
        self.assertEqual(self.convert_to_list(result_head), [4, 5, 1, 2, 3])

    def test10(self):
        head = self.construct_list_node([1, 2, 3, 4, 5])
        result_head = rotate_right(head, 1001)
        self.assertEqual(self.convert_to_list(result_head), [5, 1, 2, 3, 4])

    def test11(self):
        head = self.construct_list_node([1])
        result_head = rotate_right(head, 999)
        self.assertEqual(self.convert_to_list(result_head), [1])
        
    def test12(self):
        head = self.construct_list_node([1, 2])
        result_head = rotate_right(head, 1002)
        self.assertEqual(self.convert_to_list(result_head), [1, 2])

    def test13(self):
        head = self.construct_list_node([1, 1, 1, 1, 2, 2, 2])
        result_head = rotate_right(head, 3)
        self.assertEqual(self.convert_to_list(result_head), [2, 2, 2, 1, 1, 1, 1])

    def test14(self):
        head = self.construct_list_node([5, 5, 5, 4, 4, 4])
        result_head = rotate_right(head, 2)
        self.assertEqual(self.convert_to_list(result_head), [4, 4, 5, 5, 5, 4])


if __name__ == '__main__':
    unittest.main()
```
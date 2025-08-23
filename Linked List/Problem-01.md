# Problem Statement
You are given a singly linked list, and your task is to determine whether the linked list is a palindrome or not. A linked list is a palindrome if it reads the same forward and backward.

Implement a function `is_palindrome(head)` that takes a `head` node of a singly linked list (which is the first node in the list) and returns `True` if the linked list is a palindrome and `False` otherwise. The expected time complexity for your solution is *`O(n)`*.

For example, a linked list with the following nodes: `1 -> 2 -> 3 -> 2 -> 1` would return True as it is a palindrome; however, for `1 -> 2 -> 3 -> 4`, the function would return False because it doesn't read the same in both directions.

# Solution
```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next


def is_palindrome(head):
    
    if not head or not head.next:
        return True
        
    # Step 1: Find the middle using two pointers one fast and other slow
    # when the fast reaches the end the slow will be at the middle
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next

    # Step 2: Reverse the second half
    prev = None
    curr = slow
    while curr:
        next_node = curr.next
        curr.next = prev
        prev = curr
        curr = next_node

    # Step 3: Compare both halves
    left = head
    right = prev
    while right:
        if left.val != right.val:
            return False
        left = left.next
        right = right.next

    return True
    pass
```

# Tests
```python
import unittest
from solution import ListNode, is_palindrome

class TestIsPalindrome(unittest.TestCase):
    def test1(self):
        head = ListNode(1, ListNode(2, ListNode(2, ListNode(1))))
        self.assertEqual(is_palindrome(head), True)

    def test2(self):
        head = ListNode(1, ListNode(2, ListNode(3, ListNode(1))))
        self.assertEqual(is_palindrome(head), False)

    def test3(self):
        head = ListNode(1)
        self.assertEqual(is_palindrome(head), True)

    def test4(self):
        head = ListNode(1, ListNode(2, ListNode(3, ListNode(2, ListNode(1)))))
        self.assertEqual(is_palindrome(head), True)

    def test5(self):
        head = ListNode(-1, ListNode(-2, ListNode(-2, ListNode(-1))))
        self.assertEqual(is_palindrome(head), True)

    def test6(self):
        head = ListNode(1, ListNode(2, ListNode(3, ListNode(4, ListNode(5)))))
        self.assertEqual(is_palindrome(head), False)

    def test7(self):
        head = ListNode(5, ListNode(4, ListNode(3, ListNode(2, ListNode(1)))))
        self.assertEqual(is_palindrome(head), False)

    def test8(self):
        head = ListNode(1, ListNode(1, ListNode(1, ListNode(1, ListNode(1)))))
        self.assertEqual(is_palindrome(head), True)

    def test9(self):
        head = ListNode(-1, ListNode(-1, ListNode(-1, ListNode(-1, ListNode(-1)))))
        self.assertEqual(is_palindrome(head), True)

    def test10(self):
        head = ListNode(1, ListNode(10, ListNode(100, ListNode(10, ListNode(1)))))
        self.assertEqual(is_palindrome(head), True)

    def test11(self):
        head = ListNode(10)
        self.assertEqual(is_palindrome(head), True)

    def test12(self):
        head = ListNode(10, ListNode(11))
        self.assertEqual(is_palindrome(head), False)


if __name__ == '__main__':
    unittest.main()
```
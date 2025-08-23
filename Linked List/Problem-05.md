# Problem Statement
You are given a linked list, and you are required to detect if a cycle exists in the linked list. A linked list is said to contain a cycle if a node's next pointer points back to one of the previous nodes in the list. Given the head of the linked list `head`, return `True` if the linked list contains a cycle and `False` otherwise.

You need to solve this using _`O(1)`_ of additional memory.

# Solution
To detect a cycle in a singly linked list using O(1) additional memory, we use **Floyd’s Cycle Detection Algorithm**, also known as the **Tortoise and Hare** approach.

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next


def hasCycle(head):
    slow = fast = head
    
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next

        if slow == fast:
            return True

    return False
    pass
```

# Tests
```python
import unittest
from solution import ListNode, hasCycle

class SolutionTests(unittest.TestCase):
    def test1(self):
        head1 = ListNode(1)
        self.assertEqual(hasCycle(head1), False)

    def test2(self):
        head2 = ListNode(1, ListNode(2, ListNode(3)))
        self.assertEqual(hasCycle(head2), False)

    def test3(self):
        head3 = ListNode(1)
        head3.next = ListNode(2)
        head3.next.next = ListNode(3)
        head3.next.next.next = head3
        self.assertEqual(hasCycle(head3), True)
    
    def test4(self):
        head4 = ListNode(1, ListNode(2, ListNode(2, ListNode(1))))
        self.assertEqual(hasCycle(head4), False)
    
    def test5(self):
        head5 = ListNode(1)
        head5.next = ListNode(2)
        head5.next.next = ListNode(3)
        head5.next.next.next = ListNode(4)
        head5.next.next.next.next = ListNode(5)
        head5.next.next.next.next.next = head5.next.next
        self.assertEqual(hasCycle(head5), True)
    
    def test6(self):
        nodes = [ListNode(i) for i in range(1, 100001)]
        for i in range(100000):
            nodes[i].next = nodes[(i+1) % 100000]
        head6 = nodes[0]
        self.assertEqual(hasCycle(head6), True)


if __name__ == '__main__':
    unittest.main()
```
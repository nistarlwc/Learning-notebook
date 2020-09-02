# 142. Linked List Cycle II

Given a linked list, return the node where the cycle begins. If there is no cycle, return null.  
给定链表，返回循环开始的节点。 如果没有循环，则返回null。

To represent a cycle in the given linked list, we use an integer pos which represents the position (0-indexed) in the linked list where tail connects to. If pos is -1, then there is no cycle in the linked list.
为了表示给定链表中的循环，我们使用整数pos来表示tail连接到的链表中的位置（0索引）。 如果pos为-1，则链表中没有循环。

Note: Do not modify the linked list.
注意：请勿修改链接列表。

链表是否有环相关[博客](https://www.cnblogs.com/dancingrain/p/3405197.html)

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def detectCycle(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if head == None or head.next == None:
            return None
        slow = fast = head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            if slow == fast:
                break
        if slow == fast:
            slow = head
            while slow != fast:
                slow = slow.next
                fast = fast.next
            return slow
        return None
```
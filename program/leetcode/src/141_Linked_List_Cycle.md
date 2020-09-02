# 141. Linked List Cycle

Given a linked list, determine if it has a cycle in it.  
给定一个链表，确定它是否有一个循环。

To **represent** a cycle in the given linked list, we use an integer pos which represents the position (0-indexed) in the linked list where tail connects to. If pos is -1, then there is no cycle in the linked list.  
为了**表示**给定链表中的循环，我们使用整数pos来表示tail连接到的链表中的位置（0索引）。 如果pos为-1，则链表中没有循环。
 
 
>Example 1:  
>Input: head = [3,2,0,-4], pos = 1  
>Output: true   
>Explanation: There is a cycle in the linked list, where tail connects to the second node.  
![Example 1](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)  

>Example 2:  
>Input: head = [1,2], pos = 0  
>Output: true  
>Explanation: There is a cycle in the linked list, where tail connects to the first node.  
![Example 2](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png)  

>Example 3:  
>Input: head = [1], pos = -1  
>Output: false  
>Explanation: There is no cycle in the linked list.  
![Example 3](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test3.png)  

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

# 使用快慢2个指针，慢的走一步，快的走两步，如果两个指针可以汇聚，则链表为循环列表
class Solution(object):
    def hasCycle(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """    
        if head == None or head.next == None:
            return False
        slow = fast = head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            if slow == fast:
                return True
        return False
```
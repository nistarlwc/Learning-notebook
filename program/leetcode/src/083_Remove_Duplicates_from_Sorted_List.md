# 83. Remove Duplicates from Sorted List

Given a sorted linked list, delete all **duplicates** such that each element appear only once.  
给定已排序的链接列表，删除所有**重复项**，使每个元素只出现一次。

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def deleteDuplicates(self, head: ListNode) -> ListNode:
        list = ListNode(None)
        list.next = head
        current = list
        hash = {}  #建立一个哈希表
        while current.next:
            if not current.val in hash:  #哈希表中没有就先保存至哈希
                hash[current.val] = current.val
                
            if current.next.val in hash: #下一个链表的值在哈希表中要删除
                current.next = current.next.next
            else:
                current = current.next
                
        return list.next
```
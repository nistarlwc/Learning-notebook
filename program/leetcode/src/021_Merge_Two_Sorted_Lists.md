# 21. Merge Two Sorted Lists

Merge two sorted linked lists and return it as a new list.   
合并两个已排序的链接列表并将其作为新列表返回。  
The new list should be made by **splicing** together the nodes of the first two lists.  
新列表应该通过**拼接**前两个列表的节点来完成。  

>Example:   
>Input: 1->2->4, 1->3->4   
>Output: 1->1->2->3->4->4   

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        if not l1 and not l2: return
        result = ListNode(0)
        l = result
        while l1 and l2:
            if l1.val < l2.val:
                l.next = l1
                l1 = l1.next
            else:
                l.next = l2
                l2 = l2.next
            #融合后链表的下一位,当前位置刚刚赋值
            l = l.next
        #把剩余的链表排在后面
        l.next = l1 or l2  
        #返回融合后链表从第二个对象开始，第一个对象是自己创建的ListNode(0)
        return result.next
```
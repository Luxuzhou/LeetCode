# **题目地址**
https://leetcode-cn.com/problems/merge-two-sorted-lists/
# **题目描述**
```
将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

示例：
输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        res = ListNode(None)
        node = res
        while l1 and l2:
            if l1.val < l2.val:
                node.next, l1 = l1, l1.next
            else:
                node.next, l2 = l2, l2.next
            node = node.next
        if l1:
            node.next = l1
        else:
            node.next = l2
        return res.next
```
C++ Code:
```
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode dummy = ListNode(-1);  
        ListNode* prev = &dummy;   
        while(l1 != NULL && l2 != NULL) {
            if(l1 -> val <= l2 -> val) {
                prev -> next = l1;
                l1 = l1 -> next;
            } else {
                prev -> next = l2;
                l2 = l2 -> next;
            }
            prev = prev -> next;
        }
        prev -> next = l1 != NULL ? l1 : l2;
        return dummy.next;
    }
};
```

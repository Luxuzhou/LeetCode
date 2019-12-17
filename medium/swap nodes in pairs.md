# **题目地址**
https://leetcode-cn.com/problems/swap-nodes-in-pairs/
# **题目描述**
```
给定一个链表，两两交换其中相邻的节点，并返回交换后的链表。
你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。

示例:
给定 1->2->3->4, 你应该返回 2->1->4->3.
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def swapPairs(self, head: ListNode) -> ListNode:
        thead = ListNode(-1)
        thead.next = head
        c = thead
        while c.next and c.next.next:
            a, b = c.next, c.next.next
            c.next, a.next = b, b.next
            b.next = a
            c = c.next.next
        return thead.next
```
C++ Code:
```
class Solution {
public:
    ListNode* swapPairs(ListNode* head) {
        ListNode* dummy = new ListNode(0);
        ListNode* pre = dummy;
        dummy -> next = head;
        ListNode* cur = head;
        while ( cur != NULL) {
            ListNode* next = cur->next;  
            if (next == NULL)
                break;
            pre -> next = next;
            cur -> next = next -> next;
            next -> next = cur;
            pre = cur;
            cur = cur -> next; 
        }
        return dummy -> next;
    }
};
```

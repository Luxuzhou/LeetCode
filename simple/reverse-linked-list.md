# **题目地址**
https://leetcode-cn.com/problems/reverse-linked-list/
# **题目描述**
```
反转一个单链表。

示例:
输入: 1->2->3->4->5->NULL
输出: 5->4->3->2->1->NULL
进阶:
你可以迭代或递归地反转链表。你能否用两种方法解决这道题？
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        new_head = None
        while head:     
            tmp = head.next
            head.next = new_head
            new_head = head
            head = tmp
        return new_head
```
C++ Code:
```
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        if (!head)
            return NULL;
        ListNode *curr = head -> next, *p;
        head -> next = NULL;
        while (curr) {
            p = curr -> next;
            curr -> next = head;
            head = curr;
            curr = p;
        }
        return head;
    }
};
```

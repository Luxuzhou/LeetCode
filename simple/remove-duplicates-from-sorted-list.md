# **题目地址**
https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list/
# **题目描述**
```
给定一个排序链表，删除所有重复的元素，使得每个元素只出现一次。

示例 1:
输入: 1->1->2
输出: 1->2

示例 2:
输入: 1->1->2->3->3
输出: 1->2->3
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def deleteDuplicates(self, head: ListNode) -> ListNode:
        dummy_head = ListNode(None)
        dummy_head.next = head
        pre = dummy_head
        cur = head
        while cur:
            if pre and cur.val == pre.val:
                pre.next = cur.next
                cur.next = None
                cur = pre.next
                continue

            pre = cur
            cur = cur.next
        return dummy_head.next
```
C++ Code:
```
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        if (!head || !head->next)
            return head;
        head -> next = deleteDuplicates(head -> next);
        if (head -> val == head -> next -> val) head = head -> next;
        return head;
    }
};
```

# **题目地址**
https://leetcode-cn.com/problems/partition-list/
# **题目描述**
```
给定一个链表和一个特定值 x，对链表进行分隔，使得所有小于 x 的节点都在大于或等于 x 的节点之前。
你应当保留两个分区中每个节点的初始相对位置。

示例:
输入: head = 1->4->3->2->5->2, x = 3
输出: 1->2->2->4->3->5
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def partition(self, head: ListNode, x: int) -> ListNode:
        dummy1 = ListNode(-1)
        dummy2 = ListNode(-1)
        p1 = dummy1
        p2 = dummy2
        while head:
            if head.val < x:
                p1.next = head
                p1 = p1.next
            else:
                p2.next = head
                p2 = p2.next
            head = head.next
        p1.next = dummy2.next
        p2.next = None
        return dummy1.next
```
C++ Code:
```
class Solution {
public:
    ListNode* partition(ListNode* head, int x) {
        ListNode* min = new ListNode(0);
        ListNode* max = new ListNode(0);
        ListNode* m = min;
        ListNode* f = max;
        while (head) {
            ListNode* k = new ListNode(head -> val);
            if (head -> val < x) {
                min -> next = k;
                min = min -> next;
            }
            else {
                max -> next = k;
                max = max -> next;
            }
            head = head -> next;
        }
        min -> next = f -> next;
        return m -> next;
    }
};
```

# **题目地址**
https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/
# **题目描述**
```
给定一个链表，删除链表的倒数第 n 个节点，并且返回链表的头结点。

示例：
给定一个链表: 1->2->3->4->5, 和 n = 2.
当删除了倒数第二个节点后，链表变为 1->2->3->5.

说明：
给定的 n 保证是有效的。

进阶：
你能尝试使用一趟扫描实现吗？
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
        if not head: return 
        dummy = ListNode(0)
        dummy.next = head
        fast = dummy
        while n:
            fast = fast.next
            n -= 1
        slow = dummy
        while fast and fast.next:
            fast = fast.next
            slow = slow.next
        slow.next = slow.next.next
        return dummy.next
```
C++ Code:
```
class Solution{
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode* front = head;
        ListNode* rear = head;
        if (head -> next == NULL) return NULL;
        while (n-- >= 0) {
            if (rear == NULL) return head -> next;
            rear = rear -> next;
        }
        while (rear) {
            rear = rear -> next;
            front = front -> next;
        }
        front -> next = front -> next -> next;
        return head;
    }
};
```

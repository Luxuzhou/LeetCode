# **题目地址**
https://leetcode-cn.com/problems/reverse-nodes-in-k-group/
# **题目描述**
```
给你一个链表，每 k 个节点一组进行翻转，请你返回翻转后的链表。
k 是一个正整数，它的值小于或等于链表的长度。
如果节点总数不是 k 的整数倍，那么请将最后剩余的节点保持原有顺序。

示例 :
给定这个链表：1->2->3->4->5
当 k = 2 时，应当返回: 2->1->4->3->5
当 k = 3 时，应当返回: 3->2->1->4->5

说明 :
你的算法只能使用常数的额外空间。
你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def reverseKGroup(self, head: ListNode, k: int) -> ListNode:
        dummy = ListNode(0)
        p = dummy
        while True:
            count = k 
            stack = []
            tmp = head
            while count and tmp:
                stack.append(tmp)
                tmp = tmp.next
                count -= 1
            if count : 
                p.next = head
                break
            while stack:
                p.next = stack.pop()
                p = p.next
            p.next = tmp
            head = tmp
        return dummy.next
```
C++ Code:
```
class Solution {
public:
    ListNode* reverseKGroup(ListNode* head, int k) {
        int d = 0;
        auto node = head;
        while (node != NULL) {
            if (++d >= k) break;
            node = node->next;
        }
        if (d < k) return head;
        ListNode* prev = NULL;
        ListNode* curr = head;
        for (int i = 0; i < k; ++i) {
            auto node = curr->next;
            curr->next = prev;
            prev = curr;
            curr = node;
        }
        head->next = reverseKGroup(curr, k);
        return prev;
    }
};
```

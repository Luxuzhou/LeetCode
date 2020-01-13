# **题目地址**
https://leetcode-cn.com/problems/rotate-list/
# **题目描述**
```
给定一个链表，旋转链表，将链表每个节点向右移动 k 个位置，其中 k 是非负数。

示例 1:
输入: 1->2->3->4->5->NULL, k = 2
输出: 4->5->1->2->3->NULL
解释:
向右旋转 1 步: 5->1->2->3->4->NULL
向右旋转 2 步: 4->5->1->2->3->NULL

示例 2:
输入: 0->1->2->NULL, k = 4
输出: 2->0->1->NULL
解释:
向右旋转 1 步: 2->0->1->NULL
向右旋转 2 步: 1->2->0->NULL
向右旋转 3 步: 0->1->2->NULL
向右旋转 4 步: 2->0->1->NULL
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def rotateRight(self, head: ListNode, k: int) -> ListNode:
        l = []
        while head: l[len(l):], head = [head], head.next
        if l: l[-1].next, l[-1 - k % len(l)].next = l[0], None
        return l[-k % len(l)] if l else None
```
C++ Code:
```
class Solution {
public:
    ListNode* rotateRight(ListNode* head, int k) {
        ListNode* pst = head;
        ListNode* last = NULL;
        int count = 0;
        while (pst != NULL) {
            ++count;
            last = pst;
            pst = pst -> next;
        }
        if (count == 0) {
            return head;
        }
        int actual = k % count;
        last -> next = head;
        pst = head;
        for (int i = 0; i < count - actual - 1; ++i) {
            pst = pst -> next;
        }
        head = pst -> next;
        pst -> next = NULL;
        return head;
    }
};
```

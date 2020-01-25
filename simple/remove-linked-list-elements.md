# **题目地址**
https://leetcode-cn.com/problems/remove-linked-list-elements/
# **题目描述**
```
删除链表中等于给定值 val 的所有节点。

示例:
输入: 1->2->6->3->4->5->6, val = 6
输出: 1->2->3->4->5
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def removeElements(self, head: ListNode, val: int) -> ListNode:
        if not head: return 
        head.next = self.removeElements(head.next, val)
        return head.next if head.val == val else head
```
C++ Code:
```
class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        if (head == NULL) return NULL;
        ListNode* H = new ListNode(-1);
        H -> next = head;
        ListNode* p = H;
        ListNode* s = NULL;
        while (p -> next != NULL) {
            if (p -> next -> val == val) {
                s = p -> next;
                p -> next = p -> next -> next;
                delete s;
            }else
                p = p -> next;
        }
        return H -> next;
    }
};
```

# **题目地址**
https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list-ii/
# **题目描述**
```
给定一个排序链表，删除所有含有重复数字的节点，只保留原始链表中没有重复出现的数字。

示例 1:
输入: 1->2->3->3->4->4->5
输出: 1->2->5

示例 2:
输入: 1->1->1->2->3
输出: 2->3
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def deleteDuplicates(self, head: ListNode) -> ListNode:
        thead = ListNode('a')
        thead.next = head
        pre, cur = None, thead
        while cur:
            pre = cur
            cur = cur.next
            while cur and cur.next and cur.next.val == cur.val:
                t = cur.val
                while cur and cur.val == t:
                    cur = cur.next
                pre.next = cur
        return thead.next
```
C++ Code:
```
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        ListNode* preHead = new ListNode(0);
        preHead -> next = head;
        ListNode* cur = preHead;
        int delVal;
        while (cur -> next != NULL) {
            if(cur -> next -> next != NULL && cur -> next -> val == cur -> next -> next -> val) {
            delVal = cur -> next -> val;
            while (cur -> next != NULL && cur -> next -> val == delVal) {
                ListNode* delNode = cur -> next;
                cur -> next = delNode -> next;
                delete delNode;
            }
            }
            else {
                cur = cur -> next;
            }
        }
        ListNode* newHead = preHead -> next;
        delete preHead;
        return newHead;
    }
};
```

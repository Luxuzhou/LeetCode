# **题目地址**
https://leetcode-cn.com/problems/merge-k-sorted-lists/
# **题目描述**
```
合并 k 个排序链表，返回合并后的排序链表。请分析和描述算法的复杂度。

示例:
输入:
[
  1->4->5,
  1->3->4,
  2->6
]
输出: 1->1->2->3->4->4->5->6

```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def mergeKLists(self, lists: List[ListNode]) -> ListNode:
        import heapq
        que , curs = [] , [] # curs存K个链表滑动的头指针
        for index, node in enumerate(lists):
                if node!=None:
                    heapq.heappush(que ,(node.val, index))
                curs.append(node)

        dummy_node = ListNode(-1)
        cur = dummy_node
        while que:
            val, index =  heapq.heappop(que)
            cur.next = lists[index]
            cur = cur.next
            lists[index] = lists[index].next
            if lists[index] != None:
                heapq.heappush(que, (lists[index].val, index))
        return dummy_node.next
```
C++ Code:
```
class Solution {
public:
    struct cmp {
        bool operator()(ListNode *a,ListNode *b) {
           return a->val > b->val;
        }
    };
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        priority_queue<ListNode*, vector<ListNode*>, cmp> heapk;
        for (auto p: lists) {
        if (p != NULL) {
            heapk.push(p);
        }
        }
        ListNode *pHead = new ListNode(-1);
        ListNode *pCur = pHead;
        while (!heapk.empty()) {
            ListNode *top = heapk.top(); heapk.pop();
            pCur -> next = top;
            pCur = pCur -> next;
            if (top -> next != NULL) {
                heapk.push(top -> next);
            } 
        }
        pCur = pHead -> next;
        delete pHead;
        return pCur;
    }
};
```

# **题目地址**

https://leetcode-cn.com/problems/add-two-numbers/
# **题目描述**
```
给出两个非空的链表用来表示两个非负的整数。
其中，它们各自的位数是按照逆序的方式存储的，并且它们的每个节点只能存储一位数字。
如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。
您可以假设除了数字0之外，这两个数都不会以0开头。
示例：
输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
输出：7 -> 0 -> 8
原因：342 + 465 = 807
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
	def addTwoNumbers(self, l1: ListsNode, l2: ListNode) -> ListNode:
		re = ListNode(0)
		r = re
		carry = 0
		while(l1 or l2):
			x = l1.val if l1 else 0
			y = l2.val if l2 else 0
			s = carry+x+y
			carry = s//10
			r.next = ListNode(s%10)
			r = r.next
			if(l1!=None):l1=l1.next
			if(l2!=None):l2=l2.next
		if(carry>0):
			r.next = ListNode(1)
		return re.next
```
C++ Code:
```
class Solution {
public:
	ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* head=new ListNode(-1);
        ListNode* h=head;
        int sum=0;
        bool carry=false;
        while(l1!=NULL||l2!=NULL)
        {
            sum=0;
            if(l1!=NULL)
            {
                sum+=l1->val;
                l1=l1->next;
            }
            if(l2!=NULL)
            {
                sum+=l2->val;
                l2=l2->next;
            }
            if(carry)
                sum++;
            h->next=new ListNode(sum%10);
            h=h->next;
            carry=sum>=10?true:false;
        }
        if(carry)
        {
            h->next=new ListNode(1);
        }
		ptrDelete = head; 
		head = head->next; 
		delete ptrDelete; 
		return head;
    }
};
```

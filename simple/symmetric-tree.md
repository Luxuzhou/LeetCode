# **题目地址**
https://leetcode-cn.com/problems/symmetric-tree/
# **题目描述**
```
给定一个二叉树，检查它是否是镜像对称的。

例如，二叉树 [1,2,2,3,4,4,3] 是对称的。
    1
   / \
  2   2
 / \ / \
3  4 4  3

但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:
    1
   / \
  2   2
   \   \
   3    3
   
说明:
如果你可以运用递归和迭代两种方法解决这个问题，会很加分。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def isSymmetric(self, root: TreeNode) -> bool:
        if not root: return True
        queue = [root.left, root.right]        
        while queue:   
            n1, n2 = queue.pop(), queue.pop()            
            if not n1 and not n2: continue     
            if not n1 or not n2: return False
            if n1.val != n2.val: return False
            queue.append(n1.left)
            queue.append(n2.right)
            queue.append(n1.right)
            queue.append(n2.left)            
        return True
```
C++ Code:
```
class Solution {
public:
    bool isSymmetric(TreeNode* root) {
        queue<TreeNode*> q;
        q.push(root);
        q.push(root);
        while (!q.empty()) {
            auto t1 = q.front();
            q.pop();
            auto t2 = q.front();
            q.pop();
            if (!t1 && !t2) continue;
            if (!t1 || !t2)
                return false;
            if (t1 -> val != t2 -> val)
                return false;
            q.push(t1 -> left);
            q.push(t2 -> right);
            q.push(t1 -> right);
            q.push(t2 -> left);
        }
        return true;
    }
};
```

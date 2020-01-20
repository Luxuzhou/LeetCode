# **题目地址**
https://leetcode-cn.com/problems/balanced-binary-tree/
# **题目描述**
```
给定一个二叉树，判断它是否是高度平衡的二叉树。
本题中，一棵高度平衡二叉树定义为：
一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过1。

示例 1:
给定二叉树 [3,9,20,null,null,15,7]
    3
   / \
  9  20
    /  \
   15   7
返回 true 。

示例 2:
给定二叉树 [1,2,2,3,3,null,null,4,4]
       1
      / \
     2   2
    / \
   3   3
  / \
 4   4
返回 false 。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        return self.depth(root) != -1
    def depth(self, root):
        if not root: return 0
        left = self.depth(root.left)
        if left == -1: return -1
        right = self.depth(root.right)
        if right == -1: return -1
        return max(left, right) + 1 if abs(left - right) < 2 else -1
```
C++ Code:
```
class Solution {
public:
    bool isBalanced(TreeNode* root) {
        return CheckBalance(root)>=0;
    }
    int CheckBalance(TreeNode* root) {
        if (!root) return 0;
        int Lh = CheckBalance(root -> left);
        if (Lh < 0)
            return Lh;
        int Rh = CheckBalance(root -> right);
        if (Rh < 0)
            return Rh;
        if (abs(Lh - Rh) < 2)
            return max(Lh, Rh) + 1;
        else
            return -1;
    }
};
```

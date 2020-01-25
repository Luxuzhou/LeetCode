# **题目地址**
https://leetcode-cn.com/problems/invert-binary-tree/
# **题目描述**
```
翻转一棵二叉树。

示例：

输入：

     4
   /   \
  2     7
 / \   / \
1   3 6   9

输出：

     4
   /   \
  7     2
 / \   / \
9   6 3   1
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def invertTree(self, root: TreeNode) -> TreeNode:
        if not root:
            return 
        else:
            root.left, root.right = root.right, root.left
            root.left = self.invertTree(root.left)
            root.right = self.invertTree(root.right)
        return root
```
C++ Code:
```
class Solution {
public:
    TreeNode* invertTree(TreeNode* root) {
        if (root == NULL) return root;
        TreeNode* temp = root -> left;
        root -> left = root -> right;
        root -> right = temp;
        invertTree(root -> left);
        invertTree(root -> right);
        return root;
    }
};
```

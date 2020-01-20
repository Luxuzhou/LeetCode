# **题目地址**
https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/
# **题目描述**
```
给定一个二叉树，找出其最大深度。
二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。

说明: 叶子节点是指没有子节点的节点。

示例：
给定二叉树 [3,9,20,null,null,15,7]，
    3
   / \
  9  20
    /  \
   15   7
返回它的最大深度 3 。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        if root is None:
            return 0
        queue = [(1, root)]
        while queue:
            depth, node = queue.pop(0)
            if node.left:
                queue.append((depth + 1,node.left))
            if node.right:
                queue.append((depth + 1,node.right))
        return depth
```
C++ Code:
```
class Solution {
public:
    int maxDepth(TreeNode* root) {
        return (root == NULL) ? 0: max(maxDepth(root -> left), maxDepth(root -> right)) + 1;
    }
};
```

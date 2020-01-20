# **题目地址**
https://leetcode-cn.com/problems/binary-tree-level-order-traversal-ii/
# **题目描述**
```
给定一个二叉树，返回其节点值自底向上的层次遍历。 （即按从叶子节点所在层到根节点所在的层，逐层从左向右遍历）

例如：
给定二叉树 [3,9,20,null,null,15,7],
    3
   / \
  9  20
    /  \
   15   7
   
返回其自底向上的层次遍历为：
[
  [15,7],
  [9,20],
  [3]
]
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def levelOrderBottom(self, root: TreeNode) -> List[List[int]]:
        res = []
        def helper(root, depth):
            if not root: return 
            if depth == len(res):
                res.insert(0, [])
            res[-(depth + 1)].append(root.val)
            helper(root.left, depth + 1)
            helper(root.right, depth + 1)
        helper(root, 0)
        return res
```
C++ Code:
```
class Solution {
public:
    vector<vector<int>> levelOrderBottom(TreeNode* root) {
        if (!root) return {};
        queue<TreeNode*> que;
        que.push(root);
        vector<vector<int>> ans;
        while (!que.empty()) {
            vector<int> v;
            for (int i = que.size(); i; i--) {
                TreeNode* curr = que.front();
                que.pop();
                v.push_back(curr -> val);
                if (curr -> left != NULL)
                    que.push(curr -> left);
                if (curr -> right != NULL)
                    que.push(curr -> right);
            }
            ans.push_back(v);
        }
        reverse(ans.begin(), ans.end());
        return ans;
    }
};
```

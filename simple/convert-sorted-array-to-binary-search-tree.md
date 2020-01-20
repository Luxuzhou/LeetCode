# **题目地址**
https://leetcode-cn.com/problems/convert-sorted-array-to-binary-search-tree/
# **题目描述**
```
将一个按照升序排列的有序数组，转换为一棵高度平衡二叉搜索树。
本题中，一个高度平衡二叉树是指一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过 1。

示例:
给定有序数组: [-10,-3,0,5,9],
一个可能的答案是：[0,-3,9,-10,null,5]，它可以表示下面这个高度平衡二叉搜索树：
      0
     / \
   -3   9
   /   /
 -10  5
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> TreeNode:
        if nums:
            m = len(nums) // 2
            r = TreeNode(nums[m])
            r.left, r.right = map(self.sortedArrayToBST, [nums[:m], nums[m+1:]])
            return r
```
C++ Code:
```
class Solution {
public:
    TreeNode* sortedArrayToBST(vector<int>& nums) {
        if(nums.empty()) return nullptr;
        return helper(nums, 0, nums.size() - 1);
    }
private:
    TreeNode* helper(vector<int>& nums, int left, int right){
        if(left > right)
            return nullptr;
        int mid = (left + right) / 2;
        TreeNode *root = new TreeNode(nums[mid]);
        root -> left = helper(nums, left, mid - 1);
        root -> right = helper(nums, mid + 1, right);
        return root;
    }
};
```

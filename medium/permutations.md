# **题目地址**
https://leetcode-cn.com/problems/permutations/
# **题目描述**
```
给定一个没有重复数字的序列，返回其所有可能的全排列。

示例:
输入: [1,2,3]
输出:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        res = []
        def backtrack(nums, tmp):
            if not nums:
                res.append(tmp)
                return 
            for i in range(len(nums)):
                backtrack(nums[:i] + nums[i+1:], tmp + [nums[i]])
        backtrack(nums, [])
        return res
```
C++ Code:
```
class Solution {
public:
    vector<vector<int>> permute(vector<int>& nums) {
        vector<vector<int>> res;
        backtrack(nums, res, 0);
        return res;
        }
    void swap(int &a,int &b) {
        int temp;
        temp = a;
        a = b;
        b = temp;
        }
    void backtrack(vector<int> &nums, vector<vector<int>> &res, int i) {
        if (i == nums.size())
            res.push_back(nums);
        for (int j = i; j < nums.size(); j++){
            swap(nums[i], nums[j]);
            backtrack(nums, res, i+1);
            swap(nums[i], nums[j]);
        }
    }
};
```

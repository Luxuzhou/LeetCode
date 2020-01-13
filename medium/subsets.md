# **题目地址**
https://leetcode-cn.com/problems/subsets/
# **题目描述**
```
给定一组不含重复元素的整数数组 nums，返回该数组所有可能的子集（幂集）。
说明：解集不能包含重复的子集。

示例:
输入: nums = [1,2,3]
输出:
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        res = []
        n = len(nums)
        def helper(i, tmp):
            res.append(tmp)
            for j in range(i, n):
                helper(j + 1, tmp + [nums[j]])
        helper(0, [])
        return res
```
C++ Code:
```
class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        if (nums.size() == 0) return {{}};
        int temp_int = nums.back();
        nums.pop_back();
        vector<vector<int>> temp_vec_vec = subsets(nums);
        int k = temp_vec_vec.size();
        for (int i = 0; i < k; i++) {
            temp_vec_vec.push_back(temp_vec_vec[i]);
            temp_vec_vec[i].push_back(temp_int);
        }
        return temp_vec_vec;
    }
};
```

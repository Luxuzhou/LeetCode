# **题目地址**
https://leetcode-cn.com/problems/subsets-ii/
# **题目描述**
```
给定一个可能包含重复元素的整数数组 nums，返回该数组所有可能的子集（幂集）。
说明：解集不能包含重复的子集。

示例:
输入: [1,2,2]
输出:
[
  [2],
  [1],
  [1,2,2],
  [2,2],
  [1,2],
  []
]
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        n = len(nums)
        nums.sort()
        def track_back(i, tmp):
            res.append(tmp)
            if (i == n):
                return
            for j in range(i, n):
                if (j > i and nums[j] == nums[j - 1]):
                    continue
                track_back(j + 1, tmp + [nums[j]])
        res = []
        track_back(0, [])
        return res
```
C++ Code:
```
class Solution {
public:
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        vector<vector<int>> ans;
        vector<int> v;
        ans.push_back(v);
        int right = 1, left = 0, len = 0;
        for (int i = 0; i < nums.size(); i++) {
            if (i != 0 && (nums[i] == nums[i - 1])) left = ans.size() -len;
            else left = 0;
            right = ans.size();
            len = right - left;
            for (int j = left; j < right; ++j) {
                v = ans[j];
                v.push_back(nums[i]);
                ans.push_back(v);
            }
        }
        return ans;
    }
};
```

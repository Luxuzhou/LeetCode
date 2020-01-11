# **题目地址**
https://leetcode-cn.com/problems/combination-sum-ii/
# **题目描述**
```
给定一个数组 candidates 和一个目标数 target ，找出 candidates 中所有可以使数字和为 target 的组合。
candidates 中的每个数字在每个组合中只能使用一次。

说明：
所有数字（包括目标数）都是正整数。
解集不能包含重复的组合。 

示例 1:
输入: candidates = [10,1,2,7,6,1,5], target = 8,
所求解集为:
[
  [1, 7],
  [1, 2, 5],
  [2, 6],
  [1, 1, 6]
]

示例 2:
输入: candidates = [2,5,2,1,2], target = 5,
所求解集为:
[
  [1,2,2],
  [5]
]
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        if (not candidates):
            return []
        n = len(candidates)
        candidates.sort()
        res = []
        def helper(i, tmp, target):
            print(i, tmp, target)
            if (target == 0):
                res.append(tmp)
                return
            if (i == n or target < candidates[i]):
                return
            for j in range(i, n):
                if(j > i and candidates[j] == candidates[j - 1]):
                    continue
                helper(j + 1, tmp + [candidates[j]], target - candidates[j])
        helper(0, [], target)
        return res
```
C++ Code:
```
class Solution {
public:
    vector<vector<int>> res;
    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        sort(candidates.begin(), candidates.end());
        vector<int> ans;
        recurs(candidates, ans, 0, target);
        return res;
    }
    void recurs(vector<int>& candidates, vector<int>& ans, int pos, int target) {
        if (target==0) {
            res.push_back(ans);
            return;
        }
        for (int i = pos; i < candidates.size(); ++i) {
            if (target - candidates[i] >= 0) {
                if (i != pos && candidates[i] == candidates[i - 1])
                    continue;
                ans.push_back(candidates[i]);
                recurs(candidates, ans, i+1, target-candidates[i]);
                ans.pop_back();
            }
            else {
                break;
            }
        }
    }
};
```

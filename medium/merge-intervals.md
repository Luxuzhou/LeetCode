# **题目地址**
https://leetcode-cn.com/problems/merge-intervals/
# **题目描述**
```
给出一个区间的集合，请合并所有重叠的区间。

示例 1:
输入: [[1,3],[2,6],[8,10],[15,18]]
输出: [[1,6],[8,10],[15,18]]
解释: 区间 [1,3] 和 [2,6] 重叠, 将它们合并为 [1,6].

示例 2:
输入: [[1,4],[4,5]]
输出: [[1,5]]
解释: 区间 [1,4] 和 [4,5] 可被视为重叠区间。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        intervals = sorted(intervals)
        res = []
        n = len(intervals)
        i = 0
        while i < n:
            left = intervals[i][0]
            right = intervals[i][1]
            while i < n - 1 and intervals[i+1][0] <= right:
                i += 1
                right = max(intervals[i][1], right)
            res.append([left, right])
            i += 1
        return res
```
C++ Code:
```
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        if (intervals.empty()) return {};
        vector<vector<int>> res;
        sort(intervals.begin(), intervals.end(), [](auto& a, auto& b) {
            return a[0] < b[0];
        });
        res.push_back(move(intervals[0]));
        int j = 0;
        for (int i = 1; i < intervals.size(); i++) {
            if (res[j][1] >= intervals[i][0] && res[j][1] <= intervals[i][1]) {
            res[j][1] = intervals[i][1];
            }
            else if (res[j][1] < intervals[i][0]) {
                j++;
                res.push_back(move(intervals[i]));
            }
        }
        return res;
    }
};
```

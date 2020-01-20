# **题目地址**
https://leetcode-cn.com/problems/pascals-triangle/
# **题目描述**
```
给定一个非负整数 numRows，生成杨辉三角的前 numRows 行。
在杨辉三角中，每个数是它左上方和右上方的数的和。

示例:
输入: 5
输出:
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        if numRows == 0: return []
        if numRows == 1: return[[1]]
        if numRows == 2: return[[1],[1,1]]
        res = [[1] * i for i in range(1, numRows + 1)]
        for i in range(2, numRows):
            dp = res[i - 1]
            for j in range(1, len(res[i]) - 1):
                res[i][j] = dp[j - 1] + dp[j]
        return res
```
C++ Code:
```
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>> sum;
        for (int i = 1; i <= numRows; i++) {
            if (i == 1) sum.push_back(vector<int>{1});
            else if (i == 2) sum.push_back(vector<int>{1, 1});
            else {
                vector<int> temp{1};
                for(int j = 1; j < i - 1; j++) {
                    temp.push_back(sum[i - 2][j - 1] + sum[i - 2][j]);
                }
                temp.push_back(1);
                sum.push_back(temp);
            }  
        }
        return sum;
    }
};
```

# **题目地址**
https://leetcode-cn.com/problems/unique-paths-ii/
# **题目描述**
```
一个机器人位于一个 m x n 网格的左上角 （起始点在下图中标记为“Start” ）。
机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为“Finish”）。
现在考虑网格中有障碍物。那么从左上角到右下角将会有多少条不同的路径？

网格中的障碍物和空位置分别用 1 和 0 来表示。
说明：m 和 n 的值均不超过 100。

示例 1:
输入:
[
  [0,0,0],
  [0,1,0],
  [0,0,0]
]
输出: 2
解释:
3x3 网格的正中间有一个障碍物。
从左上角到右下角一共有 2 条不同的路径：
1. 向右 -> 向右 -> 向下 -> 向下
2. 向下 -> 向下 -> 向右 -> 向右
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        m = len(obstacleGrid)
        if m < 1:
            return 0
        n = len(obstacleGrid[0])
        if n < 1:
            return 0
        if 1 == obstacleGrid[0][0]:
            return 0
        dp = [[0]*n for _ in range(m)]
        for i in range(0, m):
            for j in range(0, n):
                if 0 == i and 0 == j:
                    dp[i][j] = 1
                elif 0 == i and 0 != j:
                    if 0 == obstacleGrid[i][j]:
                        dp[i][j] = dp[i][j - 1]
                elif 0 != i and 0 == j:
                    if 0 == obstacleGrid[i][j]:
                        dp[i][j] = dp[i - 1][j]
                else:
                    if 0 == obstacleGrid[i][j]:
                        dp[i][j] = dp[i - 1][j] + dp[i][j - 1]
        return dp[-1][-1]
```
C++ Code:
```
class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
        int m = obstacleGrid.size();
        if (m < 1) return 0;
        int n = obstacleGrid[0].size();
        if (n < 1) return 0;
        long dp[m][n];
        if (1 == obstacleGrid[0][0]) return 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (0 == i && 0 == j) dp[i][j] = 1;
                else if (0 == i && j!=0) dp[i][j] = (1 == obstacleGrid[i][j] ? 0 : dp[i][j - 1]);
                else if (0 != i && j == 0) dp[i][j] = (1 == obstacleGrid[i][j] ? 0 : dp[i - 1][j]);
                else dp[i][j] = (1 == obstacleGrid[i][j] ? 0 : dp[i][j - 1] + dp[i - 1][j]);
            }
        }
        return static_cast<int>(dp[m - 1][n - 1]);
    }
};
```

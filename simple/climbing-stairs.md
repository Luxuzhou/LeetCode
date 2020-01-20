# **题目地址**
https://leetcode-cn.com/problems/climbing-stairs/
# **题目描述**
```
假设你正在爬楼梯。需要 n 阶你才能到达楼顶。
每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？
注意：给定 n 是一个正整数。

示例 1：
输入： 2
输出： 2
解释： 有两种方法可以爬到楼顶。
1.  1 阶 + 1 阶
2.  2 阶

示例 2：
输入： 3
输出： 3
解释： 有三种方法可以爬到楼顶。
1.  1 阶 + 1 阶 + 1 阶
2.  1 阶 + 2 阶
3.  2 阶 + 1 阶
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def climbStairs(self, n: int) -> int:
        dp = [0] * (n + 1)
        dp[1] = 1
        if (n < 2):
            return dp[n]
        dp[2] = 2
        for i in range(3, n + 1):
            dp[i] = dp[i - 1] + dp[i - 2]
        return dp[n]
```
C++ Code:
```
class Solution {
public:
    int climbStairs(int n) {
        int stair[n + 1] = {0};
        stair[0] = stair[1] = 1;
        for(int i = 2; i != n+1; ++i) {
            stair[i] = stair[i - 1] + stair[i - 2];
        }
        return stair[n];
    }
};
```

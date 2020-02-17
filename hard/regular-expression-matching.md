# **题目地址**
https://leetcode-cn.com/problems/regular-expression-matching/
# **题目描述**
```
给你一个字符串 s 和一个字符规律 p，请你来实现一个支持 '.' 和 '*' 的正则表达式匹配。

'.' 匹配任意单个字符
'*' 匹配零个或多个前面的那一个元素
所谓匹配，是要涵盖 整个 字符串 s的，而不是部分字符串。

说明:
s 可能为空，且只包含从 a-z 的小写字母。
p 可能为空，且只包含从 a-z 的小写字母，以及字符 . 和 *。

示例 1:
输入:
s = "aa"
p = "a"
输出: false
解释: "a" 无法匹配 "aa" 整个字符串。

示例 2:
输入:
s = "aa"
p = "a*"
输出: true
解释: 因为 '*' 代表可以匹配零个或多个前面的那一个元素, 在这里前面的元素就是 'a'。因此，字符串 "aa" 可被视为 'a' 重复了一次。

示例 3:
输入:
s = "ab"
p = ".*"
输出: true
解释: ".*" 表示可匹配零个或多个（'*'）任意字符（'.'）。

示例 4:
输入:
s = "aab"
p = "c*a*b"
输出: true
解释: 因为 '*' 表示零个或多个，这里 'c' 为 0 个, 'a' 被重复一次。因此可以匹配字符串 "aab"。

示例 5:
输入:
s = "mississippi"
p = "mis*is*p*."
输出: false
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def isMatch(self, s: str, p: str) -> bool:
        ls, lp = len(s), len(p)
        dp = [[False for _ in range(lp + 1)] for _ in range(ls + 1)]
        dp[0][0] = True
        for j in range(2, lp + 1):
            dp[0][j] = dp[0][j - 2] and p[j - 1] == '*'
        for i in range(1, ls + 1):
            for j in range(1, lp + 1):
                m, n = i - 1, j - 1
                if p[n] == '*':
                    if s[m] == p[n - 1] or p[n - 1] == '.':
                        dp[i][j] = dp[i][j - 2] or dp[i - 1][j]
                    else: dp[i][j] = dp[i][j - 2]
                elif s[m] == p[n] or p[n] == '.':
                    dp[i][j] = dp[i - 1][j - 1]
        return dp[-1][-1]
```
C++ Code:
```
class Solution {
public:
    // 动态规划
    bool isMatch(string s, string p) {
        int ns = s.length();
        int np = p.length();
        if (p.empty()) return s.empty();
        vector<vector<bool>> dp(ns + 1, vector<bool>(np + 1, false));
        dp[0][0] = true;
        for (int i = 1; i <= np; i++) {
            if (i - 2 >= 0 && p[i - 1] == '*' && p[i - 2]) {
                dp[0][i] = dp[0][i - 2];
            }
        }
        
        for (int i = 1; i <= ns; i++) {
            for (int j = 1; j <= np; j++) {
                if (p[j - 1] == s[i - 1] || p[j - 1] == '.')
                    dp[i][j] = dp[i - 1][j - 1];
                if (p[j - 1] == '*') {
                    bool zero, one;
                    if (j - 2 >= 0) {
                        zero = dp[i][j - 2];
                        one = (p[j - 2] == s[i - 1] || p[j - 2] == '.') && dp[i - 1][j];
                        dp[i][j] = zero || one;
                    }
                }
            }
        }
        return dp[ns][np];
    }
};
```

# **题目地址**
https://leetcode-cn.com/problems/longest-valid-parentheses/
# **题目描述**
```
给定一个只包含 '(' 和 ')' 的字符串，找出最长的包含有效括号的子串的长度。

示例 1:
输入: "(()"
输出: 2
解释: 最长有效括号子串为 "()"

示例 2:
输入: ")()())"
输出: 4
解释: 最长有效括号子串为 "()()"
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def longestValidParentheses(self, s: str) -> int:
        if (not s):
            return 0
        res = 0
        n = len(s)
        dp = [0] * n
        for i in range(1, len(s)):
            if (s[i] == ")"):
                if (s[i - 1] == "("):
                    dp[i] = dp[i - 2] + 2
                if (s[i - 1] == ")" and i - dp[i - 1] - 1 >= 0 and s[i - dp[i - 1] - 1] == "("):
                    dp[i] = dp[i - 1] + dp[i - dp[i - 1] - 2] + 2
                res = max(res, dp[i])
        return res
```
C++ Code:
```
class Solution {
public:
    int longestValidParentheses(string s) {
        pair<char, char> k = { '(',')' };
        s.insert(s.begin(), k.second);
        s.insert(s.begin(), k.second);
        vector<int> dp(s.size(), 0);
        int ans = 0;
        for (int i = 2; i < s.size(); i++) {
            if (s[i] == k.first) {
                dp[i] = 0;
            }
            else {
                if (s[i - 1] == k.first) {
                    dp[i] = dp[i - 2] + 2;
                }
                else if (s[i - dp[i - 1] - 1] == k.first) {
                    dp[i] = dp[i - dp[i - 1] - 2] + 2 + dp[i - 1];
                }
            }
            ans = max(ans, dp[i]);
        }
        return ans;
    }
};
```

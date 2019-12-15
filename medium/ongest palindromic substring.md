# **题目地址**
https://leetcode-cn.com/problems/longest-palindromic-substring/
# **题目描述**
```
给定一个字符串s，找到s中最长的回文子串。你可以假设s的最大长度为1000。

示例1：
输入:"babad"
输出:"bab"
注意:"aba"也是一个有效答案。

示例2：
输入:"cbbd"
输出:"bb"
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def longestPalindrome(self, s: str) -> str:
        size = len(s)
        if size <= 1:
            return s
            
        dp = [[False for _ in range(size)] for _ in range(size)]
        
        longest_l = 1
        res = s[0]

        for r in range(1, size):
            for l in range(r):
                if s[l] == s[r] and (r - l <= 2 or dp[l + 1][r - 1]):
                    dp[l][r] = True
                    cur_len = r - l + 1
                    if cur_len > longest_l:
                        longest_l = cur_len
                        res = s[l:r + 1]
        return res
```
C++ Code:
```
class Solution {
public:
    string longestPalindrome(string str) {
        const int n = str.size();
        if(n < 2) return str;
        int s = 0, e = 0;
        int i = 0, j = 0;
        int dp[n] = {0, };
        for(int j = 0; j < n; ++j){
            for(int i = 0; i < j; ++i){
                if(!(dp[i] = dp[i + 1] || str[i] != str[j]) && (e - s) <= (j - i)) 
                    s = i, e = j;
            }
        }
        return str.substr(s, e - s + 1);
    }
};
```

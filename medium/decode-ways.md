# **题目地址**
https://leetcode-cn.com/problems/decode-ways/
# **题目描述**
```
一条包含字母 A-Z 的消息通过以下方式进行了编码：
'A' -> 1
'B' -> 2
...
'Z' -> 26
给定一个只包含数字的非空字符串，请计算解码方法的总数。

示例 1:
输入: "12"
输出: 2
解释: 它可以解码为 "AB"（1 2）或者 "L"（12）。

示例 2:
输入: "226"
输出: 3
解释: 它可以解码为 "BZ" (2 26), "VF" (22 6), 或者 "BBF" (2 2 6) 。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def numDecodings(self, s: str) -> int:
        n = len(s)
        if (not s or s[0] == "0"):
            return 0
        pre = 1
        cur = 
        for i in range(1,n):
            if (s[i] == "0"):
                if (s[i - 1] == "1" or s[i - 1] == "2"):
                    cur = pre
                else:
                    return 0
            else:
                if (s[i-1] == "1" or (s[i - 1] == "2" and "1" <= s[i] <= "6")):
                    tmp = cur
                    cur += pre
                    pre = tmp
                else:
                    pre = cur
                    cur = cur
        return cur
```
C++ Code:
```
class Solution {
    int numDecodings(string s) {
        if (s[0] == '0') return 0;
        int pre = 1, curr = 1;//dp[-1] = dp[0] = 1
        for (int i = 1; i < s.size(); i++) {
            int tmp = curr;
            if (s[i] == '0')
                if (s[i - 1] == '1' || s[i - 1] == '2') curr = pre;
                else return 0;
            else if (s[i - 1] == '1' || (s[i - 1] == '2' && s[i] >= '1' && s[i] <= '6'))
                curr = curr + pre;
            pre = tmp;
        }
        return curr;
    }
};
```

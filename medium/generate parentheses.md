# **题目地址**
https://leetcode-cn.com/problems/generate-parentheses/
# **题目描述**
```
给出 n 代表生成括号的对数，请你写出一个函数，使其能够生成所有可能的并且有效的括号组合。

例如，给出 n = 3，生成结果为：

[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        if n == 0:
            return []
        total_l = []
        total_l.append([None])
        total_l.append(["()"])
        for i in range(2, n + 1):
            l = []
            for j in range(i):
                now_list1 = total_l[j]
                now_list2 = total_l[i - 1 - j]
                for k1 in now_list1:  
                    for k2 in now_list2:
                        if k1 == None:
                            k1 = ""
                        if k2 == None:
                            k2 = ""
                        el = "(" + k1 + ")" + k2
                        l.append(el)
            total_l.append(l)
        return total_l[n]
```
C++ Code:
```
class Solution {
public:
    vector<string> generateParenthesis(int n) {
        if (n == 0) return {};
        if (n == 1) return { "()" };
        vector<vector<string>> dp(n + 1);
        dp[0] = { "" };
        dp[1] = { "()" };
        for (int i = 2; i <= n; i++) {
            for (int j = 0; j < i; j++) {
                for (string p : dp[j]) {
                    for (string q : dp[i - j - 1]) {
                        string str = "(" + p + ")" + q;
                        dp[i].push_back(str);
                    }
                }
            }
        }
        return dp[n];
    }
};
```

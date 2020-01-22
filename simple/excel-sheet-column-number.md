# **题目地址**
https://leetcode-cn.com/problems/excel-sheet-column-number/
# **题目描述**
```
给定一个Excel表格中的列名称，返回其相应的列序号。

例如，
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
    ...
    
示例 1:
输入: "A"
输出: 1

示例 2:
输入: "AB"
输出: 28

示例 3:
输入: "ZY"
输出: 701
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def titleToNumber(self, s: str) -> int:
        res = 0
        bit = 1
        for a in s[::-1]:
            res += (ord(a) - 64) * bit
            bit *= 26
        return res
```
C++ Code:
```
class Solution {
public:
    int titleToNumber(string s) {
        int sum=0;
        int n=s.size() - 1;
        for (int i = 0;i < s.size(); i++) {
            int temp = pow(26, n) * (s[i] - 'A' + 1);
            sum += temp;
            n--;
        }
        return sum;
    }
};
```

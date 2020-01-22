# **题目地址**
https://leetcode-cn.com/problems/excel-sheet-column-title/
# **题目描述**
```
给定一个正整数，返回它在 Excel 表中相对应的列名称。

例如，
    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 
    ...
    
示例 1:
输入: 1
输出: "A"

示例 2:
输入: 28
输出: "AB"

示例 3:
输入: 701
输出: "ZY"
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def convertToTitle(self, n: int) -> str:
        res = ""
        while n:
            n -= 1
            n, y = divmod(n, 26) 
            res = chr(y + 65) + res
        return res
```
C++ Code:
```
class Solution {
public:
    string convertToTitle(int n) {
        string res;
        while(n){
            int a = --n % 26;
            res += ('A' + a);
            n /= 26;
        }
        reverse(res.begin(), res.end());
        return res;
    }
};
```

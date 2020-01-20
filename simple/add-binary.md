# **题目地址**
https://leetcode-cn.com/problems/add-binary/
# **题目描述**
```
给定两个二进制字符串，返回他们的和（用二进制表示）。
输入为非空字符串且只包含数字 1 和 0。

示例 1:
输入: a = "11", b = "1"
输出: "100"

示例 2:
输入: a = "1010", b = "1011"
输出: "10101"
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        if len(a) < len(b): 
            a, b = b, a
        n = len(a)
        b = '0' * (n - len(b)) + b   
        result = ''
        summ = 0   
        for i in range(n):
            a_1 = int(a[-i - 1])
            b_1 = int(b[-i - 1])
            result = str((a_1 + b_1 + summ) % 2) + result    
            summ = (a_1 + b_1 + summ) // 2    
        
        if summ == 1:
            result = '1' + result
        return result
```
C++ Code:
```
class Solution {
public:
    string addBinary(string a, string b) {
        int al = a.size();
        int bl = b.size();
        while (al < bl) {
            a = '0' + a;
            ++ al;
        }
        while (al > bl){
            b = '0' + b;
            ++ bl;
        }
        for (int j = a.size() - 1; j > 0; -- j) {
            a[j] = a[j] - '0' + b[j];
            if (a[j] >=  '2') 
            {
                a[j] = (a[j] - '0') % 2 + '0';
                a[j-1] = a[j-1] + 1;
            }
        }
        a[0] = a[0] - '0' + b[0]; 
        if(a[0] >= '2') {
            a[0] = (a[0] - '0') % 2 + '0';
            a = '1' + a;
        }
        return a;
    }
};
```

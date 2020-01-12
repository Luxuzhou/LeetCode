# **题目地址**
https://leetcode-cn.com/problems/multiply-strings/
# **题目描述**
```
给定两个以字符串形式表示的非负整数 num1 和 num2，返回 num1 和 num2 的乘积，它们的乘积也表示为字符串形式。

示例 1:
输入: num1 = "2", num2 = "3"
输出: "6"

示例 2:
输入: num1 = "123", num2 = "456"
输出: "56088"

说明：
num1 和 num2 的长度小于110。
num1 和 num2 只包含数字 0-9。
num1 和 num2 均不以零开头，除非是数字 0 本身。
不能使用任何标准库的大数类型（比如 BigInteger）或直接将输入转换为整数来处理。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def multiply(self, num1: str, num2: str) -> str:
        if len(num1) > len(num2):
            num1, num2 = num2, num1    
        l1, l2 = len(num1), len(num2)
        if l1 == 0 or l2 == 0:return str(0)
        res = 0
        for i in range(l1-1, -1, -1):
            p = int(num1[i])
            mid = ''                  
            carry = 0                  
            for j in range(l2-1, -1, -1):
                q = int(num2[j])
                temp = (p*q + carry)% 10         
                mid = str(temp) + mid            
                carry = (p*q + carry)// 10
            if carry != 0:mid = str(carry) + mid
            res += int(mid) * 10**(l1-1-i)       
        return str(res)
```
C++ Code:
```
class Solution {
public:
    string multiply(string num1, string num2) {
        int n1 = num1.size();
        int n2 = num2.size();
        string res(n1 + n2, '0');
        for (int i = n2 - 1; i >= 0; i--) {
            for (int j = n1 - 1;j >= 0; j--) {
                int temp = (res[i + j + 1] - '0') + (num1[j] - '0') * (num2[i] - '0');
                res[i + j + 1] = temp % 10 + '0';
                res[i + j] += temp / 10; 
            }
        }
        for (int i = 0; i < n1 + n2; i++) {
            if(res[i] != '0')
                return res.substr(i);
        }
        return "0";     
    }
};
```

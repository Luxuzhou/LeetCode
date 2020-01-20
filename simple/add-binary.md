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

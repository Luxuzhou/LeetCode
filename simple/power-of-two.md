# **题目地址**
https://leetcode-cn.com/problems/power-of-two/
# **题目描述**
```
给定一个整数，编写一个函数来判断它是否是 2 的幂次方。

示例 1:
输入: 1
输出: true
解释: 2^0 = 1

示例 2:
输入: 16
输出: true
解释: 2^4 = 16

示例 3:
输入: 218
输出: false
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def isPowerOfTwo(self, n: int) -> bool:
        return n > 0 and n & (n - 1) == 0
```
C++ Code:
```
class Solution {
public:
    bool isPowerOfTwo(int n) {
        if (n <= 0) return false;
        return (n & (n - 1)) == 0;
    }
};
```

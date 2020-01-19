# **题目地址**
https://leetcode-cn.com/problems/reverse-integer/
# **题目描述**
```
给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。

示例 1:
输入: 123
输出: 321

示例 2:
输入: -123
输出: -321

示例 3:
输入: 120
输出: 21

注意:
假设我们的环境只能存储得下 32 位的有符号整数，则其数值范围为 [−2^31,  2^31 − 1]。请根据这个假设，如果反转后整数溢出那么就返回 0。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def reverse(self, x: int) -> int:
        if '-' in str(x):
            x1 = -int(str(x)[1:][::-1])
        else:
            x1 = int(str(x)[::-1])
        if x1 < -2**31 or x1 > 2**31 - 1:
            return 0
        return x1
```
C++ Code:
```
class Solution {
public:
    int reverse(int x) {
        int rpc = 0;
        while(x != 0) {
            if (rpc > INT32_MAX / 10 || (rpc == INT32_MAX / 10 && x % 10 > 7)) return 0;
            if (rpc < INT32_MIN / 10 || (rpc == INT32_MIN / 10 && x % 10 < -8)) return 0;
            rpc = rpc * 10 + x % 10;
            x /= 10; 
        }
        return rpc;
    }
};
```

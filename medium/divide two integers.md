# **题目地址**
https://leetcode-cn.com/problems/divide-two-integers/
# **题目描述**
```
给定两个整数，被除数 dividend 和除数 divisor。将两数相除，要求不使用乘法、除法和 mod 运算符。
返回被除数 dividend 除以除数 divisor 得到的商。

示例 1:
输入: dividend = 10, divisor = 3
输出: 3

示例 2:
输入: dividend = 7, divisor = -3
输出: -2

说明:
被除数和除数均为 32 位有符号整数。
除数不为 0。
假设我们的环境只能存储 32 位有符号整数，其数值范围是 [−2^31,  2^31 − 1]。
本题中，如果除法结果溢出，则返回 2^31 − 1。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def divide(self, dividend: int, divisor: int) -> int:
        if (dividend > 0 and divisor > 0) or (dividend < 0 and divisor < 0):
            tag = 1
        else:
            tag = -1
        res = self.divCreas(abs(dividend), abs(divisor))
        if tag == -1: res = 0 - res
        if res > (2 << 30) - 1: return (2 << 30) - 1
        elif res < 0 - (2 << 30): return 0 - (2 << 30)
        return res
    def divCreas(self, dividend: int, divisor: int) -> int:
        ex, count = divisor, 0
        t, m = 0, 1
        if dividend < divisor:
            return 0
        while dividend - t - ex >= 0:
            t += ex
            count += m
            m += m
            ex += ex
        if dividend - t > 0:
            return count + self.divCreas(dividend - t, divisor)
        return count
```
C++ Code:
```
class Solution {
public:
    int divide(int dividend, int divisor) {
        if (dividend == 0) return 0;
        if (divisor == 1) return dividend;
        if (divisor == -1) {
            if (dividend > INT_MIN) return -dividend;
            return INT_MAX;
        }
        long a = dividend;
        long b = divisor;
        int sign = 1; 
        if ((a > 0 && b < 0) || (a < 0 && b > 0)){
            sign = -1;
        }
        a = a > 0 ? a : -a;
        b = b > 0 ? b : -b;
        long res = div(a, b);
        if (sign > 0) return res > INT_MAX ? INT_MAX : res;
        return -res;
    }
    int div(long a, long b){
        if (a < b) return 0;
        long count = 1;
        long tb = b; 
        while ((tb + tb) <= a){
            count = count + count;
            tb = tb + tb;
        }
        return count + div(a - tb, b);
    }
};
```

# **题目地址**
https://leetcode-cn.com/problems/powx-n/
# **题目描述**
```
实现 pow(x, n) ，即计算 x 的 n 次幂函数。

示例 1:
输入: 2.00000, 10
输出: 1024.00000

示例 2:
输入: 2.10000, 3
输出: 9.26100

示例 3:
输入: 2.00000, -2
输出: 0.25000
解释: 2^-2 = 1/2^2 = 1/4 = 0.25

说明:
-100.0 < x < 100.0
n 是 32 位有符号整数，其数值范围是 [−2^31, 2^31 − 1]。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def myPow(self, x: float, n: int) -> float:
        judge = True
        if n < 0:
            n = -n
            judge = False
        final = 1
        while n > 0:
            if n & 1:
                final *= x
            x *= x
            n >>= 1
        return final if judge else 1 / final
```
C++ Code:
```
class Solution {
public:
    double myPow(double x, int n) {
        if (n == 0) return 1;
        if (n == 1) return x;
        if (n == -1) return 1 / x;
        double half = myPow(x, n / 2);
        double rest = myPow(x, n % 2);
        return rest * half * half;
    }
};
```

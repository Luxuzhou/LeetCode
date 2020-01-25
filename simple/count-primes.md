# **题目地址**
https://leetcode-cn.com/problems/count-primes/
# **题目描述**
```
统计所有小于非负整数 n 的质数的数量。

示例:
输入: 10
输出: 4
解释: 小于 10 的质数一共有 4 个, 它们是 2, 3, 5, 7 。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def countPrimes(self, n: int) -> int:
        if n < 3:
            return 0     
        else:
            output = [1] * n
            output[0], output[1] = 0, 0
            for i in range(2, int(n ** 0.5) + 1): 
                if output[i] == 1:
                    output[i * i : n : i] = [0] * len(output[i * i : n : i])
        return sum(output)
```
C++ Code:
```
class Solution {
public:
    int countPrimes(int n) {
        int count = 0;
        vector<bool> signs(n, true);
        for (int i = 2; i < n; i++) {
            if (signs[i]) {
                count++;
                for (int j = i + i; j < n; j += i) {
                    signs[j] = false;
                }
            }
        }
        return count;
    }
};
```

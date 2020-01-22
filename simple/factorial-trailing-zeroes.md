# **题目地址**
https://leetcode-cn.com/problems/factorial-trailing-zeroes/
# **题目描述**
```
给定一个整数 n，返回 n! 结果尾数中零的数量。

示例 1:
输入: 3
输出: 0
解释: 3! = 6, 尾数中没有零。

示例 2:
输入: 5
输出: 1
解释: 5! = 120, 尾数中有 1 个零.
说明: 你算法的时间复杂度应为 O(log n) 。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def trailingZeroes(self, n: int) -> int:
        p = 0 
        while n >= 5: 
            n = n // 5 
            p += n 
        return p
```
C++ Code:
```
class Solution {
public:
    int trailingZeroes(int n) {
        unsigned int nCount = 0;
		while (n) {
			nCount += (n / 5);
			n /= 5;
		}
		return nCount;
    }
};
```

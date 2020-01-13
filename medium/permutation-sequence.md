# **题目地址**
https://leetcode-cn.com/problems/permutation-sequence/
# **题目描述**
```
给出集合 [1,2,3,…,n]，其所有元素共有 n! 种排列。
按大小顺序列出所有排列情况，并一一标记，当 n = 3 时, 所有排列如下：
"123"
"132"
"213"
"231"
"312"
"321"
给定 n 和 k，返回第 k 个排列。

说明：

给定 n 的范围是 [1, 9]。
给定 k 的范围是[1,  n!]。

示例 1:
输入: n = 3, k = 3
输出: "213"

示例 2:
输入: n = 4, k = 9
输出: "2314"
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def getPermutation(self, n: int, k: int) -> str:
        nums = [str(i) for i in range(1, n + 1)]
        ans = ''
        k = k - 1
        while n > 0:
            kth = self.factorial(n - 1)
            p = k // kth
            k = k % kth
            ans += nums[p]
            del nums[p]
            n -= 1
            if k == 0:
                for c in nums:
                    ans += c
                break
        return ans
    def factorial(self, n):
        res = 1
        while n:
            res *= n
```
C++ Code:
```
class Solution {
public:
    string getPermutation(int n, int k) {
        vector<char> chs = {'1', '2', '3', '4', '5', '6', '7', '8', '9'};
        const int factor[] = {1, 1, 2, 6, 24, 120, 720, 5040, 40320, 362880};
        string str;
        for (--k; n--; k %= factor[n]) {
            const int i = k / factor[n];
            str.push_back(chs[i]);
            chs.erase(chs.begin() + i);
        }
        return str;
    }
};
```

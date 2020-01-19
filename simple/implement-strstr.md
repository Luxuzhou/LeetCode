# **题目地址**
https://leetcode-cn.com/problems/implement-strstr/
# **题目描述**
```
实现 strStr() 函数。
给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从0开始)。如果不存在，则返回  -1。

示例 1:
输入: haystack = "hello", needle = "ll"
输出: 2

示例 2:
输入: haystack = "aaaaa", needle = "bba"
输出: -1

说明:
当 needle 是空字符串时，我们应当返回什么值呢？这是一个在面试中很好的问题。
对于本题而言，当 needle 是空字符串时我们应当返回 0 。这与C语言的 strstr() 以及Java的 indexOf() 定义相符。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        for i in range(0, len(haystack) - len(needle) + 1):
 	        if haystack[i: i + len(needle)] == needle:
 	            return i
        return -1
```
C++ Code:
```
class Solution {
public:
    int strStr(string haystack, string needle) {
        int n = haystack.size(), m = needle.size();
        for (int i = 0; i < n - m + 1; i++) {
            int j = 0;
            for ( ; j < m; j++) {
                if(haystack[i + j] !=  needle[j])
                    break;
            }
            if (j == m)
                return i;
        }
        return -1;
    }
};
```

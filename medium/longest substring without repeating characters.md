# **题目地址**
https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/
# **题目描述**
```
给定一个字符串，请你找出其中不含有重复字符的最长子串的长度。

示例1:
输入:"abcabcbb"
输出:3 
解释:因为无重复字符的最长子串是"abc"，所以其长度为3。

示例2:
输入:"bbbbb"
输出:1
解释:因为无重复字符的最长子串是"b"，所以其长度为1。

示例3:
输入:"pwwkew"
输出:3
解释:因为无重复字符的最长子串是 "wke"，所以其长度为3。

请注意，你的答案必须是子串的长度，"pwke"是一个子序列，不是子串。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        if not s:return 0
        left = 0
        lookup = set()
        n = len(s)
        max_len = 0
        cur_len = 0
        for i in range(n):
            cur_len += 1
            while s[i] in lookup:
                lookup.remove(s[left])
                left += 1
                cur_len -= 1
            if cur_len > max_len:max_len = cur_len
            lookup.add(s[i])
        return max_len
```
C++ Code:
```
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        vector<int>m(256, -1);
        int left = -1;
        int res = 0;
        int len = s.size();
        for(int i=0; i<len; i++)
        {
            left = max(left, m[s[i]]);
            m[s[i]] = i;
            res=max(res, i-left);
        }
        
        return res;
    }
};
```

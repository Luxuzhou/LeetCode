# **题目地址**
https://leetcode-cn.com/problems/isomorphic-strings/
# **题目描述**
```
给定两个字符串 s 和 t，判断它们是否是同构的。
如果 s 中的字符可以被替换得到 t ，那么这两个字符串是同构的。
所有出现的字符都必须用另一个字符替换，同时保留字符的顺序。两个字符不能映射到同一个字符上，但字符可以映射自己本身。

示例 1:
输入: s = "egg", t = "add"
输出: true

示例 2:
输入: s = "foo", t = "bar"
输出: false

示例 3:
输入: s = "paper", t = "title"
输出: true

说明:
你可以假设 s 和 t 具有相同的长度。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        flag = True
        for i in range(len(s)):
            if s[i + 1:].find(s[i]) != t[i + 1:].find(t[i]):
                flag = False
                break
        return flag
```
C++ Code:
```
class Solution {
public:
    bool isIsomorphic(string s, string t) {
        unordered_map<char,char> smap;
        unordered_map<char,char> tmap;
        for (int i = 0; i < s.length(); i++) {
            if (smap.count(s.at(i)) && smap[s.at(i)] != t.at(i))
                return false;
            if (tmap.count(t.at(i)) && tmap[t.at(i)] != s.at(i))
                return false;
            smap[s.at(i)] = t.at(i);
            tmap[t.at(i)] = s.at(i);
        }
        return true;
    }
};
```

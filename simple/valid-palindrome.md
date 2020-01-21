# **题目地址**
https://leetcode-cn.com/problems/valid-palindrome/
# **题目描述**
```
给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。
说明：本题中，我们将空字符串定义为有效的回文串。

示例 1:
输入: "A man, a plan, a canal: Panama"
输出: true

示例 2:
输入: "race a car"
输出: false
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def isPalindrome(self, s: str) -> bool:
        i, j = 0, len(s) - 1
        while i < j:
            while i < len(s) and not s[i].isalnum():
                i += 1
            while j > -1 and not s[j].isalnum():
                j -= 1
            if i > j:
                return True
            if s[i].upper() != s[j].upper():
                return False
            else:
                i += 1
                j -= 1
        return True
```
C++ Code:
```
class Solution {
public:
    bool isPalindrome(string s) {
        if(s.size() <= 1) return true;
        int i = 0, j = s.size() - 1;
        while (i < j){
            while (i < j && !isalnum(s[i]))
                i++;
            while (i < j && !isalnum(s[j]))
                j--;
            if (tolower(s[i++]) != tolower(s[j--]))
                return false;
        }
        return true;
    }
};
```

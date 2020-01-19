# **题目地址**
https://leetcode-cn.com/problems/valid-parentheses/
# **题目描述**
```
给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。
有效字符串需满足：
左括号必须用相同类型的右括号闭合。
左括号必须以正确的顺序闭合。
注意空字符串可被认为是有效字符串。

示例 1:
输入: "()"
输出: true

示例 2:
输入: "()[]{}"
输出: true

示例 3:
输入: "(]"
输出: false

示例 4:
输入: "([)]"
输出: false

示例 5:
输入: "{[]}"
输出: true
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def isValid(self, s: str) -> bool:
        dic = {'{': '}',  '[': ']', '(': ')', '?': '?'}
        stack = ['?']
        for c in s:
            if c in dic: stack.append(c)
            elif dic[stack.pop()] != c: return False 
        return len(stack) == 1
```
C++ Code:
```
class Solution {
public:
    bool isValid(string s) {
        stack<char> m_stack;
        for(const auto& v :s) {
            if (m_stack.empty())
                m_stack.push(v);
            else if (compare(m_stack.top(), v))
                m_stack.pop();
            else
                m_stack.push(v);
        }
        return m_stack.size() == 0 ? true : false;
    }
private:
    bool compare(const char& c1,const char& c2)
    {
        return (c1 == '[' && c2 == ']') || (c1 == '(' && c2 == ')') || (c1 == '{' && c2 == '}');
    }
};
```

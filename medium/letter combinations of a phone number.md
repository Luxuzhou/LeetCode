# **题目地址**
https://leetcode-cn.com/problems/letter-combinations-of-a-phone-number/
# **题目描述**
```
给定一个仅包含数字 2-9 的字符串，返回所有它能表示的字母组合。
给出数字到字母的映射如下（与电话按键相同）。注意 1 不对应任何字母。

示例:
输入："23"
输出：["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].

说明:
尽管上面的答案是按字典序排列的，但是你可以任意选择答案输出的顺序。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution(object):
    def letterCombinations(self, digits: str) -> List[str]:
        if not digits:
            return []
        d = {'2': 'abc', '3': 'def', '4': 'ghi', '5': 'jkl',
             '6': 'mno', '7': 'pqrs', '8': 'tuv', '9': 'wxyz'}
        n = len(digits)
        res = ['']
        for i in range(n):
            res = [x + y for x in res for y in d[digits[i]]]
        return res
```
C++ Code:
```
class Solution {
public:
    vector<string> letterCombinations(string digits) {
        vector<string> res;
        map<char, string> m = { {'2', "abc"}, {'3', "def"}, {'4', "ghi"}, {'5', "jkl"}, {'6', "mno"}, {'7', "pqrs"}, {'8', "tuv"}, {'9', "wxyz"} };
        int size = digits.size();
        queue<string> que;
        for (int j = 0; j < m[digits[0]].size(); j++) {
            string str;
            str.push_back(m[digits[0]][j]);
            que.push(str);
        }
        string s;
        for (int i = 1; i < size; i++) {
            int length = que.size();
            while (length--) {
                for (int j = 0; j < m[digits[i]].size(); j++) {
                    s = que.front();
                    s = s + m[digits[i]][j];
                    que.push(s);
                }
                que.pop();
            }
        }
        while (!que.empty()) {
            res.push_back(que.front());
            que.pop();
        }
        return res;
    }
};
```

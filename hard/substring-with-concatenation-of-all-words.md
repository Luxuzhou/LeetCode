# **题目地址**
https://leetcode-cn.com/problems/substring-with-concatenation-of-all-words/
# **题目描述**
```
给定一个字符串 s 和一些长度相同的单词 words。找出 s 中恰好可以由 words 中所有单词串联形成的子串的起始位置。
注意子串要与 words 中的单词完全匹配，中间不能有其他字符，但不需要考虑 words 中单词串联的顺序。

示例 1：
输入：
  s = "barfoothefoobarman",
  words = ["foo","bar"]
输出：[0,9]
解释：
从索引 0 和 9 开始的子串分别是 "barfoo" 和 "foobar" 。
输出的顺序不重要, [9,0] 也是有效答案。

示例 2：
输入：
  s = "wordgoodgoodgoodbestword",
  words = ["word","good","best","word"]
输出：[]
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def findSubstring(self, s: str, words: List[str]) -> List[int]:
        res = []
        write = []
        if len(words) == 0:
            return []
        if len(s) < len(words) * len(words[0]):
            return []
        dic = {}
        flag = 0
        for i in words:
            try:
                dic[i] += 1
            except KeyError:
                dic[i] = 1
                flag += 1
                write.append(i)
        left, right = 0, len(words) * len(words[0])
        while right <= len(s):
            n, start = 0, left
            per = len(words[0])
            tag = dict(zip(write, [0] * flag))
            while n < len(words):
                if dic.get(s[start:start+per]):
                    if tag[s[start:start+per]] < dic[s[start:start+per]]:
                        tag[s[start:start+per]] += 1
                        n += 1
                        start += per
                    else:
                        break
                else:
                    break
            if n == len(words):
                res.append(left)
            left += 1
            right += 1
        return res
```
C++ Code:
```
class Solution {
public:
    vector<int> findSubstring(string s, vector<string>& words) {
        vector<int> result;
        if (s.size() <= 0 || words.size() <= 0 || words.begin()->size() <= 0)
			  return result;
		    int wlen = words.begin() -> size();
		    int wcot = words.size();
		    if (wlen * wcot > s.size()) return result;
		    sort(words.begin(), words.end());
		    vector<string> buff;
		    for (int i = 0; i <= s.size() - (wlen*wcot); i++) {
			      stepSplit(&s, i, wlen, wcot, &buff);
			      sort(buff.begin(), buff.end());
			      if (buff == words) result.push_back(i);
			      buff.clear();
		    }
		    return result;
	  }
	void stepSplit(string *s, int i, int k, int n, vector<string> *result) {
		  while(n--) {
			    result -> push_back(s -> substr(i, k));
			    i += k;
		    }
    }
};
```

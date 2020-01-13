# **题目地址**
https://leetcode-cn.com/problems/group-anagrams/
# **题目描述**
```
给定一个字符串数组，将字母异位词组合在一起。字母异位词指字母相同，但排列不同的字符串。

示例:

输入: ["eat", "tea", "tan", "ate", "nat", "bat"]
输出:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
说明：

所有输入均为小写字母。
不考虑答案输出的顺序。
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        from collections import defaultdict
        lookup = defaultdict(list)
        for s in strs:
            lookup["".join(sorted(s))].append(s)
        return list(lookup.values())
```
C++ Code:
```
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        map<string, vector<string>> ma;
        vector<vector<string>> res;
        for (auto str:strs) {
            string tmp = str;
            sort(tmp.begin(), tmp.end());
            ma[tmp].push_back(str);
        }
        for(const auto& m:ma)
            res.push_back(m.second);
        return res;
    }
};
```

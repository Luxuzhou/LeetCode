# **题目地址**
https://leetcode-cn.com/problems/pascals-triangle-ii/
# **题目描述**
```
给定一个非负索引 k，其中 k ≤ 33，返回杨辉三角的第 k 行。
在杨辉三角中，每个数是它左上方和右上方的数的和。

示例:
输入: 3
输出: [1,3,3,1]

进阶：
你可以优化你的算法到 O(k) 空间复杂度吗？
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def getRow(self, rowIndex: int) -> List[int]:
        i, result = 0, [1]
        while i < rowIndex:
            result = [1] + [result[x] + result[x + 1] for x in range(len(result) - 1)] + [1]
            i += 1
        return result
```
C++ Code:
```
class Solution {
public:
    vector<int> getRow(int rowIndex) {
        vector<int> result;
        for (int i = 0; i <= rowIndex; ++i) {
            result.push_back(1);
            for (int j = i - 1; j > 0; --j) {
                result[j] += result[j - 1];
            }
        }
        return result;
    }
};
```

# **题目地址**
https://leetcode-cn.com/problems/gray-code/
# **题目描述**
```
格雷编码是一个二进制数字系统，在该系统中，两个连续的数值仅有一个位数的差异。
给定一个代表编码总位数的非负整数 n，打印其格雷编码序列。格雷编码序列必须以 0 开头。

示例 1:
输入: 2
输出: [0,1,3,2]
解释:
00 - 0
01 - 1
11 - 3
10 - 2

对于给定的 n，其格雷编码序列并不唯一。
例如，[0,2,3,1] 也是一个有效的格雷编码序列。

00 - 0
10 - 2
11 - 3
01 - 1

示例 2:
输入: 0
输出: [0]
解释: 我们定义格雷编码序列必须以 0 开头。
     给定编码总位数为 n 的格雷编码序列，其长度为 2^n。当 n = 0 时，长度为 2^0 = 1。
     因此，当 n = 0 时，其格雷编码序列为 [0]。

```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def grayCode(self, n: int) -> List[int]:
        res, head = [0], 1
        for i in range(n):
            for j in range(len(res) - 1, -1, -1):
                res.append(head + res[j])
            head <<= 1
        return res
```
C++ Code:
```
class Solution {
public:
    vector<int> grayCode(int n) {
        vector<int> result(1);
        result[0] = 0;
        for (int i = 1; i <= n; i++) {
            int e = 1 << (i - 1);                          
            for (int j = result.size() - 1; j >= 0; j--) {  
                result.push_back(e + result[j]);
            }
        }
        return result;
    }
};
```

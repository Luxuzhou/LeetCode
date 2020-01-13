# **题目地址**
https://leetcode-cn.com/problems/spiral-matrix-ii/
# **题目描述**
```
给定一个正整数 n，生成一个包含 1 到 n^2 所有元素，且元素按顺时针顺序螺旋排列的正方形矩阵。

示例:
输入: 3
输出:
[
 [ 1, 2, 3 ],
 [ 8, 9, 4 ],
 [ 7, 6, 5 ]
]
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        l, r, t, b = 0, n - 1, 0, n - 1
        mat = [[0 for _ in range(n)] for _ in range(n)]
        num, tar = 1, n * n
        while num <= tar:
            for i in range(l, r + 1):
                mat[t][i] = num
                num += 1
            t += 1
            for i in range(t, b + 1):
                mat[i][r] = num
                num += 1
            r -= 1
            for i in range(r, l - 1, -1):
                mat[b][i] = num
                num += 1
            b -= 1
            for i in range(b, t - 1, -1):
                mat[i][l] = num
                num += 1
            l +=1
        return mat
```
C++ Code:
```
class Solution {
public:
    vector<vector<int>> generateMatrix(int n) {
        vector<vector<int>> res(n, vector<int>(n));
        for (int s = 0, e = n - 1, m = 1; s <= e; s++, e--) {
            if (s == e) res[s][e] = m++;
            for (int j = s; j <= e - 1; j++) res[s][j] = m++;
            for (int i = s; i <= e - 1; i++) res[i][e] = m++;
            for (int j = e; j >= s + 1; j--) res[e][j] = m++;
            for (int i = e; i >= s + 1; i--) res[i][s] = m++;
        }
        return res;
    }
};
```

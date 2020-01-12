# **题目地址**
https://leetcode-cn.com/problems/rotate-image/
# **题目描述**
```
给定一个 n × n 的二维矩阵表示一个图像。
将图像顺时针旋转 90 度。

说明：
你必须在原地旋转图像，这意味着你需要直接修改输入的二维矩阵。请不要使用另一个矩阵来旋转图像。

示例 1:
给定 matrix = 
[
  [1,2,3],
  [4,5,6],
  [7,8,9]
],

原地旋转输入矩阵，使其变为:
[
  [7,4,1],
  [8,5,2],
  [9,6,3]
]
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        for x in range(len(matrix)):
            for y in range(x):
                matrix[x][y], matrix[y][x] = matrix[y][x], matrix[x][y]
        for i in range(len(matrix)):
            for j in range(len(matrix[i]) // 2):
                matrix[i][j], matrix[i][len(matrix) - 1 - j] = matrix[i][len(matrix) - 1 - j], matrix[i][j]
```
C++ Code:
```
class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        int n = matrix.size();
        for (int loop = 0; loop < n / 2; loop++) {                    
            for (int i = loop, j = loop; i < n - 1 - loop; i++) {   
                int pre = matrix[i][j];
                for (int time = 1; time <= 4; time++) {             
                    int tmpi = i; i = j; j = n - 1 - tmpi;
                    swap(pre, matrix[i][j]);
                }
            }
        }
    }
};
```

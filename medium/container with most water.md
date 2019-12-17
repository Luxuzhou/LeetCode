# **题目地址**
https://leetcode-cn.com/problems/container-with-most-water/
# **题目描述**
```
给定n个非负整数a1,a2,...an,每个数代表坐标中的一个点(i,ai)。
在坐标内画n 条垂直线,垂直线i的两个端点分别为(i,ai)和(i,0)。
找出其中的两条线,使得它们与x轴共同构成的容器可以容纳最多的水。

说明：你不能倾斜容器,且n的值至少为2。

示例:
输入:[1,8,6,2,5,4,8,3,7]
输出:49
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def maxArea(self, height: List[int]) -> int:
        i, j, res = 0, len(height) - 1, 0
        while i < j:
            if height[i] < height[j]:
                res = max(res, height[i] * (j - i))
                i += 1
            else:
                res = max(res, height[j] * (j - i))
                j -= 1
        return res
```
C++ Code:
```
class Solution {
public:
    int maxArea(vector<int>& height) {
        int i = 0;
        int j = height.size() - 1;
        int res = 0;
        while (i < j) {
            int temp1 = min(height[i], height[j]);
            int temp2 = temp1 * (j - i);
            res = max(res, temp2);
            if (height[i] < height[j])
                i++;
            else j--;
        }
        return res;
    }
};
```

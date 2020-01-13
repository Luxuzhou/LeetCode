# **题目地址**
https://leetcode-cn.com/problems/sort-colors/
# **题目描述**
```
给定一个包含红色、白色和蓝色，一共 n 个元素的数组，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。
此题中，我们使用整数 0、 1 和 2 分别表示红色、白色和蓝色。

注意:
不能使用代码库中的排序函数来解决这道题。

示例:
输入: [2,0,2,1,1,0]
输出: [0,0,1,1,2,2]

进阶：
一个直观的解决方案是使用计数排序的两趟扫描算法。
首先，迭代计算出0、1 和 2 元素的个数，然后按照0、1、2的排序，重写当前数组。
你能想出一个仅使用常数空间的一趟扫描算法吗？
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        r, w, b = 0, 0, len(nums) - 1
        while w <= b:
            if nums[w] == 0:
                nums[w], nums[r] = nums[r], nums[w]
                r += 1
                w += 1
            elif nums[w] == 1:
                w += 1
            else:
                nums[w], nums[b] = nums[b], nums[w]
                b -= 1
```
C++ Code:
```
class Solution {
public:
    void sortColors(vector<int>& nums) {
        int p0 = 0, curr = 0;
        int p2 = nums.size() - 1;
        while (curr <= p2) {
            if (nums[curr] == 0) {
                swap(nums[curr++], nums[p0++]);
            }
            else if (nums[curr] == 2) {
                swap(nums[curr], nums[p2--]);
            }
            else curr++;
        }
    }
};
```

# **题目地址**
https://leetcode-cn.com/problems/rotate-array/
# **题目描述**
```
给定一个数组，将数组中的元素向右移动 k 个位置，其中 k 是非负数。

示例 1:
输入: [1,2,3,4,5,6,7] 和 k = 3
输出: [5,6,7,1,2,3,4]
解释:
向右旋转 1 步: [7,1,2,3,4,5,6]
向右旋转 2 步: [6,7,1,2,3,4,5]
向右旋转 3 步: [5,6,7,1,2,3,4]

示例 2:
输入: [-1,-100,3,99] 和 k = 2
输出: [3,99,-1,-100]
解释: 
向右旋转 1 步: [99,-1,-100,3]
向右旋转 2 步: [3,99,-1,-100]

说明:
尽可能想出更多的解决方案，至少有三种不同的方法可以解决这个问题。
要求使用空间复杂度为 O(1) 的 原地 算法。

# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        n = len(nums)
        k = k % n
        def swap(l, r):
            while (l < r):
                nums[l], nums[r] = nums[r], nums[l]
                l = l + 1
                r = r - 1
        swap(0, n - k - 1)
        swap(n - k, n - 1)
        swap(0, n - 1)
```
C++ Code:
```
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        if (k >= nums.size())
            k %= nums.size();
        if (k != 0) {
            reverse1(nums, 0, nums.size() - k - 1);
            reverse1(nums, nums.size() - k, nums.size() - 1);
            reverse1(nums, 0, nums.size() - 1);
        }
    }
    void reverse1(vector<int>& a,int s,int e) {
        while (s < e)
        {
            int temp = a[e];
            a[e] = a[s];
            a[s] = temp;
            e--;
            s++;
        }
    }
};
```

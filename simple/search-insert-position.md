# **题目地址**
https://leetcode-cn.com/problems/search-insert-position/
# **题目描述**
```
给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。
你可以假设数组中无重复元素。

示例 1:
输入: [1,3,5,6], 5
输出: 2

示例 2:
输入: [1,3,5,6], 2
输出: 1

示例 3:
输入: [1,3,5,6], 7
输出: 4

示例 4:
输入: [1,3,5,6], 0
输出: 0
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        if (not nums):
            return 0
        n = len(nums)
        l = 0
        r = n - 1
        res = -1
        while (l <= r):
            mid = (l + r) // 2
            if (nums[mid] == target):
                return mid
            elif (nums[mid] > target):
                r = mid - 1
            else:
                l = mid + 1
        res = l
        return res
```
C++ Code:
```
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int size = nums.size();
        if (size == 0) {
            return 0;
        }
        int left = 0;
        int right = size;
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] < target) {
                left = mid + 1;
            } else if (nums[mid] == target) {
                return mid;
            } else {
                right = mid;
            }
        }
        return left;
    }
};
```

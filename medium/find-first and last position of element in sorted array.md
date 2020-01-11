# **题目地址**
https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/
# **题目描述**
```
给定一个按照升序排列的整数数组 nums，和一个目标值 target。
找出给定目标值在数组中的开始位置和结束位置。
你的算法时间复杂度必须是 O(log n) 级别。
如果数组中不存在目标值，返回 [-1, -1]。

示例 1:
输入: nums = [5,7,7,8,8,10], target = 8
输出: [3,4]

示例 2:
输入: nums = [5,7,7,8,8,10], target = 6
输出: [-1,-1]
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        l, r = 0, len(nums) - 1
        while l < r:
            mid = (l + r) // 2
            if nums[mid] >= target:
                r = mid
            else:
                l = mid + 1
        if not nums or nums[l] != target:
            return [-1,-1]
        a, b = l, len(nums) - 1
        while a < b:
            mid = (a + b + 1) // 2
            if nums[mid] <= target:
                a = mid
            else:
                b = mid - 1
        return [l,a]
```
C++ Code:
```
class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
        if (nums.size() == 0)
            return {-1, -1};
        int begin = 0, end = nums.size() - 1;
        if (nums[begin] > target || nums[end] < target)
            return {-1, -1};
        while (begin <= end) {
            if (nums[begin] == target && nums[end] == target) {
                vector<int> ret = {begin, end};
                return ret;
            }
            int mid = (begin + end) / 2; 
            if (nums[mid] < target)
                begin = mid + 1;
            else if (nums[mid] > target)
                end = mid - 1;
            else {
                begin = mid;
                end = mid;
                while (begin >= 0 && nums[begin] == target) {
                    begin--;
                }
                while (end < nums.size() && nums[end] == target) {
                    end++;
                }
                vector<int> ret = {begin + 1, end - 1};
                return ret;               
            }
            if (nums[begin] > target || nums[end] < target) {
                return {-1, -1};
            }
        }
        return {-1, -1};
    }
};
```

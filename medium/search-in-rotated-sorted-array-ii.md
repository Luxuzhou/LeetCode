# **题目地址**
https://leetcode-cn.com/problems/search-in-rotated-sorted-array-ii/
# **题目描述**
```
假设按照升序排序的数组在预先未知的某个点上进行了旋转。
( 例如，数组 [0,0,1,2,2,5,6] 可能变为 [2,5,6,0,0,1,2] )。
编写一个函数来判断给定的目标值是否存在于数组中。若存在返回 true，否则返回 false。

示例 1:
输入: nums = [2,5,6,0,0,1,2], target = 0
输出: true

示例 2:
输入: nums = [2,5,6,0,0,1,2], target = 3
输出: false

进阶:
这是 搜索旋转排序数组 的延伸题目，本题中的 nums  可能包含重复元素。
这会影响到程序的时间复杂度吗？会有怎样的影响，为什么？
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def search(self, nums: List[int], target: int) -> bool:
        l = 0
        r = len(nums) - 1
        while (l <= r):
            mid = (l + r) // 2
            if (nums[mid] == target):
                return True
            if (nums[mid] == nums[l] == nums[r]):
                l += 1
                r -= 1
            elif (nums[mid] >= nums[l]):
                if (nums[l] <= target < nums[mid]):
                    r = mid - 1
                else:
                    l = mid + 1
            else:
                if(nums[mid] < target <= nums[r]):
                    l = mid + 1
                else:
                    r = mid - 1
        return False
```
C++ Code:
```
class Solution {
public:
    bool search(vector<int>& nums, int target) {
        if (nums.empty()) return false;
        int lo = 0, hi = nums.size() - 1;
        while (lo < hi) {
            int mid = lo + (hi - lo >> 1);
            if (nums[mid] == nums[hi]) --hi; 
            else if (target == nums[mid]
            || (nums[mid] >= nums[lo] && nums[lo] <= target && target < nums[mid])
            || (nums[mid] < nums[lo] && (target < nums[mid] || target >= nums[lo]))) hi = mid;
            else lo = mid + 1;
        }
    return nums[lo] == target;
    }
};
```

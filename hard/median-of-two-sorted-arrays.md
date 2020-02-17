# **题目地址**
https://leetcode-cn.com/problems/median-of-two-sorted-arrays/
# **题目描述**
```
给定两个大小为 m 和 n 的有序数组 nums1 和 nums2。
请你找出这两个有序数组的中位数，并且要求算法的时间复杂度为 O(log(m + n))。
你可以假设 nums1 和 nums2 不会同时为空。

示例 1:
nums1 = [1, 3]
nums2 = [2]
则中位数是 2.0

示例 2:
nums1 = [1, 2]
nums2 = [3, 4]
则中位数是 (2 + 3)/2 = 2.5
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:

        if len(nums1) > len(nums2):
            nums1, nums2 = nums2, nums1
        len1, len2 = len(nums1), len(nums2)
        
        left, right, half_len = 0, len1, (len1 + len2 + 1) // 2
        mid1 = (left + right) // 2
        mid2 = half_len - mid1
        
        while left < right:
            if mid1 < len1 and nums2[mid2-1] > nums1[mid1]:
                left = mid1 + 1
            else:
                right = mid1
            mid1 = (left + right) // 2
            mid2 = half_len - mid1
        
        if mid1 == 0: 
            max_of_left = nums2[mid2-1]
        elif mid2 == 0: 
            max_of_left = nums1[mid1-1]
        else: 
            max_of_left = max(nums1[mid1-1], nums2[mid2-1])

        if (len1 + len2) % 2 == 1:
            return max_of_left

        if mid1 == len1: 
            min_of_right = nums2[mid2]
        elif mid2 == len2: 
            min_of_right = nums1[mid1]
        else: 
            min_of_right = min(nums1[mid1], nums2[mid2])

        return (max_of_left + min_of_right) / 2
```
C++ Code:
```
class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        int n = nums1.size();
        int m = nums2.size();

        if (n > m) {
			return findMedianSortedArrays(nums2, nums1);
				}

        int LMax1, LMax2, RMin1, RMin2, c1, c2, lo = 0, hi = 2 * n;
        while (lo <= hi) {
            c1 = (lo + hi) / 2;  //c1是二分的结果
            c2 = m + n - c1;

            LMax1 = (c1 == 0) ? INT_MIN : nums1[(c1 - 1) / 2];
            RMin1 = (c1 == 2 * n) ? INT_MAX : nums1[c1 / 2];
            LMax2 = (c2 == 0) ? INT_MIN : nums2[(c2 - 1) / 2];
            RMin2 = (c2 == 2 * m) ? INT_MAX : nums2[c2 / 2];

            if (LMax1 > RMin2)
                hi = c1 - 1;
            else if (LMax2 > RMin1)
                lo = c1 + 1;
            else
                break;
        }
        return (max(LMax1, LMax2) + min(RMin1, RMin2)) / 2.0;
    }
};
```

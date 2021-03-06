# **题目地址**
https://leetcode-cn.com/problems/merge-sorted-array/
# **题目描述**
```
给定两个有序整数数组 nums1 和 nums2，将 nums2 合并到 nums1 中，使得 num1 成为一个有序数组。

说明:
初始化 nums1 和 nums2 的元素数量分别为 m 和 n。
你可以假设 nums1 有足够的空间（空间大小大于或等于 m + n）来保存 nums2 中的元素。

示例:
输入:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3
输出: [1,2,2,3,5,6]
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        p1 = m - 1
        p2 = n - 1

        while p1 >= 0 and p2 >= 0:
            if nums1[p1] > nums2[p2]:
                nums1[p1 + p2 + 1] = nums1[p1]
                p1 -= 1
            else:
                nums1[p1 + p2 + 1] = nums2[p2]
                p2 -= 1 
        if p2 > 0:
            nums1[: p1 + p2 + 2] = nums2[:p2+1]
        if p2 == 0:
            nums1[0] = nums2[p2]
```
C++ Code:
```
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        for (int i = m - 1, j = n - 1, k = m + n - 1; k >= 0; --k) {
            if (j < 0 || i >= 0 && nums1[i] > nums2[j])
                nums1[k] = nums1[i--];
            else
                nums1[k] = nums2[j--];
        }
    }
};
```

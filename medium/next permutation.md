# **题目地址**
https://leetcode-cn.com/problems/next-permutation/
# **题目描述**
```
实现获取下一个排列的函数，算法需要将给定数字序列重新排列成字典序中下一个更大的排列。
如果不存在下一个更大的排列，则将数字重新排列成最小的排列（即升序排列）。
必须原地修改，只允许使用额外常数空间。

以下是一些例子，输入位于左侧列，其相应输出位于右侧列。
1,2,3 → 1,3,2
3,2,1 → 1,2,3
1,1,5 → 1,5,1
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def nextPermutation(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        def reverse(nums,i,j):
            while(i < j):
                nums[i], nums[j] = nums[j], nums[i]
                i = i + 1
                j = j - 1
            return nums
        n = len(nums)
        index1 = -1
        for i in range(n-2, -1, -1):
            if (nums[i] < nums[i + 1]):
                index1 = i
                break
        if (index1 == -1):
            nums = reverse(nums, 0, n-1)
            return
        index2 = -1
        for j in range(n-1, -1, -1):
            if (nums[j] > nums[index1]):
                index2 = j
                break
        nums[index1], nums[index2] = nums[index2], nums[index1]
        nums=reverse(nums, index1 + 1, n - 1)
```
C++ Code:
```
class Solution {
public:
void nextPermutation(vector<int>& nums) {
    int flag = 0;
    int i = nums.size() - 1;
    for (; i > 0; i--) {
        if(nums[i - 1] < nums[i]) {
            flag = i - 1;
            break;
        }
    }
    if (i == 0)
        sort(nums.begin(), nums.end());
    else {
        sort(nums.begin() + i,nums.end());
        int j = i;
        for(; j < nums.size(); j++)
            if(nums[j] > nums[flag]) break;
        int t = nums[flag];
        nums[flag] = nums[j];
        nums[j] = t;
    }
}
```

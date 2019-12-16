# **题目地址**
https://leetcode-cn.com/problems/3sum-closest/
# **题目描述**
```
给定一个包括 n 个整数的数组 nums 和 一个目标值 target。
找出 nums 中的三个整数，使得它们的和与 target 最接近。
返回这三个数的和。假定每组输入只存在唯一答案。

例如，给定数组 nums = [-1，2，1，-4], 和 target = 1.

与 target 最接近的三个数的和为 2. (-1 + 2 + 1 = 2).
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        n = len(nums)
        if (not nums or n < 3):
            return None
        nums.sort()
        res = float("inf")
        for i in range(n):
            if (i > 0 and nums[i] == nums[i-1]):
                continue
            L = i + 1
            R = n - 1
            while (L < R):
                cur_sum = nums[i] + nums[L] + nums[R]
                if (cur_sum == target):
                    return target
                if (abs(cur_sum - target) < abs(res - target)):
                    res = cur_sum
                if (cur_sum - target < 0):
                    L += 1
                else:
                    R -= 1
        return res
```
C++ Code:
```
class Solution {
public:   
    int threeSumClosest(vector<int>& nums, int target) {
        sort(nums.begin(), nums.end());
        int closestSumValue = nums[0]+ nums[1]+ nums[2];
        int digit1_index, digit2_index, digit3_index;
        int max_digit1_index = nums.size() - 2;
        for (int i = 0; i < max_digit1_index; i++){
            digit1_index = i;
            digit2_index = i + 1;
            digit3_index = nums.size() - 1;
            int tmp_sum = nums[digit1_index] + nums[digit2_index] + nums[digit3_index];
            while (digit2_index < digit3_index){
                if (abs(tmp_sum - target) < abs(closestSumValue - target))
                    closestSumValue = tmp_sum;
                int difference = target - tmp_sum;
                if (difference == 0){
                    return target;
                }
                if (difference > 0){
                    digit2_index++;
                }
                else {
                digit3_index--;
                }
                tmp_sum = nums[digit1_index] + nums[digit2_index] + nums[digit3_index];
            }
        }
        return closestSumValue;
    }
};
```

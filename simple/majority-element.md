# **题目地址**
https://leetcode-cn.com/problems/majority-element/
# **题目描述**
```
给定一个大小为 n 的数组，找到其中的多数元素。多数元素是指在数组中出现次数大于 ⌊ n/2 ⌋ 的元素。
你可以假设数组是非空的，并且给定的数组总是存在多数元素。

示例 1:
输入: [3,2,3]
输出: 3

示例 2:
输入: [2,2,1,1,1,2,2]
输出: 2
```
# **思路解析**
# **代码实现**
Python3 Code:
```
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        count = 1
        target = nums[0]
        n = len(nums)
        for i in range(1, n):
            if nums[i] == target:
                count += 1
            else:
                if count >= 1:
                    count -= 1
                else:
                    target = nums[i]            
        return target
```
C++ Code:
```
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int target = nums[0];
        int count = 1;
        for (int i = 1; i < nums.size(); i++)
            if (nums[i] != target) {  
                count--;
                if (count == 0) {
                    target = nums[i];
                    count = 1;
                }
            }else count++;
      return target;
    }
};
```
